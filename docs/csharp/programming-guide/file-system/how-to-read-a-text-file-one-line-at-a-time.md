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
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a>Jak číst textový soubor po jednom řádku (Průvodce programováním jazyka C#)
Tento příklad přečte obsah textového souboru, jeden řádek v `ReadLine` době, `StreamReader` do řetězce pomocí metody třídy. Každý řádek textu je `line` uložen do řetězce a zobrazen na obrazovce.  
  
## <a name="example"></a>Příklad  
  
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
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Zkopírujte kód a vložte jej do `Main` metody konzolové aplikace.  
  
 Nahraďte `"c:\test.txt"` skutečným názvem souboru.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Soubor pravděpodobně neexistuje.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor `myFile.cs` nemusí být zdrojový soubor Jazyka C#.  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO?displayProperty=nameWithType>
- [Programovací příručka jazyka C#](../index.md)
- [Systém souborů a registr (Průvodce programováním v C#)](./index.md)
