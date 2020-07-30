---
title: Jak číst textový soubor po jednom řádku v průběhu času – Průvodce programováním v C#
description: Naučte se, jak číst textový soubor po jednotlivých řádcích. Podívejte se na příklad kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: 1e29013b1008e1000c23804dc3056014cc7c104b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301954"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a><span data-ttu-id="4ac0c-104">Jak číst textový soubor po jednotlivých řádcích (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4ac0c-104">How to read a text file one line at a time (C# Programming Guide)</span></span>
<span data-ttu-id="4ac0c-105">Tento příklad přečte obsah textového souboru, jeden řádek v čase, do řetězce pomocí `ReadLine` metody `StreamReader` třídy.</span><span class="sxs-lookup"><span data-stu-id="4ac0c-105">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="4ac0c-106">Každý textový řádek je uložen do řetězce `line` a zobrazený na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="4ac0c-106">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ac0c-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="4ac0c-107">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="4ac0c-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4ac0c-108">Compiling the Code</span></span>  
 <span data-ttu-id="4ac0c-109">Zkopírujte kód a vložte ho do `Main` metody konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="4ac0c-109">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="4ac0c-110">Nahraďte `"c:\test.txt"` skutečným názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="4ac0c-110">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4ac0c-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="4ac0c-111">Robust Programming</span></span>  
 <span data-ttu-id="4ac0c-112">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="4ac0c-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="4ac0c-113">Soubor možná neexistuje.</span><span class="sxs-lookup"><span data-stu-id="4ac0c-113">The file may not exist.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="4ac0c-114">Zabezpečení .NET</span><span class="sxs-lookup"><span data-stu-id="4ac0c-114">.NET Security</span></span>  
 <span data-ttu-id="4ac0c-115">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="4ac0c-115">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="4ac0c-116">Soubor nemůže `myFile.cs` být například zdrojový soubor C#.</span><span class="sxs-lookup"><span data-stu-id="4ac0c-116">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ac0c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ac0c-117">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="4ac0c-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="4ac0c-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4ac0c-119">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4ac0c-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
