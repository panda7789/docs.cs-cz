---
title: Jak číst textový soubor po jednom řádku v průběhu času – Průvodce programováním v C#
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: b54d072ce9837f9b15694f2d7100817de62e9762
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241770"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a><span data-ttu-id="927a2-102">Jak číst textový soubor po jednotlivých řádcích (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="927a2-102">How to read a text file one line at a time (C# Programming Guide)</span></span>
<span data-ttu-id="927a2-103">Tento příklad přečte obsah textového souboru, jeden řádek v čase, do řetězce pomocí `ReadLine` metody `StreamReader` třídy.</span><span class="sxs-lookup"><span data-stu-id="927a2-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="927a2-104">Každý textový řádek je uložen do řetězce `line` a zobrazený na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="927a2-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="927a2-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="927a2-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="927a2-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="927a2-106">Compiling the Code</span></span>  
 <span data-ttu-id="927a2-107">Zkopírujte kód a vložte ho do `Main` metody konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="927a2-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="927a2-108">Nahraďte `"c:\test.txt"` skutečným názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="927a2-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="927a2-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="927a2-109">Robust Programming</span></span>  
 <span data-ttu-id="927a2-110">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="927a2-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="927a2-111">Soubor možná neexistuje.</span><span class="sxs-lookup"><span data-stu-id="927a2-111">The file may not exist.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="927a2-112">Zabezpečení .NET</span><span class="sxs-lookup"><span data-stu-id="927a2-112">.NET Security</span></span>  
 <span data-ttu-id="927a2-113">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="927a2-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="927a2-114">Soubor nemůže `myFile.cs` být například zdrojový soubor C#.</span><span class="sxs-lookup"><span data-stu-id="927a2-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="927a2-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="927a2-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="927a2-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="927a2-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="927a2-117">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="927a2-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
