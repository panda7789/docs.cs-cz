---
title: 'Postupy: Čtení z textových souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: 8af088ad269cc77bc5c83aedb86bde9af2e37a15
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334590"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a>Postupy: Čtení z textových souborů v jazyce Visual Basic

Metoda <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> objektu `My.Computer.FileSystem` umožňuje číst z textového souboru. Kódování souboru lze určit, pokud obsah tohoto souboru používá nějaké kódování, například ASCII nebo UTF-8.

Při čtení ze souboru obsahujícího znaky s diakritikou budete muset určit kódování souboru.

> [!NOTE]
> Chcete-li soubor číst po jednom řádku textu <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> současně, `My.Computer.FileSystem` použijte metodu objektu. Metoda `OpenTextFileReader` vrátí objekt <xref:System.IO.StreamReader>. Metodu <xref:System.IO.StreamReader.ReadLine%2A> objektu `StreamReader` můžete použít ke čtení souboru po jednom řádku. Konec souboru můžete otestovat pomocí <xref:System.IO.StreamReader.EndOfStream%2A> metody `StreamReader` objektu.

## <a name="to-read-from-a-text-file"></a>Čtení z textového souboru

Pomocí `ReadAllText` metody objektu `My.Computer.FileSystem` můžete číst obsah textového souboru do řetězce a dodávat cestu. Následující příklad načte obsah souboru test.txt do řetězce a pak jej zobrazí v okně se zprávou.

[!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]

### <a name="to-read-from-a-text-file-that-is-encoded"></a>Čtení z textového souboru s kódováním

Pomocí `ReadAllText` metody objektu `My.Computer.FileSystem` můžete číst obsah textového souboru do řetězce a zadat tak typ kódování cesty a souboru. Následující příklad načte obsah souboru test.txt s kódováním UTF32 do řetězce a pak jej zobrazí v okně se zprávou.

[!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]

## <a name="robust-programming"></a>Robustní programování

Následující podmínky mohou způsobit výjimku:

- Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky, obsahuje pouze prázdné<xref:System.ArgumentException>znaky, obsahuje neplatné znaky nebo se jedná o cestu zařízení ( ).

- Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).

- Soubor neexistuje (<xref:System.IO.FileNotFoundException>).

- Soubor je používán jiným procesem nebo dojde k<xref:System.IO.IOException>chybě vstupně-out ( ).

- Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).

- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).

- Není dostatek paměti pro zápis řetězce<xref:System.OutOfMemoryException>do vyrovnávací paměti ( ).

- Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ).

Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.

Před použitím dat ve své aplikaci ověřte všechny vstupy. Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [Čtení ze souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Postupy: Čtení z textových souborů s oddělovači](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Postupy: Čtení z textových souborů s pevnou šířkou](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Postupy: Čtení z textových souborů ve více formátech](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Řešení potíží: Čtení z textových souborů a zápis do nich](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Návod: Práce se soubory a adresáři v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Kódování souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
