---
title: 'Postupy: Zkopírování adresáře do jiného adresáře'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: a23079f093f53ab8e20eb71c684a594dcf7f894b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348866"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a>Postupy: Zkopírování adresáře do jiného adresáře v jazyce Visual Basic

K zkopírování adresáře do jiného adresáře použijte metodu <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>. Tato metoda zkopíruje obsah adresáře a také samotný adresář. Pokud cílový adresář neexistuje, vytvoří se. Pokud v cílovém umístění existuje adresář se stejným názvem a `overwrite` je nastavená na `False`, obsah obou adresářů se sloučí. Během operace můžete zadat nový název adresáře.

Při kopírování souborů v adresáři mohou být vyvolány výjimky, které jsou způsobeny konkrétním souborem, jako je například soubor existující během sloučení, zatímco `overwrite` je nastavena na hodnotu `False`. Pokud jsou tyto výjimky vyvolány, jsou konsolidovány do jediné výjimky, jejíž `Data` vlastnost obsahuje položky, ve kterých je soubor nebo cesta adresáře klíč, a specifická zpráva výjimky je obsažena v odpovídající hodnotě.

## <a name="to-copy-a-directory-to-another-directory"></a>Zkopírování adresáře do jiného adresáře

- Použijte metodu `CopyDirectory` a zadejte názvy zdrojového a cílového adresáře. Následující příklad zkopíruje adresář s názvem `TestDirectory1` do `TestDirectory2`a přepíše stávající soubory.

    [!code-vb[VbVbcnMyFileSystem#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#16)]

    Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu se nachází v **systému souborů – zpracování jednotek, složek a souborů**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).

## <a name="robust-programming"></a>Robustní programování

Následující podmínky mohou způsobit výjimku:

- Nový název zadaný pro adresář obsahuje dvojtečku (:) nebo lomítko (\ nebo/) (<xref:System.ArgumentException>).

- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\\\.\\) (<xref:System.ArgumentException>).

- Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).

- `destinationDirectoryName` je `Nothing` nebo prázdný řetězec (<xref:System.ArgumentNullException>).

- Zdrojový adresář neexistuje (<xref:System.IO.DirectoryNotFoundException>).

- Zdrojový adresář je kořenový adresář (<xref:System.IO.IOException>).

- Kombinovaná cesta odkazuje na existující soubor (<xref:System.IO.IOException>).

- Cesta ke zdroji a cílová cesta jsou stejné (<xref:System.IO.IOException>).

- `ShowUI` je nastavená na `UIOption.AllDialogs` a uživatel operaci zruší nebo jeden nebo více souborů v adresáři nelze zkopírovat (<xref:System.OperationCanceledException>).

- Operace je cyklická (<xref:System.InvalidOperationException>).

- Cesta obsahuje dvojtečku (:) (<xref:System.NotSupportedException>).

- Cesta překračuje maximální povolenou délku systému (<xref:System.IO.PathTooLongException>).

- Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo má neplatný formát (<xref:System.NotSupportedException>).

- Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).

- Cílový soubor existuje, ale nelze k němu přistupovat (<xref:System.UnauthorizedAccessException>).

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [Postupy: Hledání podadresářů pomocí specifického vzoru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Postupy: Získání kolekce souborů z adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
