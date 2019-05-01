---
title: 'Postupy: Hledání podadresářů pomocí specifického vzoru v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: 705fa6e40d0e6d18826966e3f10cfd31d9e7a6ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013865"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Postupy: Hledání podadresářů pomocí specifického vzoru v jazyce Visual Basic
<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> Metoda vrátí kolekci jen pro čtení řetězců, které představují názvy cest pro podadresářů v adresáři. Můžete použít `wildCards` parametr k určení určitému vzoru. Pokud chcete do hledání zahrnout obsah podadresářů, nastavte `searchType` parametr `SearchOption.SearchAllSubDirectories`.  
  
 Prázdná kolekce je vrácena, pokud nejsou nalezeny žádné adresáře odpovídající zadanému vzoru.  
  
### <a name="to-find-subdirectories-with-a-specific-pattern"></a>K hledání podadresářů pomocí specifického vzoru  
  
- Použití `GetDirectories` metody poskytnutí název a cesta k adresáři, kterou chcete vyhledat. Následující příklad vrátí všechny adresáře do struktury adresářů, které obsahují slovo "Protokoly" v názvu a přidá je do `ListBox1`.  
  
     [!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje pouze mezeru, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
- Jeden nebo více zadaným zástupných znaků je `Nothing`, prázdný řetězec, nebo obsahuje pouze mezery (<xref:System.ArgumentNullException>).  
  
- `directory` neexistuje (<xref:System.IO.DirectoryNotFoundException>).  
  
- `directory` odkaz na existující soubor (<xref:System.IO.IOException>).  
  
- Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
- Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
- Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
- Uživatel nemá potřebná oprávnění (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [Postupy: Hledání souborů pomocí specifického vzoru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
