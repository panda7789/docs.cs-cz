---
title: 'Postupy: Hledání souborů pomocí specifického vzoru'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: 5faaa16615f52714db3de6853786990265716501
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348761"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a>Postupy: Hledání souborů pomocí specifického vzoru v jazyce Visual Basic

Metoda <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> vrátí kolekci řetězců jen pro čtení představující názvy cest pro soubory. `wildCards` Parametr můžete použít k určení určitého vzoru. Pokud chcete do hledání zahrnout podadresáře, `searchType` nastavte `SearchOption.SearchAllSubDirectories`parametr na .  
  
 Prázdná kolekce je vrácena, pokud jsou nalezeny žádné soubory odpovídající zadanému vzoru.  
  
> [!NOTE]
> Informace o vrácení seznamu souborů pomocí `DirectoryInfo` třídy `System.IO` oboru názvů <xref:System.IO.DirectoryInfo.GetFiles%2A>naleznete v tématu .  
  
### <a name="to-find-files-with-a-specified-pattern"></a>Hledání souborů se zadaným vzorkem  
  
- Použijte `GetFiles` metodu, která zadá název a cestu adresáře, který chcete prohledat, a zadejte vzorek. Následující příklad vrátí všechny soubory `.dll` s příponou `ListBox1`v adresáři a přidá je do aplikace .  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  

 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky, obsahuje pouze prázdné znaky, \\ \\\\obsahuje neplatné znaky nebo se jedná o cestu zařízení (začíná na . ) (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).  
  
- `directory`neexistuje (<xref:System.IO.DirectoryNotFoundException>).  
  
- `directory`odkazuje na existující<xref:System.IO.IOException>soubor ( ).  
  
- Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).  
  
- Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
- Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ).  
  
- Uživatel nemá potřebná<xref:System.UnauthorizedAccessException>oprávnění ( ).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Postupy: Hledání podadresářů pomocí specifického vzoru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Řešení potíží: Čtení z textových souborů a zápis do nich](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Postupy: Získání kolekce souborů z adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
