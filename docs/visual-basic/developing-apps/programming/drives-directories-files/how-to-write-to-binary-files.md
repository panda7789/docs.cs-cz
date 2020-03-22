---
title: 'Postupy: Zápis do binárních souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: 72d019f5f49868bd84d0507535e8ebc547b50e25
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334434"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>Postupy: Zápis do binárních souborů v jazyce Visual Basic

Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> zapisuje data do binárního souboru. Pokud `append` je `True`parametr , připojí data k souboru; v opačném případě jsou data v souboru přepsána.

Pokud zadaná cesta bez názvu souboru <xref:System.IO.DirectoryNotFoundException> není platná, bude vyvolána výjimka. Pokud je cesta platná, ale soubor neexistuje, soubor bude vytvořen.

## <a name="to-write-to-a-binary-file"></a>Zápis do binárního souboru

Použijte `WriteAllBytes` metodu, která poskytuje cestu k souboru a název a bajty, které mají být zapsány. Tento příklad připojí datové `CustomerData` pole k `CollectedData.dat`souboru s názvem .

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a>Robustní programování

Následující podmínky mohou vytvořit výjimku:

- Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky; obsahuje pouze prázdné místo; nebo obsahuje neplatné znaky. (<xref:System.ArgumentException>).

- Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).

- `File`odkazuje na cestu, která<xref:System.IO.FileNotFoundException> neexistuje <xref:System.IO.DirectoryNotFoundException>( nebo ).

- Soubor je používán jiným procesem nebo dojde k chybě<xref:System.IO.IOException>vstupně-out ( ).

- Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).

- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).

- Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Postupy: Zápis textu do souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
