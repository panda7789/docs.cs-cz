---
title: 'Postupy: Připojování k textovým souborům v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: 78d98dcf098966de435254926af21db76b7bccfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585733"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a>Postupy: Připojování k textovým souborům v jazyce Visual Basic
<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metodu můžete použít k připojení do textového souboru zadáním, že `append` parametr je nastaven na `True`.  
  
### <a name="to-append-to-a-text-file"></a>Pro připojení do textového souboru  
  
-   Použití `WriteAllText` metoda, cílový soubor a řetězec, který má být připojen a nastavení `append` parametru `True`.  
  
     Tento příklad zapíše řetězec `"This is a test string."` do souboru s názvem `Testfile.txt`.  
  
     [!code-vb[VbFileIOWrite#6](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-append-to-text-files_1.vb)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `File` odkazuje na cestu, která neexistuje (<xref:System.IO.FileNotFoundException> nebo <xref:System.IO.DirectoryNotFoundException>).  
  
-   Soubor je používán jiným procesem nebo dojde k chybě vstupně-výstupní operace (<xref:System.IO.IOException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 [Zápis do souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
