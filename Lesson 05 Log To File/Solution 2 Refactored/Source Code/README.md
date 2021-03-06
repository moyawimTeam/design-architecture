<img style="float: right;" src="../../../Images/aublogosmall.png"> 

**CMPS 253 Software Engineering - Spring 2019-2020 \
Mahmoud Bdeir \
American University of Beirut**

## Lesson 5.3: Refactoring
<a href="./"><img src='../../../Images/code.png'> Source Code</a>

![problem icon](../../../Images/refactoring.png 'Refactoring') 
### Code Refactoring 
Notice there are chances for improving the names (classes, methods, and namespaces) to be more uniform:

- `Logger.dll` is no longer an appropriate name for the library that logs to console, rename it to `ConsoleLogger.dll`

- `Logger` is no longer an appropriate name for the class that logs to console, rename it to `ConsoleLogger`

- Finally, there is no need to use a different name for each logging method (`Log`, `LogToFile`) now that each method is defined in a class of its own, simply use `Log`

```C#
using System.Threading;

namespace Lesson5.Solution2Refactored
{
	class Program
	{
		static void Main(string[] args)
		{
			ConsoleLogger.Log("Program Started");
			FileLogger.Log(".\\log.txt","Program Started");
			
			Thread.Sleep(3000); //Simulating work by having the program sleep for 3 seconds
			
			ConsoleLogger.Log("Program Ended");
			FileLogger.Log(".\\log.txt", "Program Ended");
		}
	}
}
```

```C#
using System;

namespace Lesson5.Solution2Refactored
{
    public static class ConsoleLogger
    {
        public static void Log(string msg)
        {
            Console.WriteLine($"{DateTime.Now} {msg}");
        }
    }
}
```

```C#
using System;
using System.IO;

namespace Lesson5.Solution2Refactored
{
    public static class FileLogger
    {
        public static void Log(string fileName, string msg)
        {
            File.AppendAllText(fileName, $"{DateTime.Now} {msg}\n");
        }
    }
}
```
###### Class Diagram
![Lesson 5 Solution 1 Class Diagram](../images/Class-Diagram.png)
###### Deployment Diagram
![Lesson 6 Solution 1 Deployment Diagram](../images/Deployment-Diagram.png)

<table style='width=100%;'>
<tr>
<td><a href="../../Solution%202%20FileLogger%20Library/Source%20Code"><img src='../../../Images/leftarrow.png'> Back</a></td>
<td width="100%"></td>
<td><a href="../../../Lesson 06 Multiple Output Log/Solution 0 Log Method/Source Code"><img src='../../../Images/rightarrow.png'> Next</a></td>
</tr>
</table>
