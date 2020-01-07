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
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a>Jak číst textový soubor po jednotlivých řádcích (C# Průvodce programováním)
Tento příklad přečte obsah textového souboru, jeden řádek v čase, do řetězce pomocí metody `ReadLine` třídy `StreamReader`. Každý textový řádek je uložen do řetězce `line` a zobrazený na obrazovce.  
  
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
 Zkopírujte kód a vložte ho do metody `Main` konzolové aplikace.  
  
 Nahraďte `"c:\test.txt"` skutečným názvem souboru.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Soubor možná neexistuje.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Soubor `myFile.cs` například nemusí být C# zdrojový soubor.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO?displayProperty=nameWithType>
- [Průvodce programováním v jazyce C#](../index.md)
- [Systém souborů a registr (C# Průvodce programováním)](./index.md)
