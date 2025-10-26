# Octavier
import java.util.InputMismatchException;
import java.util.Scanner;
public class Octavier {

// The entire application is contained within this main class
      // ====== COLOR CONSTANTS (Must be static members of the class) ======
      // ANSI escape codes for coloring the console output.
      public static final String Reset = "\033[0m";
      public static final String Purple = "\033[35m";
      public static final String Cyan = "\033[36m";
      public static final String Pink = "\033[95m";
      public static final String Yellow = "\033[33m";
      public static final String White = "\033[37m";
      public static final String Green = "\033[32m";
      public static final String Red = "\033[31m";

      // Static Scanner for reading user input throughout the application.
      private static final Scanner sc = new Scanner(System.in);
      
      // Global flag to control program termination.
      private static boolean exit = false;

      public static void main(String[] args) throws InterruptedException {
          bigWelcomeLogo();
          loadingLogo();
          // Start the main loop. The application will loop until 'exit' is true.
          while (!exit) {
              startScreen();
          }
      }
      
      // ====== CLEAR SCREEN ======
      private static void clearScreen() {
          // ANSI code to clear the screen and move the cursor to the home position.
          System.out.print("\033[H\033[2J");
          System.out.flush();
      }

      
      // ====== BIG WELCOME LOGO ======
      private static void bigWelcomeLogo() throws InterruptedException {
          clearScreen();
          
          System.out.println(Pink);
          System.out.println("     ╔════════════════════════════════════════════════════════════════╗");
          System.out.println("     ║                   😍 W E L C O M E 😍                                     ║");
          System.out.println("     ╚════════════════════════════════════════════════════════════════╝");
          Thread.sleep(600);
          System.out.println(Purple); 
          System.out.println("    ██╗░░░░░░░██╗███████╗██╗░░░░░░█████╗░░█████╗░███╗░░░███╗███████╗ ");
          System.out.println("    ██║░░██╗░░██║██╔════╝██║░░░░░██╔══██╗██╔══██╗████╗░████║██╔════╝ ");
          System.out.println("    ╚██╗████╗██╔╝█████╗░░██║░░░░░██║░░╚═╝██║░░██║██╔████╔██║█████╗░░ ");
          System.out.println("    ░████╔═████║░██╔══╝░░██║░░░░░██║░░██╗██║░░██║██║╚██╔╝██║██╔══╝░░ ");
          System.out.println("    ░╚██╔╝░╚██╔╝░███████╗███████╗╚█████╔╝╚█████╔╝██║░╚═╝░██║███████╗ ");
          System.out.println("    ░░╚═╝░░░╚═╝░░╚══════╝╚══════╝░╚════╝░░╚════╝░╚═╝░░░░░╚═╝╚══════╝ ");
          System.out.println(Reset);
          Thread.sleep(1500);
      }

      // ====== ANIMATED LOADING LOGO ======
      private static void loadingLogo() throws InterruptedException {
          clearScreen();
          String[] loadingFrames = {
              
              "[████▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒10%]10%", 
              "[██████████▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒30%]30%",   // Adjusted frames for smooth transition
              "[████████████████▒▒▒▒▒▒▒▒▒▒50%]50%", 
              "[████████████████████████▒▒80%]80%", 
              "[██████████████████████████100%]100%",  // Fixed typo in 100% frame
              
          };
          
          System.out.println(Cyan + "\n\n Loading, please wait! \n\n" + Reset);
          for (String frame : loadingFrames) {
              System.out.print("\r" + Pink + "   " + frame + Reset);
              Thread.sleep(200);
          }
          System.out.println("\n\n" + Green + "✨ All systems ready! ✨" + Reset);
          Thread.sleep(1000);
      }
      
      // ====== MAIN MENU ======
      // **Fix**: Corrected typo from EnterruptedExcemption to InterruptedException.
      private static void startScreen() throws InterruptedException { 
          
          clearScreen();
          System.out.println(Pink);
          System.out.println("    ╔═══════════════════════════════════════════════╗ ");
          System.out.println("    ║             ✨ M A I N  M E N U ✨                    ║ ");
          System.out.println("    ╠═══════════════════════════════════════════════╣ ");
          System.out.println("    ║                                                       ║ ");
          System.out.println("    ║              [1] 🤡 Start                             ║ ");
          System.out.println("    ║              [2] 🤫 About Us                          ║ ");
          System.out.println("    ║              [3] 😷 Exit                              ║ ");
          System.out.println("    ║                                                       ║ ");
          System.out.println("    ╚═══════════════════════════════════════════════╝ " + Reset);
      
          // Main menu selection loop
          while (!exit) {
              System.out.print("\n" + Pink + "♡ Choose an option: " + Reset);
              try {
                  int option = sc.nextInt();
                  sc.nextLine(); // Consume newline character
                  switch (option) {
                      case 1 -> start();
                      case 2 -> aboutUs();
                      case 3 -> exitProgram();
                      default -> invalidOption();
                  }
                  // If exit is true, break out of the main loop.
                  if (exit) break; 
              } catch (InputMismatchException e) {
                  sc.nextLine(); // Clear the invalid input
                  invalidOption();
              }
          }
      
      }

      // ====== INVALID OPTION ======
      private static void invalidOption() throws InterruptedException {
          clearScreen();
          System.out.println(Red + "⚠️ Oops! That’s not a valid option. Please try again!" + Reset);
          Thread.sleep(1500); // Increased pause for better visibility
          // NOTE: We don't call startScreen() here. We let the calling loop re-display the menu.
      }

      // ====== START OPTION / SUB-MENU ======
      private static void start() throws InterruptedException {
          boolean backToMain = false;
          while (!backToMain) {
              clearScreen();
              System.out.println(Cyan);
              System.out.println("   ╔═══════════════════════════════════════════════════╗");
              System.out.println("   ║         🥳 Welcome to the Start Menu! 🥳                   ║");
              System.out.println("   ╠═══════════════════════════════════════════════════╣");
              System.out.println("   ║                                                            ║");
              System.out.println("   ║              [1] 🧪 Calculator                             ║");
              System.out.println("   ║              [2] 📏 Area & Circumference                   ║");
              System.out.println("   ║              [3] 🔄 Unit Converter                         ║");
              System.out.println("   ║              [4] ⏪ Back to Main Menu                      ║");
              System.out.println("   ║                                                            ║");
              System.out.println("   ╚═══════════════════════════════════════════════════╝" + Reset);
          
              System.out.print("\n" + Pink + "♡ Choose an option: " + Reset);
              try {
                  int option = sc.nextInt();
                  sc.nextLine(); 
                  switch (option) {
                      case 1 -> calcu();
                      case 2 -> areacircum();
                      case 3 -> unitconvert();
                      case 4 -> backToMain = true;
                      default -> invalidOption();
                  }
              } catch (InputMismatchException e) {
                  sc.nextLine();
                  invalidOption();
              }
          }
      }
      
      // ====== CALCULATOR FEATURE (Calcu) ======
      private static void calcu() throws InterruptedException {
          boolean inCalculator = true;
          while(inCalculator) {
              clearScreen();
              System.out.println(Purple + "\n-- 🧪 Simple Calculator --" + Reset);
              try {
                  System.out.print("Enter first number: ");
                  double a = Double.parseDouble(sc.nextLine());

                  System.out.print("Enter operator (+, -, *, /): ");
                  String opStr = sc.nextLine();
                  if (opStr.isEmpty()) { 
                       System.out.println(Red + "Error: Operator cannot be empty." + Reset);
                       Thread.sleep(1500);
                       continue;
                  }
                  char op = opStr.charAt(0);

                  System.out.print("Enter second number: ");
                  double b = Double.parseDouble(sc.nextLine());

                  double result;

                  switch (op) {
                      case '+':
                          result = a + b;
                          break;
                      case '-':
                          result = a - b;
                          break;
                      case '*':
                          result = a * b;
                          break;
                      case '/':
                          if (b == 0) {
                              System.out.println(Red + "Error: Division by zero is not allowed." + Reset);
                              Thread.sleep(2000);
                              continue;
                          }
                          result = a / b;
                          break;
                      default:
                          System.out.println(Red + "Error: Invalid operator." + Reset);
                          Thread.sleep(2000);
                          continue;
                  }

                  System.out.println(Green + "Answer: " + result + Reset);
              } catch (NumberFormatException e) {
                  System.out.println(Red + "Error: Invalid number input. Please enter valid numbers." + Reset);
              }
              
              System.out.print(Yellow + "\nPress [R] to calculate again, or [B] to go back: " + Reset);
              String choice = sc.nextLine().trim().toLowerCase();
              if (choice.equals("b")) {
                  inCalculator = false;
              }
          }
      }

      // ====== AREA & CIRCUMFERENCE FEATURE (areacircum) ======
      private static void areacircum() throws InterruptedException {
          boolean inAreaCircum = true;
          while(inAreaCircum) {
              clearScreen();
              System.out.println(Purple + "\n-- 📏 Circle Area & Circumference --" + Reset);
              try {
                  System.out.print("Enter the radius of the circle: ");
                  double radius = Double.parseDouble(sc.nextLine());

                  if (radius < 0) {
                      System.out.println(Red + "Error: Radius cannot be negative." + Reset);
                      Thread.sleep(1500);
                      continue;
                  }

                  double area = Math.PI * radius * radius;
                  double circumference = 2 * Math.PI * radius;

                  System.out.println(Green + "\nResults (for radius " + radius + "):" + Reset);
                  System.out.printf(Cyan + "  - Area: %.2f%n" + Reset, area);
                  System.out.printf(Cyan + "  - Circumference: %.2f%n" + Reset, circumference);

              } catch (NumberFormatException e) {
                  System.out.println(Red + "Error: Invalid input. Please enter a valid number for the radius." + Reset);
              }
              
              System.out.print(Yellow + "\nPress [R] to calculate again, or [B] to go back: " + Reset);
              String choice = sc.nextLine().trim().toLowerCase();
              if (choice.equals("b")) {
                  inAreaCircum = false;
              }
          }
      }

      // ====== UNIT CONVERTER FEATURE (unitconvert) ======
      private static void unitconvert() throws InterruptedException {
          boolean inConverter = true;
          while(inConverter) {
              clearScreen();
              System.out.println(Purple + "\n-- 🔄 Unit Converter (Celsius to Fahrenheit) --" + Reset);
              try {
                  System.out.print("Enter temperature in Celsius (C): ");
                  double celsius = Double.parseDouble(sc.nextLine());

                  // Formula: (C * 9/5) + 32
                  double fahrenheit = (celsius * 9/5) + 32;

                  System.out.println(Green + "\nConversion Result:" + Reset);
                  System.out.printf(Cyan + "%.2f C is equal to %.2f F%n" + Reset, celsius, fahrenheit);

              } catch (NumberFormatException e) {
                  System.out.println(Red + "Error: Invalid input. Please enter a valid number for Celsius." + Reset);
              }
              
              System.out.print(Yellow + "\nPress [R] to convert again, or [B] to go back: " + Reset);
              String choice = sc.nextLine().trim().toLowerCase();
              if (choice.equals("b")) {
                  inConverter = false;
              }
          }
      }

      // ====== ABOUT US ======
      private static void aboutUs() throws InterruptedException {
          clearScreen();
          System.out.println(Purple);
          System.out.println("  ╔═══════════════════════════════════╗");
          System.out.println("  ║           ❗ABOUT US❗                  ║");
          System.out.println("  ╚═══════════════════════════════════╝" + Reset);
          // **Fix**: Correctly printed the color constants instead of string literals.
          System.out.println(Cyan);
          System.out.println("Created by: Octavier");
          System.out.println("Version: 3.0 No Sleep");
          System.out.println("Language: Javalog");
          System.out.println("Goal: To finish my Project");
          System.out.println(Reset);
          Thread.sleep(2500);
          System.out.print("\nPress Enter to return...");
          sc.nextLine(); // Wait for user to press enter
          // The calling loop in startScreen() will handle re-displaying the menu.
      }
      
      // ====== BIG THANK YOU LOGO ======
      private static void bigThankYou() throws InterruptedException {
        clearScreen();
          System.out.println(Pink);
          System.out.println(" ╔════════════════════════════════════════════════════════════╗");
          System.out.println(" ║                     🤩 T H A N K  Y O U 🤩                            ║");
          System.out.println(" ╚════════════════════════════════════════════════════════════╝");
          System.out.println(Cyan);
          System.out.println(" ████████╗██╗░░██╗░█████╗░███╗░░██╗██╗░░██╗  ██╗░░░██╗░█████╗░██╗░░░██╗ ");
          System.out.println(" ╚══██╔══╝██║░░██║██╔══██╗████╗░██║██║░██╔╝  ╚██╗░██╔╝██╔══██╗██║░░░██║ ");
          System.out.println(" ░░░██║░░░███████║███████║██╔██╗██║█████═╝░  ░╚████╔╝░██║░░██║██║░░░██║ ");
          System.out.println(" ░░░██║░░░██╔══██║██╔══██║██║╚████║██╔═██╗░  ░░╚██╔╝░░██║░░██║██║░░░██║ ");
          System.out.println(" ░░░██║░░░██║░░██║██║░░██║██║░╚███║██║░╚██╗  ░░░██║░░░╚█████╔╝╚██████╔╝ ");
          System.out.println(" ░░░╚═╝░░░╚═╝░░╚═╝╚═╝░░╚═╝╚═╝░░╚══╝╚═╝░░╚═╝  ░░░╚═╝░░░░╚════╝░░╚═════╝░ ");        
          System.out.println(Reset);          
          Thread.sleep(1500);
          System.out.println(Yellow + "✨ Thank you for using this adorable program! ✨");
          System.out.println("Stay happy, keep coding, and always shine bright 🌟" + Reset);
          Thread.sleep(2000);
          
      }
          
      // ====== EXIT OPTION ======
      private static void exitProgram() throws InterruptedException {
         
        bigThankYou();
          System.out.print(Pink + "\nExiting program");
          for (int i = 0; i < 5; i++) {
              System.out.print(" 💫");
              Thread.sleep(400);
          }
          System.out.println("\n" + Reset);
          exit = true; // Set global flag to true to break the main loop
      }
}
