---
title: 'Postupy: Hledání souborů s určitým vzorem v Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: f35222d958f8b02f83c6575d940d24e359c3ae00
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914720"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a>Postupy: Hledání souborů s určitým vzorem v Visual Basic
<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> Metoda vrátí kolekci řetězců jen pro čtení, které představují názvy cest pro soubory. K určení konkrétního `wildCards` vzoru můžete použít parametr. Chcete-li do hledání zahrnout podadresáře, nastavte `searchType` parametr na. `SearchOption.SearchAllSubDirectories`  
  
 Pokud se nenajde žádné soubory, které odpovídají zadanému vzoru, vrátí se prázdná kolekce.  
  
> [!NOTE]
> Informace o vrácení seznamu souborů pomocí `DirectoryInfo` třídy `System.IO` oboru názvů naleznete v tématu <xref:System.IO.DirectoryInfo.GetFiles%2A>.  
  
### <a name="to-find-files-with-a-specified-pattern"></a>Vyhledání souborů se zadaným vzorem  
  
- `GetFiles` Použijte metodu, zadejte název a cestu k adresáři, který chcete vyhledat, a určete jeho vzor. Následující příklad vrátí všechny soubory s příponou `.dll` v adresáři a přidá je do. `ListBox1`  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná \\ \\na.\\) (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).  
  
- `directory`neexistuje (<xref:System.IO.DirectoryNotFoundException>).  
  
- `directory`odkazuje na existující soubor (<xref:System.IO.IOException>).  
  
- Cesta přesahuje maximální povolenou délku (<xref:System.IO.PathTooLongException>) definovanou systémem.  
  
- Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu format<xref:System.NotSupportedException>().  
  
- Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
- Uživatel nemá potřebná oprávnění (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Postupy: Najde podadresáře s určitým vzorem.](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Odstraňování potíží: Čtení z textových souborů a zápis do nich](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Postupy: Získání kolekce souborů v adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
