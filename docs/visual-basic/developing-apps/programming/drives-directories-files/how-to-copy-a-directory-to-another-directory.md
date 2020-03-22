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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348866"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a>Postupy: Zkopírování adresáře do jiného adresáře v jazyce Visual Basic

Pomocí <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> této metody zkopírujte adresář do jiného adresáře. Tato metoda kopíruje obsah adresáře i samotný adresář. Pokud cílový adresář neexistuje, bude vytvořen. Pokud adresář se stejným názvem existuje v `overwrite` cílovém `False`umístění a je nastaven na , bude obsah obou adresářů sloučen. Během operace můžete zadat nový název adresáře.

Při kopírování souborů v adresáři mohou být vyvolány výjimky, které jsou způsobeny určitým `overwrite` souborem, například souborem existujícím během sloučení, zatímco je nastavenna na `False`. Při vyvolání těchto výjimek jsou sloučeny do jediné `Data` výjimky, jejíž vlastnost obsahuje položky, ve kterých je klíč souboru nebo cesty k adresáři a konkrétní zpráva o výjimce je obsažena v odpovídající hodnotě.

## <a name="to-copy-a-directory-to-another-directory"></a>Kopírování adresáře do jiného adresáře

- Použijte `CopyDirectory` metodu určující názvy zdrojových a cílových adresářů. Následující příklad zkopíruje `TestDirectory1` adresář `TestDirectory2`s názvem do , přepsání existujících souborů.

    [!code-vb[VbVbcnMyFileSystem#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#16)]

    Tento příklad kódu je také k dispozici jako fragment kódu IntelliSense. Ve výběru fragmentu kódu je umístěn v **systému souborů - Zpracování jednotek, složek a souborů**. Další informace naleznete v [tématu Fragmenty kódu](/visualstudio/ide/code-snippets).

## <a name="robust-programming"></a>Robustní programování

Následující podmínky mohou způsobit výjimku:

- Nový název zadaný pro adresář obsahuje dvojtečku (:) nebo lomítko (\<xref:System.ArgumentException>nebo /) ( ).

- Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky, obsahuje pouze prázdné znaky, \\ \\\\obsahuje neplatné znaky nebo se jedná o cestu zařízení (začíná na . ) (<xref:System.ArgumentException>).

- Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).

- `destinationDirectoryName`je `Nothing` nebo prázdný<xref:System.ArgumentNullException>řetězec ( )

- Zdrojový adresář neexistuje (<xref:System.IO.DirectoryNotFoundException>).

- Zdrojový adresář je kořenový<xref:System.IO.IOException>adresář ( ).

- Kombinovaná cesta odkazuje na existující<xref:System.IO.IOException>soubor ( ).

- Zdrojová cesta a cílová<xref:System.IO.IOException>cesta jsou stejné ( ).

- `ShowUI`je nastavena na `UIOption.AllDialogs` a uživatel operaci zruší nebo jeden nebo více souborů<xref:System.OperationCanceledException>v adresáři nelze zkopírovat ( ).

- Operace je cyklická<xref:System.InvalidOperationException>( ).

- Cesta obsahuje dvojtečku (:) (<xref:System.NotSupportedException>).

- Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).

- Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).

- Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ).

- Cílový soubor existuje, ale nelze<xref:System.UnauthorizedAccessException>k němu získat přístup ( ).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [Postupy: Hledání podadresářů pomocí specifického vzoru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Postupy: Získání kolekce souborů z adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
