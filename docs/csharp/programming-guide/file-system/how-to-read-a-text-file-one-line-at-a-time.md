---
title: Jak číst textový soubor po jednom řádku v C# programovací příručce pro čas
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: a6af48cdacd836465d776a3fd4e1d17aa0298b77
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635337"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a><span data-ttu-id="35556-102">Jak číst textový soubor po jednotlivých řádcích (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="35556-102">How to read a text file one line at a time (C# Programming Guide)</span></span>
<span data-ttu-id="35556-103">Tento příklad přečte obsah textového souboru, jeden řádek v čase, do řetězce pomocí metody `ReadLine` třídy `StreamReader`.</span><span class="sxs-lookup"><span data-stu-id="35556-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="35556-104">Každý textový řádek je uložen do řetězce `line` a zobrazený na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="35556-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35556-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="35556-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="35556-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="35556-106">Compiling the Code</span></span>  
 <span data-ttu-id="35556-107">Zkopírujte kód a vložte ho do metody `Main` konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="35556-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="35556-108">Nahraďte `"c:\test.txt"` skutečným názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="35556-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="35556-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="35556-109">Robust Programming</span></span>  
 <span data-ttu-id="35556-110">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="35556-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="35556-111">Soubor možná neexistuje.</span><span class="sxs-lookup"><span data-stu-id="35556-111">The file may not exist.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="35556-112">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="35556-112">.NET Framework Security</span></span>  
 <span data-ttu-id="35556-113">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="35556-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="35556-114">Soubor `myFile.cs` například nemusí být C# zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="35556-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35556-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35556-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="35556-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="35556-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="35556-117">Systém souborů a registr (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="35556-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
