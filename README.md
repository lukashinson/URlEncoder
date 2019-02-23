using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace URLEncoder
{
    class Program
    {
        //Lukas Hinson Module 5 URLEncoder
        static bool flag = false;
        public static string[] controls = { "?", "/", "@", "&", ";", ":", "$", "+", "=" };
        static void Main(string[] args)
        {
            do
            {
                try
                {
                   
                    Console.WriteLine("What is the Project Name?");
                    string projectName = GetUserInput();
                    Console.WriteLine("What is the Activity Name?");
                    string activityName = GetUserInput();
                    Console.WriteLine("Here is your URL:");
                    Console.WriteLine("https://companyserver.com/content/" + projectName + "/files/" + activityName + "/" + activityName + "Report.pdf");
                }
                catch
                {
                    Console.WriteLine("Please enter valid details.");
                }
                Console.WriteLine("\n");
                Console.WriteLine("Would you like to create another URL?");
                Console.WriteLine("Y/N");
                char response = Convert.ToChar(Console.ReadLine());
                if (response == 'y')
                {
                    flag = true;
                }
                if (response == 'n')
                {
                    flag = false;
                }
            } while (flag == true);
        }
        static string GetUserInput()
        {
            string input = "";
            do
            {
                input = Console.ReadLine();
                if (IsValid(input)) return input;
                Console.Write("This input doesn't work.");
            } while (true);
        }
        static bool IsValid(string input)
        {
            foreach (char character in input.ToCharArray())
            {
                if (input.ToLower().Contains("?"))
                {
                    Console.WriteLine("Invalid input.");
                    return false;
                }
                if (input.ToLower().Contains("/"))
                {
                    Console.WriteLine("Invalid input.");
                    return false;
                }
                if (input.ToLower().Contains("$"))
                {
                    Console.WriteLine("Invalid input.");
                    return false;
                }
                if (input.ToLower().Contains("="))
                {
                    Console.WriteLine("Invalid input.");
                    return false;
                }
                if (input.ToLower().Contains("+"))
                {
                    Console.WriteLine("Invalid input.");
                    return false;
                }
                if (input.ToLower().Contains("&"))
                {
                    Console.WriteLine("Invalid input.");
                    return false;
                }
                if (input.ToLower().Contains("@"))
                {
                    Console.WriteLine("Invalid input.");
                    return false;
                }
                if (input.ToLower().Contains(":"))
                {
                    Console.WriteLine("Invalid input.");
                    return false;
                }
                if (input.ToLower().Contains(";"))
                {
                    Console.WriteLine("Invalid input.");
                    return false;
                }
                if (character == 0x1F)
                {
                    Console.WriteLine("Hexadecimals are invalid.");
                    return false;
                }
                else
                {
                    Console.WriteLine("Input given valid.");
                    return true;
                }
            }
            return true;
        }

      

            }
        }
  
