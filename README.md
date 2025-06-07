Program Description
This C# console application is a simple maze game where the player navigates through a maze to reach the goal.

How it works:
  The maze is represented by a 2D character array, where:
  '|' and '-' are walls that the player cannot pass through.
  ' ' (space) is an open path the player can move on.
  '*' marks the goal location.
  The player is represented by the @ symbol and starts at the top-left of the maze.
  The maze is drawn in the console window on each turn.
  The player uses the W (up), A (left), S (down), and D (right) keys to move.
  The game prevents moving through walls.
  When the player reaches the goal (*), a "You Win! 🎉" message is displayed and the game ends.
Features:
  Uses Console.SetCursorPosition to update the player's position smoothly.
  Updates the display in real time after each move.
  Provides a simple and engaging way to learn about arrays, loops, and console input/output in C#.


here is the code:
            
            using System;
            using System.Text;
            
            namespace LearnCS
            {
                internal class Program
                {
                    static void Main(string[] args)
                    {
                        // Set console to output UTF-8 characters and hide the cursor for better visualization
                        Console.OutputEncoding = Encoding.UTF8;
                        Console.CursorVisible = false;
            
                        // Define the map layout using a 2D character array, where:
                        // '|' and '-' are walls, ' ' is empty space, '*' is the goal
                        char[,] map =
                        {
                            { '|','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','|' },
                            { '|',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','|' },
                            { '|',' ','|','-','-','-','-','-','-','-','|','-','-','-','-','-','-','-','-','|','-','-','-',' ','-','|' },
                            { '|',' ','|',' ',' ',' ',' ',' ',' ','|',' ',' ',' ',' ',' ',' ',' ',' ',' ','|',' ',' ',' ',' ','|','|' },
                            { '|',' ','|',' ','|','-','-','-',' ','|',' ','|','-','-','-','-','-','|',' ','|',' ','|','-','-','|','|' },
                            { '|',' ','|',' ','|',' ',' ','|',' ','|',' ','|',' ',' ',' ',' ',' ','|',' ','|',' ','|',' ',' ',' ','|' },
                            { '|',' ','|',' ','|',' ','|','|',' ','|',' ','|',' ','|','-','-','-','|',' ','|',' ','|','-','-','-','|' },
                            { '|',' ','|',' ','|',' ','|',' ',' ','|',' ','|',' ','|',' ',' ',' ',' ',' ','|',' ',' ',' ',' ',' ','|' },
                            { '|',' ','|',' ','|',' ','|',' ','|','|',' ','|',' ','|',' ','|','-','-','-','|','-','-','-','-',' ','|' },
                            { '|',' ','|',' ','|',' ','|',' ','|',' ',' ','|',' ','|',' ','|',' ',' ',' ',' ',' ',' ',' ','|',' ','|' },
                            { '|',' ','|',' ','|',' ','|',' ','|',' ','|','|',' ','|',' ','|',' ','|','-','-','-','-',' ','|',' ','|' },
                            { '|',' ','|',' ',' ',' ',' ',' ','|',' ','|',' ',' ','|',' ',' ',' ','|',' ',' ',' ',' ',' ','|',' ','|' },
                            { '|',' ','|','-','-','-','-','-','|',' ','|',' ','|','|','-','-','-','|',' ','|','-','-','-','|',' ','|' },
                            { '|',' ',' ',' ',' ',' ',' ',' ','|',' ',' ',' ',' ','*',' ',' ',' ','|',' ',' ',' ',' ',' ',' ',' ','|' },
                            { '|',' ','|','-','-','-','-','-','|','-','-','-','|','-','-','-',' ','|',' ','|','-','-','-','|',' ','|' },
                            { '|',' ','|',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','|',' ','|',' ','|',' ',' ',' ','|',' ','|' },
                            { '|',' ','|',' ','|','-','-','-','-','-','-','-','|',' ','|','|','-','|',' ','|',' ','|','-','|',' ','|' },
                            { '|',' ','|',' ','|',' ',' ',' ',' ',' ',' ',' ','|',' ',' ',' ',' ',' ',' ','|',' ','|',' ',' ',' ','|' },
                            { '|',' ','|','-','|',' ','|','-','-','-','|','-','|','-','-','-','-','-','-','|','-','|',' ','|','-','|' },
                            { '|',' ',' ',' ',' ',' ','|',' ',' ',' ','|',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','|' },
                            { '|','-','-','-','-','-','|',' ','|','-','|','-','-','-','-','-','-','|','-','-','-','-','-','-','-','|' },
                            { '|',' ',' ',' ',' ',' ','|',' ','|',' ',' ',' ',' ',' ',' ',' ',' ','|',' ',' ',' ',' ',' ',' ',' ','|' },
                            { '|',' ','|','-','-','-','|',' ','|',' ','|','-','-','-','|','-','-','|',' ','|','-','-','-','-','-','|' },
                            { '|',' ','|',' ',' ',' ',' ',' ',' ',' ','|',' ',' ',' ','|',' ',' ',' ',' ','|',' ',' ',' ',' ',' ','|' },
                            { '|',' ','|',' ','|','-','-','-','-','-','|',' ','|','-','|','-','-','-','|',' ','|','-','-','-',' ','|' },
                            { '|',' ','|',' ','|',' ',' ',' ',' ',' ',' ',' ','|',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','|' },
                            { '|',' ','|',' ','|','-','-','-','-','-','-','-','|','-','-','-','-','-','-','-','-','-','-','-','-','|' },
                            { '|',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','|' },
                            { '|','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','-','|' },
                        };
            
                        // Initialize player position at (1,1)
                        int userX = 1, userY = 1;
            
                        // Main game loop
                        while (true)
                        {
                            // Clear the console screen for each frame
                            Console.Clear();
            
                            // Draw the map by iterating through each row and column
                            for (int i = 0; i < map.GetLength(0); i++)
                            {
                                for (int j = 0; j < map.GetLength(1); j++)
                                {
                                    Console.Write(map[i, j]);
                                }
                                Console.WriteLine();
                            }
            
                            // Draw the player character '@' at the current position
                            Console.SetCursorPosition(userX, userY);
                            Console.Write('@');
            
                            // Wait for the player to press a key (not displayed on screen)
                            ConsoleKeyInfo key = Console.ReadKey(true);
            
                            // Restore the map symbol at the player's old position
                            Console.SetCursorPosition(userX, userY);
                            Console.Write(map[userY, userX]);
            
                            // If the player hasn't reached the goal ('*'), handle movement
                            if (map[userY, userX] != '*')
                            {
                                // Check which key was pressed and move if possible (not into walls '|', '-')
                                switch (key.Key)
                                {
                                    case ConsoleKey.W: // Move up
                                        if (map[userY - 1, userX] != '|' && map[userY - 1, userX] != '-')
                                            userY--;
                                        break;
                                    case ConsoleKey.S: // Move down
                                        if (map[userY + 1, userX] != '|' && map[userY + 1, userX] != '-')
                                            userY++;
                                        break;
                                    case ConsoleKey.A: // Move left
                                        if (map[userY, userX - 1] != '|' && map[userY, userX - 1] != '-')
                                            userX--;
                                        break;
                                    case ConsoleKey.D: // Move right
                                        if (map[userY, userX + 1] != '|' && map[userY, userX + 1] != '-')
                                            userX++;
                                        break;
                                }
                            }
                            // If the player reached the goal ('*'), display win message and exit the loop
                            else
                            {
                                Console.Clear();
                                Console.SetCursorPosition(0, 0);
                                Console.WriteLine("You Win! 🎉"); // Show victory message
                                Console.ReadKey(); // Wait for any key press before exiting
                                break;
                            }
            
                        }
                    }
                }
            }
