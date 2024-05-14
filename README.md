struct Point }
public int x { get; set; }
    public int y { get; set; }
    public char ch { get; set; }

    public static implicit operator Point((int, int, char) value) => 
        new Point {x = value.Item1, y = value.Item2, ch = value.Item3};

    public void Draw(){
        DrawPoint(ch);
    }
    public void Clear(){
        DrawPoint(' ');
    }
    private void DrawPoint(char _ch){
        Console.SetCursorPosition(x, y);
        Console.Write(_ch);
    }
}

private void DrawHorizontal
    for(int i=0,i<x,i++){
        Point p=(i,y,ch);
p.Draw();
Wall.add();
    }
}
/// we create a horizontal wall, then using the for loop we create walls from all sides, also when eating food we get one point
Class Walls{
    private char ch; 
    private List<Point> wall=new List<Point>();

    public walls(int x,int y,char ch){
        this.ch=ch;

    
    public Walls(int x, int y, char ch){
        this.ch = ch;
        DrawHorizontal(x, 0);
        DrawHorizontal(x, y);
        DrawVertical(0, y);
        DrawVertical(x, y);
    }
/// we make coordinates along the vertical line and along the horizontal line
    }
    private void DrawVertical(int x, int y) {
        for (int i = 0; i < y; i++) {
            Point p = (x, i, ch);
            p.Draw();
            wall.Add(p);
        }
    }}
}
class FoodFactory
{
    int x;
    int y;
    char ch;
    public Point food { get; private set; }

    Random random = new Random();

    public FoodFactory(int x, int y, char ch)
    {
        this.x = x;
        this.y = y;
        this.ch = ch;
    }

    public void CreateFood()
    {
        food = (random.Next(2, x - 2), random.Next(2, y - 2), ch);
        food.Draw();
    }
}
/// we declare the Food Factory class and we create food for the snake, so that food appears at any moment
class Game
    static FoodFactory foodFactory;

    static void Main(){
        foodFactory = new FoodFactory(x, y, '@');
        foodFactory.CreateFood();
        enum Direction{
            LEFT,
            RIGHT,
            UP,
            DOWN
        }
        class Snake{
            private List<Point> snake;
            private Direction direction;
            private int step = 1;
            private Point tail;
            private Point head;
            bool rotate = true;
            public Snake(int x, int y, int length){
                direction = Direction.RIGHT;
                snake = new List<Point>();
                for (int i = x - length; i < x; i++)        {
                    Point p = (i, y, '*');
                    snake.Add(p);
                    p.Draw();
                }
            }
        ///Methods of movement and rotation depending on the direction of movement of the snake.
            public Point GetHead() => snake.Last();
            public void Move(){
                head = GetNextPoint();
                snake.Add(head);
                tail = snake.First();
                snake.Remove(tail);
                tail.Clear();
                head.Draw();
                rotate = true;
            }
            public Point GetNextPoint() {
                Point p = GetHead();
                switch (direction) {
                    case Direction.LEFT:
                        p.x -= step;
                        break;
                    case Direction.RIGHT:
                        p.x += step;
                        break;
                    case Direction.UP:
                        p.y -= step;
                        break;
                    case Direction.DOWN:
                        p.y += step;
                        break;
                }
            return p;
            }
            public void Rotation(ConsoleKey key) {
                if (rotate) {
                    switch (direction) {
                        case Direction.LEFT:
                        case Direction.RIGHT:
                            if (key == ConsoleKey.DownArrow)
                                direction = Direction.DOWN;
                            else if (key == ConsoleKey.UpArrow)
                                direction = Direction.UP;
                            break;
                        case Direction.UP:
                        case Direction.DOWN:
                            if (key == ConsoleKey.LeftArrow)
                                direction = Direction.LEFT;
                            else if (key == ConsoleKey.RightArrow)
                                direction = Direction.RIGHT;
                            break;
                    }
                    rotate = false;
                }
            }
        }/
// /class Snake
        class Game{
            static Snake snake;
            static void Main(){
                snake = new Snake(x / 2, y / 2, 3);
                class Game {
                    static void Main () {
                        while (true) {
                            if (Console.KeyAvailable) {
                                ConsoleKeyInfo key = Console.ReadKey ();
                                snake.Rotatiс(key.Key);
                            }
              /// after declaring classSnake, after that we will use the while loop, if our value is correct, then we get the key

                using System.Threading;
                class Game {
                    static Timer time;
                    static void Main () {
                        time = new Timer (Loop, null, 0, 200);
                ...
                struct Point {
                    public static bool operator == (Point a, Point b) => 
                        (a.x == b.x && a.y == b.y) ? true : false;
                    public static bool operator != (Point a, Point b) => 
                        (a.x != b.x || a.y != b.y) ? true : false;
                ...

                class Walls {
                    public bool IsHit (Point p) {
                        foreach (var w in wall) {
                            if (p == w) {
                                return true;
                            }
                        }
                        return false;
                    }
                 
                        }
                        declaring the walls class, after that we use the for loop by setting the necessary variables to us, as a result we get the value false
                        class Snake {
                            public bool IsHit (Point p) {
                                for (int i = snake.Count - 2; i > 0; i--) {
                                    if (snake[i] == p) {
                                        return true;
                                    }
                                }
                                return false;
                            }
                         /// we declare the snake class, after that we use the for loop by setting variables, as a result we get the value false
                            class Snake {
                                static void Loop (object obj) {
                                    if (walls.IsHit (snake.GetHead ()) || snake.IsHit (snake.GetHead ())) {
                                        time.Change (0, Timeout.Infinite);
                                    } else if (snake.Eat (foodFactory.food)) {
                                        foodFactory.CreateFood ();
                                    } else {
                                        snake.Move ();
                                    }
                                }
                                declare the snake class after that we use the if operator, then we give a set of functions for the snake so that its head can move in all directions
