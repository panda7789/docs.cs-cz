---
title: 'Postupy: Vytváření souborů nebo složek (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: d69885b420d28878072a70dfd2288905cf13de1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a>Postupy: Vytváření souborů nebo složek (Průvodce programováním v C#)
Můžete prostřednictvím kódu programu vytvořte složku v počítači, vytvořit podsložky, vytvořte soubor v podsložce a zapisovat data do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csFilesandFolders#10](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-create-a-file-or-folder_1.cs)]  
  
 Pokud daná složka již existuje, <xref:System.IO.Directory.CreateDirectory%2A> nemá, je vyvolána nic a žádná výjimka. Ale <xref:System.IO.File.Create%2A?displayProperty=nameWithType> nahradí existující soubor nový soubor. V příkladu se používá `if` - `else` příkaz zabránit nahrazují existující soubor.  
  
 Tím, že provedete následující změny v příkladu, můžete zadat různé výsledky podle toho, zda je soubor s určitým názvem již existuje. Pokud takový soubor neexistuje, kód vytvoří. Pokud takový soubor neexistuje, kód připojí data k souboru.  
  
-   Zadejte název souboru bez náhodné.  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
-   Nahraďte `if` - `else` příkaz s `using` příkaz v následujícím kódu.  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 V příkladu spustit několikrát ověření dat se přidá do souboru pokaždé, když.  
  
 Další informace `FileMode` hodnoty, které můžete vyzkoušet, najdete v části <xref:System.IO.FileMode>.  
  
 Následující podmínky mohou způsobit výjimku:  
  
-   Název složky není správně vytvořen. Například obsahuje neplatné znaky nebo je pouze mezera (<xref:System.ArgumentException> třídy). Použití <xref:System.IO.Path> třídy za účelem vytvoření názvy platnou cestu.  
  
-   Nadřazená složka vytvořit složku je jen pro čtení (<xref:System.IO.IOException> třídy).  
  
-   Je název složky `null` (<xref:System.ArgumentNullException> třídy).  
  
-   Název složky je příliš dlouhý (<xref:System.IO.PathTooLongException> třídy).  
  
-   Pouze dvojtečku, je název složky ":" (<xref:System.IO.PathTooLongException> třídy).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Instance <xref:System.Security.SecurityException> třída může být vyvolána v situacích s částečným vztahem důvěryhodnosti.  
  
 Pokud nemáte oprávnění vytvořit složku, v příkladu vyvolá instanci <xref:System.UnauthorizedAccessException> třídy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO?displayProperty=nameWithType>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Systém souborů a registr (C# Průvodce programováním)](../../../csharp/programming-guide/file-system/index.md)
