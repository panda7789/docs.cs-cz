---
title: 'Postupy: Čtení textového souboru po řádcích (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: 75274d93ee29feb5f79dfc29c24109f25fd98a5c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589960"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-visual-c"></a>Postupy: Čtení textového souboru po řádcích (Průvodce programováním v C#)
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
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Soubor `myFile.cs` nemůže být například C# zdrojový soubor.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO?displayProperty=nameWithType>
- [Průvodce programováním v jazyce C#](../index.md)
- [Systém souborů a registr (C# Průvodce programováním)](./index.md)
