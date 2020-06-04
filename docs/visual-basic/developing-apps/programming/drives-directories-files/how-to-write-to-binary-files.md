---
title: 'Postupy: Zápis do binárních souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: b36da82060b930101cb54dd852d050ac0155bd10
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411548"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>Postupy: Zápis do binárních souborů v jazyce Visual Basic

<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>Metoda zapisuje data do binárního souboru. Pokud `append` je parametr `True` , připojí data do souboru; v opačném případě se data v souboru přepíše.

Pokud zadaná cesta s výjimkou názvu souboru není platná, <xref:System.IO.DirectoryNotFoundException> bude vyvolána výjimka. Pokud je cesta platná, ale soubor neexistuje, vytvoří se soubor.

## <a name="to-write-to-a-binary-file"></a>Zápis do binárního souboru

Použijte `WriteAllBytes` metodu a zadejte cestu k souboru a název a bajty, které mají být zapsány. Tento příklad připojí datové pole `CustomerData` k souboru s názvem `CollectedData.dat` .

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a>Robustní programování

Následující podmínky mohou vytvořit výjimku:

- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce; obsahuje pouze prázdné znaky; nebo obsahuje neplatné znaky. (<xref:System.ArgumentException>).

- Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).

- `File`odkazuje na cestu, která neexistuje ( <xref:System.IO.FileNotFoundException> nebo <xref:System.IO.DirectoryNotFoundException> ).

- Soubor je používán jiným procesem nebo dojde k vstupně-výstupní chybě ( <xref:System.IO.IOException> ).

- Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .

- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).

- Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Postupy: Zápis textu do souborů](how-to-write-text-to-files.md)
