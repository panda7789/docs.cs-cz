---
title: 'Postupy: Zkopírování adresáře do jiného adresáře v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: 9b6e095d061619cf9d2e2d87a7247cbdbc51cbe2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588581"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a>Postupy: Zkopírování adresáře do jiného adresáře v jazyce Visual Basic
Použití <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> metodu pro zkopírování adresáře do jiného adresáře. Tato metoda zkopíruje obsah adresáře, jakož i daný adresář. Pokud cílový adresář neexistuje, bude vytvořen. Pokud adresář se stejným názvem existuje v cílovém umístění a `overwrite` je nastaven na `False`, se sloučí obsah dva adresáře. Během operace můžete zadat nový název pro adresář.  
  
 Při kopírování souborů v adresáři, můžou být vyvolány výjimky vzniklé v konkrétním souborem, jako je například existující soubor během sloučení při `overwrite` je nastaven na `False`. Pokud je vyvolána, jsou spojeny do jednoho výjimky, jejichž `Data` vlastnost obsahuje položky, které cestu soubor nebo adresář je klíč a zprávu výjimky s odpovídající hodnotou.  
  
### <a name="to-copy-a-directory-to-another-directory"></a>Pro zkopírování adresáře do jiného adresáře  
  
-   Použití `CopyDirectory` metoda, zadání zdrojové a cílové názvy adresářů. Následující příklad zkopíruje adresář s názvem `TestDirectory1` do `TestDirectory2`, přepíše existující soubory.  
  
     [!code-vb[VbVbcnMyFileSystem#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-a-directory-to-another-directory_1.vb)]  
  
     Tento příklad kódu je také k dispozici jako IntelliSense fragment kódu. V Sběrač fragmentů kódu je umístěn v **systému - zpracování jednotek, složek a souborů souborů**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Nový název adresáře obsahuje dvojtečku (:) nebo lomítko (\ nebo /) (<xref:System.ArgumentException>).  
  
-   Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `destinationDirectoryName` je `Nothing` nebo prázdný řetězec (<xref:System.ArgumentNullException>)  
  
-   Zadaný zdrojový adresář neexistuje (<xref:System.IO.DirectoryNotFoundException>).  
  
-   Zadaný zdrojový adresář je kořenový adresář (<xref:System.IO.IOException>).  
  
-   Kombinované cesta odkazuje na existující soubor (<xref:System.IO.IOException>).  
  
-   Zdrojová cesta a cílová cesta jsou stejné (<xref:System.IO.IOException>).  
  
-   `ShowUI` je nastavena na `UIOption.AllDialogs` a uživatel zrušil operaci, nebo nelze zkopírovat jeden nebo více souborů v adresáři (<xref:System.OperationCanceledException>).  
  
-   Operace je cyklická (<xref:System.InvalidOperationException>).  
  
-   Cesta obsahuje dvojtečku (:) (<xref:System.NotSupportedException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
-   Cílový soubor existuje, ale není přístupná (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>  
 [Postupy: Hledání podadresářů pomocí specifického vzoru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)  
 [Postupy: Získání kolekce souborů z adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
