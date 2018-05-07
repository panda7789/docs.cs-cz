---
title: 'Postupy: Získání kolekce souborů z adresáře v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: c498928bd5fc58b8264e9098f49aabafc68c7fe6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a>Postupy: Získání kolekce souborů z adresáře v jazyce Visual Basic
Přetížení <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> metoda vrátit jen pro čtení kolekce řetězce představující názvy souborů v adresáři:  
  
-   Použití <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> přetížení pro hledání jednoduchého souboru v daném adresáři, bez hledání podadresářů.  
  
-   Použití <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> přetížení k určení dalších možností pro hledání. Můžete použít `wildCards` parametr k určení vzoru hledání. Chcete-li do vyhledávání přidat podadresáře, nastavte `searchType` parametru <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.  
  
 Prázdná kolekce je vrácena, pokud nejsou nalezeny žádné soubory odpovídající zadanému vzoru.  
  
### <a name="to-list-files-in-a-directory"></a>Pro vytvoření seznamu souborů v adresáři  
  
-   Použijte jednu z <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> přetížení metody zadávání název a cestu k adresáři pro hledání v `directory` parametr. Následující příklad vrátí všechny soubory v adresáři a přidá je do `ListBox1`.  
  
     [!code-vb[VbVbcnMyFileSystem#32](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-get-the-collection-of-files-in-a-directory_1.vb)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `directory` neexistuje (<xref:System.IO.DirectoryNotFoundException>).  
  
-   `directory` ukazuje na existující soubor (<xref:System.IO.IOException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
-   Uživatel nemá potřebná oprávnění (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>  
 [Postupy: Hledání souborů pomocí specifického vzoru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)  
 [Postupy: Hledání podadresářů pomocí specifického vzoru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
