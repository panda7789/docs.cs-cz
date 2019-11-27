---
title: 'Postupy: Získání kolekce souborů z adresáře'
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: bb07ae25b413334f94456b378f0a2339402ac668
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335340"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a>Postupy: Získání kolekce souborů z adresáře v jazyce Visual Basic

Přetížení metody <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> vrátí kolekci řetězců jen pro čtení, které představují názvy souborů v adresáři:  
  
- Použijte přetížení <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> pro jednoduché hledání souborů v zadaném adresáři bez Prohledávání podadresářů.  
  
- K určení dalších možností vyhledávání použijte přetížení <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])>. K určení vzoru hledání můžete použít parametr `wildCards`. Chcete-li do hledání zahrnout podadresáře, nastavte parametr `searchType` na hodnotu <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.  
  
 Pokud se nenajde žádné soubory, které odpovídají zadanému vzoru, vrátí se prázdná kolekce.  
  
### <a name="to-list-files-in-a-directory"></a>Výpis souborů v adresáři  
  
- Použijte jedno z přetížení metody <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType>, zadejte název a cestu adresáře, ve kterém chcete vyhledat `directory` parametr. Následující příklad vrátí všechny soubory v adresáři a přidá je do `ListBox1`.  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\\\.\\) (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).  
  
- `directory` neexistuje (<xref:System.IO.DirectoryNotFoundException>).  
  
- `directory` odkazuje na existující soubor (<xref:System.IO.IOException>).  
  
- Cesta překračuje maximální povolenou délku systému (<xref:System.IO.PathTooLongException>).  
  
- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatný formát (<xref:System.NotSupportedException>).  
  
- Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
- Uživatel nemá potřebná oprávnění (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [Postupy: Hledání souborů pomocí specifického vzoru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
- [Postupy: Hledání podadresářů pomocí specifického vzoru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
