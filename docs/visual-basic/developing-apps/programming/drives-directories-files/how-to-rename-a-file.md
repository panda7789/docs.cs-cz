---
title: 'Postupy: Přejmenování souboru v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: 3b1e85cc9e0b0768f7065ff690f6dc969ee040b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676364"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a>Postupy: Přejmenování souboru v jazyce Visual Basic
Použití `RenameFile` metodu `My.Computer.FileSystem` objektu přejmenovat soubor zadáním aktuální umístění, název souboru a název nového souboru. Tuto metodu nelze použít k přesouvání souborů. použít `MoveFile` metody pro přesun a přejmenujte soubor.  
  
### <a name="to-rename-a-file"></a>Pokud chcete přejmenovat soubor  
  
-   Použití `My.Computer.FileSystem.RenameFile` metoda chcete přejmenovat soubor. Tento příklad přejmenuje soubor s názvem `Test.txt` k `SecondTest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-rename-a-file_1.vb)]  
  
 Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense. V dialogu pro výběr fragmentu kódu fragmentu kódu je umístěn v **souborový systém – zpracování jednotek, složek a souborů**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje pouze mezeru, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   `newName` obsahuje informace o cestě (<xref:System.ArgumentException>).  
  
-   Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `newName` je `Nothing` nebo prázdný řetězec (<xref:System.ArgumentNullException>).  
  
-   Zdrojový soubor je neplatný nebo neexistuje (<xref:System.IO.FileNotFoundException>).  
  
-   Jde o existující soubor nebo adresář s názvem zadaným v `newName` (<xref:System.IO.IOException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
-   Uživatel nemá požadovaná oprávnění (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [Postupy: Přesunutí souboru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)
- [Vytváření, odstraňování a přesouvání souborů a adresářů](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
- [Postupy: Vytvoření kopie souboru ve stejném adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Postupy: Vytvoření kopie souboru v jiném adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
