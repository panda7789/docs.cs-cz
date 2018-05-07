---
title: 'Postupy: Zápis do binárních souborů v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: 59edf84c1addd287eb1d1615c46258f329b1c7e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>Postupy: Zápis do binárních souborů v jazyce Visual Basic
<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> Metoda zapisuje data do binárního souboru. Pokud `append` parametr `True`, připojí data k souboru; v opačném případě se data v souboru přepíše.  
  
 Pokud zadaná cesta není platná, <xref:System.IO.DirectoryNotFoundException> dojde k výjimce. Pokud je cesta platná, ale soubor neexistuje, vytvoří se soubor.  
  
### <a name="to-write-to-a-binary-file"></a>Zápis do binárního souboru  
  
-   Použití `WriteAllBytes` metodu cesta k souboru, název a bajtů, které mají být zapsána. Tento příklad přidáno pole data `CustomerData` do souboru s názvem `CollectedData.dat`.  
  
     [!code-vb[VbVbcnMyFileSystem#27](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-to-binary-files_1.vb)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následujících podmínek může vytvořit výjimku:  
  
-   Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky; obsahuje jenom prázdné znaky; nebo obsahuje neplatné znaky. (<xref:System.ArgumentException>).  
  
-   Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `File` odkazuje na cestu, která neexistuje (<xref:System.IO.FileNotFoundException> nebo <xref:System.IO.DirectoryNotFoundException>).  
  
-   Soubor je používán jiným procesem nebo dojde k chybě vstupně-výstupní operace (<xref:System.IO.IOException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>  
 [Postupy: Zápis textu do souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
