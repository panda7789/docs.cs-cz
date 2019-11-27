---
title: 'Postupy: Hledání souborů pomocí specifického vzoru'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: 5faaa16615f52714db3de6853786990265716501
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348761"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a>Postupy: Hledání souborů pomocí specifického vzoru v jazyce Visual Basic

Metoda <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> vrátí kolekci řetězců jen pro čtení, které představují názvy cest pro soubory. K určení konkrétního vzoru můžete použít parametr `wildCards`. Chcete-li do hledání zahrnout podadresáře, nastavte parametr `searchType` na hodnotu `SearchOption.SearchAllSubDirectories`.  
  
 Pokud se nenajde žádné soubory, které odpovídají zadanému vzoru, vrátí se prázdná kolekce.  
  
> [!NOTE]
> Informace o vrácení seznamu souborů pomocí třídy `DirectoryInfo` `System.IO` oboru názvů naleznete v tématu <xref:System.IO.DirectoryInfo.GetFiles%2A>.  
  
### <a name="to-find-files-with-a-specified-pattern"></a>Vyhledání souborů se zadaným vzorem  
  
- Použijte metodu `GetFiles`, zadejte název a cestu k adresáři, který chcete vyhledat, a určete jeho vzor. Následující příklad vrátí všechny soubory s příponou `.dll` v adresáři a přidá je do `ListBox1`.  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  

 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\\\.\\) (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).  
  
- `directory` neexistuje (<xref:System.IO.DirectoryNotFoundException>).  
  
- `directory` odkazuje na existující soubor (<xref:System.IO.IOException>).  
  
- Cesta překračuje maximální povolenou délku systému (<xref:System.IO.PathTooLongException>).  
  
- Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo má neplatný formát (<xref:System.NotSupportedException>).  
  
- Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
- Uživatel nemá potřebná oprávnění (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Postupy: Hledání podadresářů pomocí specifického vzoru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Řešení potíží: Čtení z textových souborů a zápis do nich](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Postupy: Získání kolekce souborů z adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
