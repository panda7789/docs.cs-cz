---
title: Jak číst textový soubor po jednom řádku - C# Programming Guide
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: e4a9ba2da2548991f442c2f5ab09d39243137875
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167507"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a><span data-ttu-id="ec618-102">Jak číst textový soubor po jednom řádku (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ec618-102">How to read a text file one line at a time (C# Programming Guide)</span></span>
<span data-ttu-id="ec618-103">Tento příklad přečte obsah textového souboru, jeden řádek v `ReadLine` době, `StreamReader` do řetězce pomocí metody třídy.</span><span class="sxs-lookup"><span data-stu-id="ec618-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="ec618-104">Každý řádek textu je `line` uložen do řetězce a zobrazen na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="ec618-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec618-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec618-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="ec618-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ec618-106">Compiling the Code</span></span>  
 <span data-ttu-id="ec618-107">Zkopírujte kód a vložte jej do `Main` metody konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec618-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="ec618-108">Nahraďte `"c:\test.txt"` skutečným názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="ec618-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ec618-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="ec618-109">Robust Programming</span></span>  
 <span data-ttu-id="ec618-110">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="ec618-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="ec618-111">Soubor pravděpodobně neexistuje.</span><span class="sxs-lookup"><span data-stu-id="ec618-111">The file may not exist.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ec618-112">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ec618-112">.NET Framework Security</span></span>  
 <span data-ttu-id="ec618-113">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="ec618-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="ec618-114">Například soubor `myFile.cs` nemusí být zdrojový soubor Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="ec618-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec618-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec618-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="ec618-116">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ec618-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ec618-117">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ec618-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
