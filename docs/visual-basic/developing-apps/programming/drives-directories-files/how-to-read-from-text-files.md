---
title: 'How to: Read From Text Files'
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

The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> method of the `My.Computer.FileSystem` object allows you to read from a text file. Kódování souboru lze určit, pokud obsah tohoto souboru používá nějaké kódování, například ASCII nebo UTF-8.

Při čtení ze souboru obsahujícího znaky s diakritikou budete muset určit kódování souboru.

> [!NOTE]
> To read a file a single line of text at a time, use the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> method of the `My.Computer.FileSystem` object. The `OpenTextFileReader` method returns a <xref:System.IO.StreamReader> object. You can use the <xref:System.IO.StreamReader.ReadLine%2A> method of the `StreamReader` object to read a file one line at a time. You can test for the end of the file using the <xref:System.IO.StreamReader.EndOfStream%2A> method of the `StreamReader` object.

## <a name="to-read-from-a-text-file"></a>Čtení z textového souboru

Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path. Následující příklad načte obsah souboru test.txt do řetězce a pak jej zobrazí v okně se zprávou.

[!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]

### <a name="to-read-from-a-text-file-that-is-encoded"></a>Čtení z textového souboru s kódováním

Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path and file encoding type. Následující příklad načte obsah souboru test.txt s kódováním UTF32 do řetězce a pak jej zobrazí v okně se zprávou.

[!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]

## <a name="robust-programming"></a>Robustní programování

Následující podmínky mohou způsobit výjimku:

- The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).

- The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).

- The file does not exist (<xref:System.IO.FileNotFoundException>).

- The file is in use by another process or an I/O error occurs (<xref:System.IO.IOException>).

- The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).

- A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).

- There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).

- The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).

Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. For example, the file Form1.vb may not be a Visual Basic source file.

Před použitím dat ve své aplikaci ověřte všechny vstupy. Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [Čtení ze souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Postupy: Čtení z textových souborů s oddělovačem čárkou](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Postupy: Čtení z textových souborů s pevnou šířkou](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Postupy: Čtení z textových souborů ve více formátech](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Řešení potíží: Čtení z textových souborů a zápis do nich](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Walkthrough: Manipulating Files and Directories in Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Kódování souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
