---
title: 'Postupy: Odstranění souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 0c8213786b8073d784f1f3ea51417741d5ad4cba
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401651"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a>Postupy: Odstranění souboru v jazyce Visual Basic

`DeleteFile`Metoda `My.Computer.FileSystem` objektu umožňuje odstranit soubor. Mezi možnosti, které nabízí, patří: bez ohledu na to, jestli se má odstraněný soubor poslat do **koše**, jestli se má uživatel položit, aby zkontroloval, jestli by se měl soubor odstranit, a co dělat, když uživatel operaci zruší.  
  
### <a name="to-delete-a-text-file"></a>Odstranění textového souboru  
  
- `DeleteFile`K odstranění souboru použijte metodu. Následující kód ukazuje, jak odstranit soubor s názvem `test.txt` .  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a>Odstranění textového souboru a požádejte uživatele o potvrzení, že by se měl soubor odstranit  
  
- Pomocí `DeleteFile` metody odstraňte soubor a nastavte `showUI` na `AllDialogs` . Následující kód ukazuje, jak odstranit soubor s názvem `test.txt` a umožní uživateli potvrdit, že by měl být soubor smazán.  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a>Odstranění textového souboru a jeho odeslání do odpadkového koše  
  
- Použijte `DeleteFile` metodu k odstranění souboru, který určuje `SendToRecycleBin` `recycle` parametr. Následující kód ukazuje, jak odstranit soubor s názvem `test.txt` a odeslat ho do **odpadkového koše**.  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .  
  
- Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).  
  
- Soubor se používá ( <xref:System.IO.IOException> ).  
  
- Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ).  
  
- Soubor neexistuje ( <xref:System.IO.FileNotFoundException> ).  
  
- Uživatel nemá oprávnění k odstranění tohoto souboru, nebo je soubor jen pro čtení ( <xref:System.UnauthorizedAccessException> ).  
  
- V případě, že uživatel nemá dostatečná oprávnění (), existuje situace s částečným vztahem důvěryhodnosti <xref:System.Security.SecurityException> .  
  
- Uživatel operaci zrušil a `onUserCancel` je nastaven na `ThrowException` ( <xref:System.OperationCanceledException> ).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [Postupy: Získání kolekce souborů z adresáře](how-to-get-the-collection-of-files-in-a-directory.md)
