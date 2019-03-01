---
title: 'Postupy: Zkopírování adresáře do jiného adresáře v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: 873defb025ff02e6af2572d8d2587f86e5228ca0
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968787"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a>Postupy: Zkopírování adresáře do jiného adresáře v jazyce Visual Basic
Použití <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> metodu pro zkopírování adresáře do jiného adresáře. Tato metoda zkopíruje obsah do adresáře, stejně jako adresář samotný. Pokud cílový adresář neexistuje, vytvoří se. Pokud v cílovém umístění existuje adresář se stejným názvem a `overwrite` je nastavena na `False`, sloučí obsah dva adresáře. Při operaci můžete zadat nový název pro adresář.  
  
 Při kopírování souborů v adresáři, můžou být vyvolány výjimky, které jsou způsobeny podle určitého souboru, jako je například existující soubor během sloučení při `overwrite` je nastavena na `False`. Pokud takové výjimky jsou vyvolány, jsou spojeny do jednoho výjimek, jejichž `Data` vlastnost obsahuje položky, které cestu souboru nebo adresáře je klíč a zprávu výjimky odpovídající hodnotu.  
  
### <a name="to-copy-a-directory-to-another-directory"></a>Pro zkopírování adresáře do jiného adresáře  
  
-   Použití `CopyDirectory` metoda zadání zdrojové a cílové názvy adresářů. V následujícím příkladu se zkopíruje adresář s názvem `TestDirectory1` do `TestDirectory2`, že přepíšete existující soubory.  
  
     [!code-vb[VbVbcnMyFileSystem#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#16)]  
  
     Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense. V dialogu pro výběr fragmentu kódu je umístěn v **souborový systém – zpracování jednotek, složek a souborů**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Nový název adresáře obsahuje dvojtečku (:) nebo lomítka (\ nebo /) (<xref:System.ArgumentException>).  
  
-   Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje pouze mezeru, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `destinationDirectoryName` je `Nothing` nebo prázdný řetězec (<xref:System.ArgumentNullException>)  
  
-   Zdrojový adresář neexistuje (<xref:System.IO.DirectoryNotFoundException>).  
  
-   Zdrojový adresář je kořenový adresář (<xref:System.IO.IOException>).  
  
-   Kombinované cesta odkazuje na existující soubor (<xref:System.IO.IOException>).  
  
-   Cesta ke zdroji a cílová cesta jsou stejné (<xref:System.IO.IOException>).  
  
-   `ShowUI` je nastavena na `UIOption.AllDialogs` a uživatel operaci zruší nebo nelze zkopírovat jeden nebo více souborů v adresáři (<xref:System.OperationCanceledException>).  
  
-   Operace je cyklická (<xref:System.InvalidOperationException>).  
  
-   Cesta obsahuje dvojtečku (:) (<xref:System.NotSupportedException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
-   Cílový soubor existuje, ale není přístupná (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [Postupy: Hledání podadresářů pomocí specifického vzoru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Postupy: Získání kolekce souborů v adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
