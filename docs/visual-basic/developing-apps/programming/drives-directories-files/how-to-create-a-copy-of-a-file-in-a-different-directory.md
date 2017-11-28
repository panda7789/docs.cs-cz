---
title: "Postupy: Vytvoření kopie souboru v jiném adresáři v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0fe37ba940172e83574505d4c82e196f60dfc1eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a>Postupy: Vytvoření kopie souboru v jiném adresáři v jazyce Visual Basic
`My.Computer.FileSystem.CopyFile` Metoda umožňuje kopírovat soubory. Jeho parametry umožňují přepsat existující soubory, přejmenujte soubor, zobrazit průběh operace a umožní uživateli na tlačítko Storno.  
  
### <a name="to-copy-a-text-file-to-another-folder"></a>Zkopírovat do textového souboru do jiné složky  
  
-   Použití `CopyFile` metoda zkopírovat soubor, zadáním zdrojového souboru a cílové složky. `overwrite` Parametr umožňuje určit, zda chcete přepsat existující soubory. Následující příklady kódu ukazují, jak používat `CopyFile`.  
  
     [!code-vb[VbFileIOMisc#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-a-different-directory_1.vb)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Vyvolání výjimky může způsobit následující podmínky:  
  
-   Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Systém nemohl načíst absolutní cestu (<xref:System.ArgumentException>).  
  
-   Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Zdrojový soubor je neplatný nebo neexistuje (<xref:System.IO.FileNotFoundException>).  
  
-   Kombinované cesta odkazuje na existující adresář (<xref:System.IO.IOException>).  
  
-   Cílový soubor existuje a `overwrite` je nastaven na `False` (<xref:System.IO.IOException>).  
  
-   Uživatel nemá dostatečná oprávnění k přístupu k souboru (<xref:System.IO.IOException>).  
  
-   Soubor v cílové složce se stejným názvem je používán (<xref:System.IO.IOException>).  
  
-   Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
-   `ShowUI`je nastavena na `True`, `onUserCancel` je nastaven na `ThrowException`, a uživatel zrušil operaci (<xref:System.OperationCanceledException>).  
  
-   `ShowUI`je nastavena na `True`, `onUserCancel` je nastaven na `ThrowException`, a dojde k nespecifikované chybě vstupně-výstupní operace (<xref:System.OperationCanceledException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Uživatel nemá požadované oprávnění (<xref:System.UnauthorizedAccessException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 [Postupy: kopírování souborů vyhovujících určitému vzoru do jiného adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)  
 [Postupy: vytvoření kopie souboru ve stejném adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)  
 [Postupy: zkopírování adresáře do jiného adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)  
 [Postupy: přejmenování souboru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
