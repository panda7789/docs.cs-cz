---
title: 'Postupy: Zápis do binárních souborů v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: 9e83029b7b5fd635ff08e608760b6c64c7945da0
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965927"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>Postupy: Zápis do binárních souborů v jazyce Visual Basic
<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> Metoda zapisuje data do binárního souboru. Pokud `append` parametr `True`, připojí data k souboru; jinak se přepíše data v souboru.  
  
 Pokud zadaná cesta není platná, <xref:System.IO.DirectoryNotFoundException> , bude vyvolána výjimka. Pokud je cesta platná, ale soubor neexistuje, vytvoří se soubor.  
  
### <a name="to-write-to-a-binary-file"></a>Zápis do binárního souboru  
  
-   Použití `WriteAllBytes` metodu cesta k souboru a název a bajtů, které mají být zapsána. Tento příklad připojí data pole `CustomerData` do souboru s názvem `CollectedData.dat`.  
  
     [!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky; obsahuje pouze prázdné znaky; nebo obsahuje neplatné znaky. (<xref:System.ArgumentException>).  
  
-   Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `File` odkazuje na cestu, která neexistuje (<xref:System.IO.FileNotFoundException> nebo <xref:System.IO.DirectoryNotFoundException>).  
  
-   Soubor je používán jiným procesem nebo dojde k chybě vstupně-výstupních operací (<xref:System.IO.IOException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Postupy: Zápis textu do souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
