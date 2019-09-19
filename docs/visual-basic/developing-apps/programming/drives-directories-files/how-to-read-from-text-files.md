---
title: 'Postupy: Čtení z textových souborů v Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: 26e6d8f9cc64f0f1238afaaf6aaf85d69f6c32ce
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039421"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a>Postupy: Čtení z textových souborů v Visual Basic

<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> Metoda`My.Computer.FileSystem` objektu umožňuje čtení z textového souboru. Kódování souboru lze určit, pokud obsah tohoto souboru používá nějaké kódování, například ASCII nebo UTF-8.

Při čtení ze souboru obsahujícího znaky s diakritikou budete muset určit kódování souboru.

> [!NOTE]
> Chcete-li číst soubor v jednom řádku textu, použijte <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> metodu `My.Computer.FileSystem` objektu. `OpenTextFileReader` Metoda<xref:System.IO.StreamReader> vrací objekt. Můžete použít <xref:System.IO.StreamReader.ReadLine%2A> metodu `StreamReader` objektu pro čtení souboru po jednotlivých řádcích. Můžete otestovat na konec souboru pomocí <xref:System.IO.StreamReader.EndOfStream%2A> metody `StreamReader` objektu.

## <a name="to-read-from-a-text-file"></a>Čtení z textového souboru

`ReadAllText` Použijte metodu `My.Computer.FileSystem` objektu pro čtení obsahu textového souboru do řetězce a zadejte cestu. Následující příklad načte obsah souboru test.txt do řetězce a pak jej zobrazí v okně se zprávou.

[!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]

### <a name="to-read-from-a-text-file-that-is-encoded"></a>Čtení z textového souboru s kódováním

`ReadAllText` Použijte metodu `My.Computer.FileSystem` objektu pro čtení obsahu textového souboru do řetězce a zadejte cestu a typ kódování souboru. Následující příklad načte obsah souboru test.txt s kódováním UTF32 do řetězce a pak jej zobrazí v okně se zprávou.

[!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]

## <a name="robust-programming"></a>Robustní programování

Následující podmínky mohou způsobit výjimku:

- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (<xref:System.ArgumentException>).

- Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).

- Soubor neexistuje (<xref:System.IO.FileNotFoundException>).

- Soubor je používán jiným procesem nebo dojde k vstupně-výstupní chybě (<xref:System.IO.IOException>).

- Cesta přesahuje maximální povolenou délku (<xref:System.IO.PathTooLongException>) definovanou systémem.

- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu format<xref:System.NotSupportedException>().

- K zápisu řetězce do vyrovnávací paměti (<xref:System.OutOfMemoryException>) není dostatek paměti.

- Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).

Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor Form1. vb nemusí být Visual Basic zdrojový soubor.

Před použitím dat ve své aplikaci ověřte všechny vstupy. Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [Čtení ze souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Postupy: Čtení z textových souborů s oddělovači](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Postupy: Čtení z textových souborů s pevnou šířkou](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Postupy: Čtení z textových souborů s více formáty](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Odstraňování potíží: Čtení z textových souborů a zápis do nich](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Návod: Manipulace se soubory a adresáři v Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Kódování souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
