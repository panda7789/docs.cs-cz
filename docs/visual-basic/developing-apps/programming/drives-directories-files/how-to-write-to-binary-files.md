---
title: 'Postupy: Zápis do binárních souborů v Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: ab42fa50aaf39397ac51db8a4cc3a3b00f6ce878
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039420"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>Postupy: Zápis do binárních souborů v Visual Basic

<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> Metoda zapisuje data do binárního souboru. Pokud je `append` `True`parametr, připojí data do souboru; v opačném případě se data v souboru přepíše.

Pokud zadaná cesta s výjimkou názvu souboru není platná, <xref:System.IO.DirectoryNotFoundException> bude vyvolána výjimka. Pokud je cesta platná, ale soubor neexistuje, vytvoří se soubor.

## <a name="to-write-to-a-binary-file"></a>Zápis do binárního souboru

`WriteAllBytes` Použijte metodu a zadejte cestu k souboru a název a bajty, které mají být zapsány. Tento příklad připojí datové pole `CustomerData` k souboru s názvem. `CollectedData.dat`

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a>Robustní programování

Následující podmínky mohou vytvořit výjimku:

- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce; obsahuje pouze prázdné znaky; nebo obsahuje neplatné znaky. (<xref:System.ArgumentException>).

- Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).

- `File`odkazuje na cestu, která neexistuje (<xref:System.IO.FileNotFoundException> nebo <xref:System.IO.DirectoryNotFoundException>).

- Soubor je používán jiným procesem nebo dojde k vstupně-výstupní chybě (<xref:System.IO.IOException>).

- Cesta přesahuje maximální povolenou délku (<xref:System.IO.PathTooLongException>) definovanou systémem.

- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu format<xref:System.NotSupportedException>().

- Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Postupy: Zápis textu do souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
