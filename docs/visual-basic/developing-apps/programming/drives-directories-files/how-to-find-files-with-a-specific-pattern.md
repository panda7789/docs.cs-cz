---
title: 'Postupy: Hledání souborů pomocí specifického vzoru v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: 6010aa263b734f5bf57eaa3082a794cb1019645e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498541"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a>Postupy: Hledání souborů pomocí specifického vzoru v jazyce Visual Basic
<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> Metoda vrátí kolekci řetězců, které představují názvy cest souborů jen pro čtení. Můžete použít `wildCards` parametr k určení určitému vzoru. Pokud chcete do hledání zahrnout podadresářů, nastavte `searchType` parametr `SearchOption.SearchAllSubDirectories`.  
  
 Prázdná kolekce je vrácena, pokud se nenajdou žádné soubory odpovídající zadanému vzoru.  
  
> [!NOTE]
>  Informace o vrácení seznamu souborů pomocí `DirectoryInfo` třídu `System.IO` obor názvů, naleznete v tématu <xref:System.IO.DirectoryInfo.GetFiles%2A>.  
  
### <a name="to-find-files-with-a-specified-pattern"></a>K vyhledání souborů s zadanému vzoru  
  
-   Použití `GetFiles` metody poskytnutí název a cesta k adresáři, kterou chcete vyhledat a určení vzoru. Následující příklad vrátí všechny soubory s příponou `.dll` v adresáři a přidá je do `ListBox1`.  
  
     [!code-vb[VbFileIOMisc#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-find-files-with-a-specific-pattern_1.vb)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Následující podmínky mohou způsobit výjimku:  
  
-   Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje pouze mezeru, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `directory` neexistuje (<xref:System.IO.DirectoryNotFoundException>).  
  
-   `directory` odkaz na existující soubor (<xref:System.IO.IOException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
-   Uživatel nemá potřebná oprávnění (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Postupy: Hledání podadresářů pomocí specifického vzoru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Řešení potíží: Čtení a zápis do textových souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Postupy: Získání kolekce souborů v adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
