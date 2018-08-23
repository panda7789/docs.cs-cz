---
title: 'Postupy: Čtení textového souboru po řádcích (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: b31e3f0164b2a2094e84263702c52c2817219d20
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2018
ms.locfileid: "42753915"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-visual-c"></a>Postupy: Čtení textového souboru po řádcích (Průvodce programováním v C#)
Tento příklad přečte obsah textového souboru, jednořádkový najednou, do řetězce pomocí `ReadLine` metodu `StreamReader` třídy. Každý řádek textu je uložen do řetězce `line` a zobrazí na obrazovce.  
  
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
 Zkopírujte kód a vložte ho do `Main` metoda konzolové aplikace.  
  
 Nahraďte `"c:\test.txt"` pomocí skutečného názvu souboru.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Soubor neexistuje.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor `myFile.cs` nemusí být zdrojový soubor jazyka C#.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO?displayProperty=nameWithType>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Systém souborů a registr (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md)
