---
title: "Postupy: Odstranění souboru v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 536c10070ef51044b801fc6a5805741896586dff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-a-file-in-visual-basic"></a>Postupy: Odstranění souboru v jazyce Visual Basic
`DeleteFile` Metodu `My.Computer.FileSystem` objekt umožňuje odstranit soubor. Nabízí možnosti jsou: zda odstraněné soubor k **Koš**, zda má být požádat uživatele o potvrzení, že soubor by měl odstranit a co dělat, když uživatel operaci zruší.  
  
### <a name="to-delete-a-text-file"></a>Chcete-li odstranit textový soubor  
  
-   Použití `DeleteFile` metoda k odstranění tohoto souboru. Následující kód ukazuje, jak odstranit soubor s názvem `test.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a>K odstranění textového souboru a požádat uživatele o potvrzení, že by měl odstranit soubor  
  
-   Použití `DeleteFile` metoda k odstranění tohoto souboru, nastavení `showUI` k `AllDialogs`. Následující kód ukazuje, jak odstranit soubor s názvem `test.txt` a povolit uživatele k potvrzení, že soubor měla by být odstraněna.  
  
     [!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a>K odstranění textového souboru a odeslat do koše  
  
-   Použití `DeleteFile` metoda k odstranění tohoto souboru zadání `SendToRecycleBin` pro `recycle` parametr. Následující kód ukazuje, jak odstranit soubor s názvem `test.txt` a jeho odeslání **Koš**.  
  
     [!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
-   Soubor je používán (<xref:System.IO.IOException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
-   Soubor neexistuje (<xref:System.IO.FileNotFoundException>).  
  
-   Uživatel nemá oprávnění k odstranění tohoto souboru nebo souboru je jen pro čtení (<xref:System.UnauthorizedAccessException>).  
  
-   Částečné důvěryhodnosti situaci existuje, ve kterém uživatel nemá dostatečná oprávnění (<xref:System.Security.SecurityException>).  
  
-   Uživatel zrušil operaci a `onUserCancel` je nastaven na `ThrowException` (<xref:System.OperationCanceledException>).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.UIOption>  
 <xref:Microsoft.VisualBasic.FileIO.RecycleOption>  
 [Postupy: získání kolekce souborů v adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
