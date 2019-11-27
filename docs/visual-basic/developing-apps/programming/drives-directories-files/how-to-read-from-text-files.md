---
title: 'Postupy: čtení z textových souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: 8af088ad269cc77bc5c83aedb86bde9af2e37a15
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334590"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a>Postupy: Čtení z textových souborů v jazyce Visual Basic

Metoda <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> objektu `My.Computer.FileSystem` umožňuje čtení z textového souboru. Kódování souboru lze určit, pokud obsah tohoto souboru používá nějaké kódování, například ASCII nebo UTF-8.

Při čtení ze souboru obsahujícího znaky s diakritikou budete muset určit kódování souboru.

> [!NOTE]
> Chcete-li číst soubor v jednom řádku textu, použijte metodu <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> objektu `My.Computer.FileSystem`. Metoda `OpenTextFileReader` vrátí objekt <xref:System.IO.StreamReader>. Můžete použít metodu <xref:System.IO.StreamReader.ReadLine%2A> objektu `StreamReader` pro čtení souboru po jednom řádku. Můžete otestovat na konec souboru pomocí metody <xref:System.IO.StreamReader.EndOfStream%2A> objektu `StreamReader`.

## <a name="to-read-from-a-text-file"></a>Čtení z textového souboru

K načtení obsahu textového souboru do řetězce použijte metodu `ReadAllText` objektu `My.Computer.FileSystem` a zadejte cestu. Následující příklad načte obsah souboru test.txt do řetězce a pak jej zobrazí v okně se zprávou.

[!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]

### <a name="to-read-from-a-text-file-that-is-encoded"></a>Čtení z textového souboru s kódováním

Pomocí metody `ReadAllText` objektu `My.Computer.FileSystem` si můžete přečíst obsah textového souboru do řetězce a zadat cestu a typ kódování souboru. Následující příklad načte obsah souboru test.txt s kódováním UTF32 do řetězce a pak jej zobrazí v okně se zprávou.

[!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]

## <a name="robust-programming"></a>Robustní programování

Následující podmínky mohou způsobit výjimku:

- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (<xref:System.ArgumentException>).

- Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).

- Soubor neexistuje (<xref:System.IO.FileNotFoundException>).

- Soubor je používán jiným procesem nebo dojde k vstupně-výstupní chybě (<xref:System.IO.IOException>).

- Cesta překračuje maximální povolenou délku systému (<xref:System.IO.PathTooLongException>).

- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatný formát (<xref:System.NotSupportedException>).

- K zápisu řetězce do vyrovnávací paměti (<xref:System.OutOfMemoryException>) není dostatek paměti.

- Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).

Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor Form1. vb nemusí být Visual Basic zdrojový soubor.

Před použitím dat ve své aplikaci ověřte všechny vstupy. Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [Čtení ze souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Postupy: Čtení z textových souborů s oddělovačem čárkou](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Postupy: Čtení z textových souborů s pevnou šířkou](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Postupy: Čtení z textových souborů ve více formátech](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Řešení potíží: Čtení z textových souborů a zápis do nich](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Návod: manipulace se soubory a adresáři v Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Kódování souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
