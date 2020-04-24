---
title: 'Postupy: Vytvoření kopie souboru v jiném adresáři'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: e9a14e1f3743979548b92a3db653d09a470a1875
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348833"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a>Postupy: Vytvoření kopie souboru v jiném adresáři v jazyce Visual Basic

`My.Computer.FileSystem.CopyFile` Metoda umožňuje kopírování souborů. Jeho parametry poskytují možnost přepsat stávající soubory, přejmenovat soubor, zobrazit průběh operace a umožnit uživateli zrušit operaci.  
  
### <a name="to-copy-a-text-file-to-another-folder"></a>Zkopírování textového souboru do jiné složky  
  
- Použijte `CopyFile` metodu ke zkopírování souboru, zadání zdrojového souboru a cílového adresáře. `overwrite` Parametr umožňuje určit, jestli se mají přepsat existující soubory. Následující příklady kódu ukazují, jak použít `CopyFile`.  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit vyvolání výjimky:  
  
- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná \\ \\na.\\) (<xref:System.ArgumentException>).  
  
- Systém nemůže načíst absolutní cestu (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).  
  
- Zdrojový soubor není platný nebo neexistuje (<xref:System.IO.FileNotFoundException>).  
  
- Kombinovaná cesta odkazuje na existující adresář (<xref:System.IO.IOException>).  
  
- Cílový soubor existuje a `overwrite` je nastaven na `False` hodnotu (<xref:System.IO.IOException>).  
  
- Uživatel nemá dostatečná oprávnění pro přístup k souboru (<xref:System.IO.IOException>).  
  
- Soubor v cílové složce se stejným názvem se používá (<xref:System.IO.IOException>).  
  
- Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu format<xref:System.NotSupportedException>().  
  
- `ShowUI`je nastaven na `True`, `onUserCancel` je nastaven na `ThrowException`a uživatel zrušil operaci (<xref:System.OperationCanceledException>).  
  
- `ShowUI`je nastaven na `True`, `onUserCancel` je nastaven na `ThrowException`a dojde k nespecifikované vstupně-výstupní chybě (<xref:System.OperationCanceledException>).  
  
- Cesta přesahuje maximální povolenou délku (<xref:System.IO.PathTooLongException>) definovanou systémem.  
  
- Uživatel nemá požadovaná oprávnění (<xref:System.UnauthorizedAccessException>).  
  
- Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [Postupy: Vytvoření kopie souboru ve stejném adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Postupy: Zkopírování adresáře do jiného adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [Postupy: Přejmenování souboru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
