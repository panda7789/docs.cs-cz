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
ms.openlocfilehash: 0d99209ed123686355e8d49c82ba23f94084f895
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411613"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a>Postupy: Čtení z textových souborů v jazyce Visual Basic

<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A>Metoda `My.Computer.FileSystem` objektu umožňuje čtení z textového souboru. Kódování souboru lze určit, pokud obsah tohoto souboru používá nějaké kódování, například ASCII nebo UTF-8.

Při čtení ze souboru obsahujícího znaky s diakritikou budete muset určit kódování souboru.

> [!NOTE]
> Chcete-li číst soubor v jednom řádku textu, použijte <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> metodu `My.Computer.FileSystem` objektu. Metoda `OpenTextFileReader` vrátí objekt <xref:System.IO.StreamReader>. Můžete použít <xref:System.IO.StreamReader.ReadLine%2A> metodu `StreamReader` objektu pro čtení souboru po jednotlivých řádcích. Můžete otestovat na konec souboru pomocí <xref:System.IO.StreamReader.EndOfStream%2A> metody `StreamReader` objektu.

## <a name="to-read-from-a-text-file"></a>Čtení z textového souboru

Použijte `ReadAllText` metodu `My.Computer.FileSystem` objektu pro čtení obsahu textového souboru do řetězce a zadejte cestu. Následující příklad načte obsah souboru test.txt do řetězce a pak jej zobrazí v okně se zprávou.

[!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]

### <a name="to-read-from-a-text-file-that-is-encoded"></a>Čtení z textového souboru s kódováním

Použijte `ReadAllText` metodu `My.Computer.FileSystem` objektu pro čtení obsahu textového souboru do řetězce a zadejte cestu a typ kódování souboru. Následující příklad načte obsah souboru test.txt s kódováním UTF32 do řetězce a pak jej zobrazí v okně se zprávou.

[!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]

## <a name="robust-programming"></a>Robustní programování

Následující podmínky mohou způsobit výjimku:

- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení ( <xref:System.ArgumentException> ).

- Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).

- Soubor neexistuje ( <xref:System.IO.FileNotFoundException> ).

- Soubor je používán jiným procesem nebo dojde k vstupně-výstupní chybě ( <xref:System.IO.IOException> ).

- Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .

- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).

- K zápisu řetězce do vyrovnávací paměti () není dostatek paměti <xref:System.OutOfMemoryException> .

- Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ).

Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor Form1. vb nemusí být Visual Basic zdrojový soubor.

Před použitím dat ve své aplikaci ověřte všechny vstupy. Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [Čtení ze souborů](reading-from-files.md)
- [Postupy: Čtení z textových souborů s oddělovačem čárkou](how-to-read-from-comma-delimited-text-files.md)
- [Postupy: Čtení z textových souborů s pevnou šířkou](how-to-read-from-fixed-width-text-files.md)
- [Postupy: Čtení z textových souborů ve více formátech](how-to-read-from-text-files-with-multiple-formats.md)
- [Řešení potíží: Čtení z textových souborů a zápis do nich](troubleshooting-reading-from-and-writing-to-text-files.md)
- [Návod: Práce se soubory a adresáři v jazyce Visual Basic](walkthrough-manipulating-files-and-directories.md)
- [Kódování souborů](file-encodings.md)
