---
title: 'Postupy: Odstranění souboru v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: c083855ea298fa62459d107651e62c13d65c52c5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972830"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a>Postupy: Odstranění souboru v jazyce Visual Basic
`DeleteFile` Metodu `My.Computer.FileSystem` objekt umožňuje odstranění souboru. Nabízí možnosti jsou:, jestli se má odeslat odstraněný soubor **koše**, zda požádat uživatele o potvrzení, že soubor by měl odstranit a co dělat, když uživatel ruší operaci.  
  
### <a name="to-delete-a-text-file"></a>Chcete-li odstranit textového souboru  
  
-   Použití `DeleteFile` metodu pro stejný soubor odstranit také. Následující kód ukazuje, jak odstranit soubor s názvem `test.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a>Chcete odstranit textového souboru a požádat uživatele, abyste potvrdili, že soubor by se měla odstranit  
  
-   Použití `DeleteFile` metoda odstranit soubor nastavení `showUI` k `AllDialogs`. Následující kód ukazuje, jak odstranit soubor s názvem `test.txt` a umožnit uživateli pro potvrzení, že soubor by měl odstranit.  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a>Chcete odstranit textového souboru a odeslat ho do složky Koš  
  
-   Použití `DeleteFile` metodu pro odstranění souboru, zadávání `SendToRecycleBin` pro `recycle` parametru. Následující kód ukazuje, jak odstranit soubor s názvem `test.txt` a odeslat ji **koše**.  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje pouze mezeru, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
-   Soubor je používán (<xref:System.IO.IOException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
-   Soubor neexistuje (<xref:System.IO.FileNotFoundException>).  
  
-   Uživatel nemá oprávnění k odstranění souboru nebo souboru je jen pro čtení (<xref:System.UnauthorizedAccessException>).  
  
-   Částečné důvěryhodnosti situace existuje, ve kterém uživatel nemá dostatečná oprávnění (<xref:System.Security.SecurityException>).  
  
-   Uživatel zrušil operaci a `onUserCancel` je nastavena na `ThrowException` (<xref:System.OperationCanceledException>).  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [Postupy: Získání kolekce souborů v adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
