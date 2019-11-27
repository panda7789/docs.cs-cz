---
title: 'Postupy: Zápis do binárních souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: 72d019f5f49868bd84d0507535e8ebc547b50e25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334434"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>Postupy: Zápis do binárních souborů v jazyce Visual Basic

Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> zapisuje data do binárního souboru. Pokud je parametr `append` `True`, připojí data do souboru. v opačném případě jsou data v souboru přepsána.

Pokud zadaná cesta s výjimkou názvu souboru není platná, bude vyvolána výjimka <xref:System.IO.DirectoryNotFoundException>. Pokud je cesta platná, ale soubor neexistuje, vytvoří se soubor.

## <a name="to-write-to-a-binary-file"></a>Zápis do binárního souboru

Použijte metodu `WriteAllBytes` a zadejte cestu k souboru a název a počet bajtů, které mají být zapsány. Tento příklad připojí datové pole `CustomerData` k souboru s názvem `CollectedData.dat`.

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a>Robustní programování

Následující podmínky mohou vytvořit výjimku:

- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce; obsahuje pouze prázdné znaky; nebo obsahuje neplatné znaky. (<xref:System.ArgumentException>).

- Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).

- `File` odkazuje na cestu, která neexistuje (<xref:System.IO.FileNotFoundException> nebo <xref:System.IO.DirectoryNotFoundException>).

- Soubor je používán jiným procesem nebo dojde k vstupně-výstupní chybě (<xref:System.IO.IOException>).

- Cesta překračuje maximální povolenou délku systému (<xref:System.IO.PathTooLongException>).

- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatný formát (<xref:System.NotSupportedException>).

- Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Postupy: Zápis textu do souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
