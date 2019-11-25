---
title: 'Postupy: Čtení z binárních souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: c33bc72a5c79901e3715ed6a587ffdb8e3565e48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335298"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a>Postupy: Čtení z binárních souborů v jazyce Visual Basic

The `My.Computer.FileSystem` object provides the `ReadAllBytes` method for reading from binary files.  
  
### <a name="to-read-from-a-binary-file"></a>To read from a binary file  
  
- Use the `ReadAllBytes` method, which returns the contents of a file as a byte array. This example reads from the file `C:/Documents and Settings/selfportrait.jpg`.  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
- For large binary files, you can use the <xref:System.IO.FileStream.Read%2A> method of the <xref:System.IO.FileStream> object to read from the file only a specified amount at a time. You can then limit how much of the file is loaded into memory for each read operation. The following code example copies a file and allows the caller to specify how much of the file is read into memory per read operation.  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a>Robustní programování  

 The following conditions may cause an exception to be thrown:  
  
- The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).  
  
- The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).  
  
- The file does not exist (<xref:System.IO.FileNotFoundException>).  
  
- The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).  
  
- The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).  
  
- A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).  
  
- There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).  
  
- The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).  
  
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. For example, the file Form1.vb may not be a Visual Basic source file.  
  
 Před použitím dat ve své aplikaci ověřte všechny vstupy. Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Čtení ze souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Postupy: Čtení z textových souborů ve více formátech](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Ukládání dat do schránky a čtení ze schránky](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
