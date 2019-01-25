---
title: 'Postupy: Přesunutí souboru v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: 6888531918dd932ba5acb3ec967303568606d5df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721939"
---
# <a name="how-to-move-a-file-in-visual-basic"></a>Postupy: Přesunutí souboru v jazyce Visual Basic
`My.Computer.FileSystem.MoveFile` Metodu je možné přesunout soubor do jiné složky. Pokud cílová struktura neexistuje, vytvoří se.  
  
### <a name="to-move-a-file"></a>Chcete-li přesunout soubor  
  
-   Použití `MoveFile` metoda se přesunout soubor, zadáním názvu souboru a umístění zdrojového souboru a cílový soubor. V tomto příkladu přesune soubor s názvem `test.txt` z `TestDir1` k `TestDir2`. Všimněte si, že je zadán název cílového souboru, i když je stejný jako název zdrojového souboru.  
  
     [!code-vb[VbVbcnMyFileSystem#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_1.vb)]  
  
### <a name="to-move-a-file-and-rename-it"></a>Chcete-li přesunout soubor a přejmenujte jej na  
  
-   Použití `MoveFile` metoda se přesunout soubor, zadáte název zdrojového souboru a umístění, cílové umístění a název nového v cílovém umístění. V tomto příkladu přesune soubor s názvem `test.txt` z `TestDir1` k `TestDir2` a přejmenuje ho `nexttest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#25](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_2.vb)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje pouze mezeru, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `destinationFileName` je `Nothing` nebo prázdný řetězec (<xref:System.ArgumentNullException>).  
  
-   Zdrojový soubor je neplatný nebo neexistuje (<xref:System.IO.FileNotFoundException>).  
  
-   Body kombinovanou cestu k existujícímu adresáři, cílový soubor existuje a `overwrite` je nastavena na `False`, soubor v cílovém adresáři se stejným názvem se používá, nebo uživatel nemá dostatečná oprávnění pro přístup k souboru (<xref:System.IO.IOException> ).  
  
-   Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
-   `showUI` je nastavena na `True`, `onUserCancel` je nastavena na `ThrowException`a buď uživatel zrušil operaci nebo dojde k nespecifikované chybě vstupně-výstupních operací (<xref:System.OperationCanceledException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
-   Uživatel nemá požadovaná oprávnění (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [Postupy: Přejmenovat soubor](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
- [Postupy: Vytvoření kopie souboru v jiném adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Postupy: Analýza cest k souborům](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
