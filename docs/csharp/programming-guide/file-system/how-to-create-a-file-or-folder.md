---
title: Postup vytvoření souboru nebo složky – Průvodce programováním v C#
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: 5efe3b7dc600645488816d6f931df57fc236efc9
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241640"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a>Postup vytvoření souboru nebo složky (Průvodce programováním v C#)
Můžete programově vytvořit složku v počítači, vytvořit podsložku, vytvořit soubor v podsložce a zapsat data do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 Pokud složka již existuje, <xref:System.IO.Directory.CreateDirectory%2A> neprovede žádnou akci a není vyvolána žádná výjimka. Ale <xref:System.IO.File.Create%2A?displayProperty=nameWithType> nahradí existující soubor novým souborem. V příkladu se používá `if` - `else` příkaz, který brání v nahrazení existujícího souboru.  
  
 Provedením následujících změn v příkladu můžete určit různé výsledky na základě toho, zda soubor s určitým názvem již existuje. Pokud takový soubor neexistuje, kód ho vytvoří. Pokud takový soubor existuje, kód připojí data do tohoto souboru.  
  
- Zadejte jiný než náhodný název souboru.  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- Nahraďte `if` - `else` příkaz `using` příkazem v následujícím kódu.  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 Spusťte příklad několikrát, abyste ověřili, že se data do souboru přidávají pokaždé.  
  
 Další `FileMode` hodnoty, které můžete vyzkoušet, najdete v tématu <xref:System.IO.FileMode> .  
  
 Následující podmínky mohou způsobit výjimku:  
  
- Název složky je poškozený. Například obsahuje neplatné znaky nebo je pouze mezera ( <xref:System.ArgumentException> třída). Použijte <xref:System.IO.Path> třídu k vytvoření platných názvů cest.  
  
- Nadřazená složka složky, která se má vytvořit, je jen pro čtení ( <xref:System.IO.IOException> třída).  
  
- Název složky je `null` ( <xref:System.ArgumentNullException> Class).  
  
- Název složky je příliš dlouhý ( <xref:System.IO.PathTooLongException> třída).  
  
- Název složky je pouze dvojtečka, ":" ( <xref:System.IO.PathTooLongException> třída).  
  
## <a name="net-security"></a>Zabezpečení .NET  
 Instance <xref:System.Security.SecurityException> třídy může být vyvolána v situacích částečné důvěryhodnosti.  
  
 Pokud nemáte oprávnění k vytvoření složky, příklad vyvolá instanci <xref:System.UnauthorizedAccessException> třídy.  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO?displayProperty=nameWithType>
- [Průvodce programováním v C#](../index.md)
- [Systém souborů a registr (Průvodce programováním v C#)](./index.md)
