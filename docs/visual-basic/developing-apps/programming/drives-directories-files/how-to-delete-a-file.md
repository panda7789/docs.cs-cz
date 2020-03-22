---
title: 'Postupy: Odstranění souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 57182f1a1d92b7fe954fd26b32c5e4b1107823ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348784"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a>Postupy: Odstranění souboru v jazyce Visual Basic

Metoda `DeleteFile` objektu `My.Computer.FileSystem` umožňuje odstranit soubor. Mezi možnosti, které nabízí, patří: zda odeslat odstraněný soubor do **koše**, zda požádat uživatele o potvrzení, že soubor by měl být odstraněn, a co dělat, když uživatel zruší operaci.  
  
### <a name="to-delete-a-text-file"></a>Odstranění textového souboru  
  
- Pomocí `DeleteFile` metody odstraňte soubor. Následující kód ukazuje, jak odstranit `test.txt`soubor s názvem .  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a>Odstranění textového souboru a požádejte uživatele o potvrzení, že má být soubor odstraněn  
  
- Pomocí `DeleteFile` metody odstraňte soubor `showUI` a `AllDialogs`nastavením na . Následující kód ukazuje, jak odstranit `test.txt` pojmenovaný soubor a umožnit uživateli potvrdit, že soubor by měl být odstraněn.  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a>Odstranění textového souboru a jeho odeslání do koše  
  
- Pomocí `DeleteFile` metody odstraňte soubor a `SendToRecycleBin` určete `recycle` parametr. Následující kód ukazuje, jak odstranit `test.txt` pojmenovaný soubor a odeslat jej do **koše**.  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky, obsahuje pouze prázdné znaky, \\ \\\\obsahuje neplatné znaky nebo se jedná o cestu zařízení (začíná na . ) (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).  
  
- Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).  
  
- Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
- Soubor je používán<xref:System.IO.IOException>( ).  
  
- Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ).  
  
- Soubor neexistuje (<xref:System.IO.FileNotFoundException>).  
  
- Uživatel nemá oprávnění k odstranění souboru nebo je soubor<xref:System.UnauthorizedAccessException>jen pro čtení ( ).  
  
- Existuje situace částečné důvěryhodnosti, ve které uživatel nemá<xref:System.Security.SecurityException>dostatečná oprávnění ( ).  
  
- Uživatel operaci zrušil a `onUserCancel` je `ThrowException` nastavenna na (<xref:System.OperationCanceledException>).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [Postupy: Získání kolekce souborů z adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
