---
title: 'Postupy: Čtení textového souboru po řádcích (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: 6ba479e341b71bebe60d9744f239b752d3d81167
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43738765"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-visual-c"></a><span data-ttu-id="71bc3-102">Postupy: Čtení textového souboru po řádcích (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="71bc3-102">How to: Read a Text File One Line at a Time (Visual C#)</span></span>
<span data-ttu-id="71bc3-103">Tento příklad přečte obsah textového souboru, jednořádkový najednou, do řetězce pomocí `ReadLine` metodu `StreamReader` třídy.</span><span class="sxs-lookup"><span data-stu-id="71bc3-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="71bc3-104">Každý řádek textu je uložen do řetězce `line` a zobrazí na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="71bc3-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71bc3-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="71bc3-105">Example</span></span>  
  
```csharp
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =   
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine(line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="71bc3-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="71bc3-106">Compiling the Code</span></span>  
 <span data-ttu-id="71bc3-107">Zkopírujte kód a vložte ho do `Main` metoda konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="71bc3-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="71bc3-108">Nahraďte `"c:\test.txt"` pomocí skutečného názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="71bc3-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="71bc3-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="71bc3-109">Robust Programming</span></span>  
 <span data-ttu-id="71bc3-110">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="71bc3-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="71bc3-111">Soubor neexistuje.</span><span class="sxs-lookup"><span data-stu-id="71bc3-111">The file may not exist.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="71bc3-112">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="71bc3-112">.NET Framework Security</span></span>  
 <span data-ttu-id="71bc3-113">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="71bc3-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="71bc3-114">Například soubor `myFile.cs` nemusí být zdrojový soubor jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="71bc3-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71bc3-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="71bc3-115">See Also</span></span>

- <xref:System.IO?displayProperty=nameWithType>  
- [<span data-ttu-id="71bc3-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="71bc3-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="71bc3-117">Systém souborů a registr (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="71bc3-117">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
