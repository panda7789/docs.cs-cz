---
title: 'Postupy: Získání kolekce souborů z adresáře'
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: 055151d4b3e3aba6be9b9b03ac9abffc6eb7b734
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401612"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a>Postupy: Získání kolekce souborů z adresáře v jazyce Visual Basic

Přetížení <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> metody vrátí kolekci řetězců jen pro čtení, které představují názvy souborů v adresáři:  
  
- Použijte <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> přetížení pro jednoduché hledání souborů v zadaném adresáři bez Prohledávání podadresářů.  
  
- Použijte <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> přetížení k určení dalších možností vyhledávání. Pomocí `wildCards` parametru můžete zadat vzor hledání. Chcete-li do hledání zahrnout podadresáře, nastavte `searchType` parametr na <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType> .  
  
 Pokud se nenajde žádné soubory, které odpovídají zadanému vzoru, vrátí se prázdná kolekce.  
  
### <a name="to-list-files-in-a-directory"></a>Výpis souborů v adresáři  
  
- Použijte jedno z <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> přetížení metod, zadejte název a cestu k adresáři, který chcete vyhledat v `directory` parametru. Následující příklad vrátí všechny soubory v adresáři a přidá je do `ListBox1` .  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- `directory`neexistuje ( <xref:System.IO.DirectoryNotFoundException> ).  
  
- `directory`odkazuje na existující soubor ( <xref:System.IO.IOException> ).  
  
- Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .  
  
- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).  
  
- Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ).  
  
- Uživatel nemá potřebná oprávnění ( <xref:System.UnauthorizedAccessException> ).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [Postupy: Hledání souborů pomocí specifického vzoru](how-to-find-files-with-a-specific-pattern.md)
- [Postupy: Hledání podadresářů pomocí specifického vzoru](how-to-find-subdirectories-with-a-specific-pattern.md)
