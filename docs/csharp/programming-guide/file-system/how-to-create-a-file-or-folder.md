---
title: Jak vytvořit soubor nebo složku - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: cdcc0a375aa1eca29c024d1e0c9008f337d0c772
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167554"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a>Jak vytvořit soubor nebo složku (C# Programming Guide)
Můžete programově vytvořit složku v počítači, vytvořit podsložku, vytvořit soubor v podsložce a zapsat data do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 Pokud složka již existuje, <xref:System.IO.Directory.CreateDirectory%2A> neprovede žádnou akci a není vyvolána žádná výjimka. Nahradí <xref:System.IO.File.Create%2A?displayProperty=nameWithType> však existující soubor novým souborem. Příklad používá `if` - `else` příkaz, který zabraňuje nahrazení existujícího souboru.  
  
 Provedením následujících změn v příkladu můžete určit různé výsledky na základě toho, zda soubor s určitým názvem již existuje. Pokud takový soubor neexistuje, kód jej vytvoří. Pokud takový soubor existuje, kód připojí data k tomuto souboru.  
  
- Zadejte název nenáhodného souboru.  
  
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
  
 Spusťte příklad několikrát ověřit, že data jsou přidána do souboru pokaždé.  
  
 Další `FileMode` hodnoty, které můžete <xref:System.IO.FileMode>vyzkoušet, naleznete v tématu .  
  
 Následující podmínky mohou způsobit výjimku:  
  
- Název složky je poškozen. Obsahuje například neplatné znaky nebo je<xref:System.ArgumentException> pouze prázdné znaky (třída). Pomocí <xref:System.IO.Path> třídy vytvořte platné názvy cest.  
  
- Nadřazená složka složky, která<xref:System.IO.IOException> má být vytvořena, je jen pro čtení (třída).  
  
- Název složky `null` <xref:System.ArgumentNullException> je (třída).  
  
- Název složky je<xref:System.IO.PathTooLongException> příliš dlouhý (třída).  
  
- Název složky je pouze dvojtečka, ":"(<xref:System.IO.PathTooLongException> třída).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Instance třídy <xref:System.Security.SecurityException> může být vyvolána v situacích částečné důvěryhodnosti.  
  
 Pokud nemáte oprávnění k vytvoření složky, příklad vyvolá instanci <xref:System.UnauthorizedAccessException> třídy.  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO?displayProperty=nameWithType>
- [Programovací příručka jazyka C#](../index.md)
- [Systém souborů a registr (Průvodce programováním v C#)](./index.md)
