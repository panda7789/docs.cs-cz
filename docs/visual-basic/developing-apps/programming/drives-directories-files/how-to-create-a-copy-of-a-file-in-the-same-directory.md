---
title: 'Postupy: Vytvoření kopie souboru ve stejném adresáři v jazyce Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: 1147e89292181060589b38be2972e2ff1a3e386c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a>Postupy: Vytvoření kopie souboru ve stejném adresáři v jazyce Visual Basic
Použití `My.Computer.FileSystem.CopyFile` metoda kopírování souborů. Parametry umožňují přepsat existující soubory, přejmenujte soubor, zobrazit průběh operace a umožní uživateli na tlačítko Storno.  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a>Vytvoření kopie souboru ve stejné složce  
  
-   Použití `CopyFile` metoda, poskytuje cílový soubor a umístění. Následující příklad vytvoří kopii `test.txt` názvem `test2.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#51](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_1.vb)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a>Vytvoření kopie souboru ve stejné složce, přepíše existující soubory  
  
-   Použití `CopyFile` metoda, poskytuje cílový soubor a umístění a nastavení `overwrite` k `True`. Následující příklad vytvoří kopii `test.txt` názvem `test2.txt` a přepíše všechny existující soubory s tímto názvem.  
  
     [!code-vb[VbVbcnMyFileSystem#52](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_2.vb)]  
  
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
  
-   `ShowUI` je nastavena na `True`, `onUserCancel` je nastaven na `ThrowException`, a uživatel zrušil operaci (<xref:System.OperationCanceledException>).  
  
-   `ShowUI` je nastavena na `True`, `onUserCancel` je nastaven na `ThrowException`, a dojde k nespecifikované chybě vstupně-výstupní operace (<xref:System.OperationCanceledException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Uživatel nemá požadované oprávnění (<xref:System.UnauthorizedAccessException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 [Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)  
 [Postupy: Vytvoření kopie souboru v jiném adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)  
 [Postupy: Zkopírování adresáře do jiného adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)  
 [Postupy: Přejmenování souboru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
