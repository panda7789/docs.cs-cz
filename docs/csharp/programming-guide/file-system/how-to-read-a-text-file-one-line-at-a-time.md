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
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a>Jak číst textový soubor po jednotlivých řádcích (Průvodce programováním v C#)
Tento příklad přečte obsah textového souboru, jeden řádek v čase, do řetězce pomocí `ReadLine` metody `StreamReader` třídy. Každý textový řádek je uložen do řetězce `line` a zobrazený na obrazovce.  
  
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
 Zkopírujte kód a vložte ho do `Main` metody konzolové aplikace.  
  
 Nahraďte `"c:\test.txt"` skutečným názvem souboru.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Soubor možná neexistuje.  
  
## <a name="net-security"></a>Zabezpečení .NET  
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Soubor nemůže `myFile.cs` být například zdrojový soubor C#.  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO?displayProperty=nameWithType>
- [Průvodce programováním v C#](../index.md)
- [Systém souborů a registr (Průvodce programováním v C#)](./index.md)
