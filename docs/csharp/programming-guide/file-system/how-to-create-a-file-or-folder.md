---
title: 'Postupy: Vytváření souborů nebo složek (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: 34919efe32730fe0db11cb881b8e07629a3094fd
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43884799"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a>Postupy: Vytváření souborů nebo složek (Průvodce programováním v C#)
Můžete prostřednictvím kódu programu vytvořte složku v počítači, vytvořte podsložku, vytvořit soubor v podsložce a zapisovat data do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csFilesandFolders#10](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-create-a-file-or-folder_1.cs)]  
  
 Pokud složka již existuje, <xref:System.IO.Directory.CreateDirectory%2A> fakturuje se nic a žádná výjimka je vyvolána výjimka. Ale <xref:System.IO.File.Create%2A?displayProperty=nameWithType> nahradí existující soubor do nového souboru. V příkladu se používá `if` - `else` příkaz zabránit nahrazuje existující soubor.  
  
 Provedením následujících změn v příkladu, můžete určit různé výsledky založené na tom, jestli soubor s určitým názvem již existuje. Pokud takový soubor neexistuje, kód ho vytvoří. Pokud takový soubor existuje, kód připojí data do tohoto souboru.  
  
-   Zadejte nenáhodný název.  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
-   Nahradit `if` - `else` příkaz `using` příkaz v následujícím kódu.  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 Spusťte příklad několikrát ověření tato data se přidá do souboru pokaždé, když.  
  
 Další informace `FileMode` hodnoty, které můžete vyzkoušet, naleznete v tématu <xref:System.IO.FileMode>.  
  
 Následující podmínky mohou způsobit výjimku:  
  
-   Název složky je chybný. Například obsahuje neplatné znaky nebo je prázdné znaky (<xref:System.ArgumentException> třídy). Použití <xref:System.IO.Path> třídy za účelem vytvoření platné názvy cesty.  
  
-   Nadřazená složka složky, který se má vytvořit je jen pro čtení (<xref:System.IO.IOException> třídy).  
  
-   Název složky je `null` (<xref:System.ArgumentNullException> třídy).  
  
-   Název složky je příliš dlouhý (<xref:System.IO.PathTooLongException> třídy).  
  
-   Název složky je pouze dvojtečka ":" (<xref:System.IO.PathTooLongException> třídy).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Instance <xref:System.Security.SecurityException> třídy může být vyvolána v situacích částečné důvěryhodnosti.  
  
 Pokud nemáte oprávnění k vytvoření složky, příklad vyvolá instanci <xref:System.UnauthorizedAccessException> třídy.  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO?displayProperty=nameWithType>  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Systém souborů a registr (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md)
