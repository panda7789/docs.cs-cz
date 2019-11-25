---
title: 'Postupy: Přejmenování souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: e69dad9ad7f59002ad62b7a06299ff012488e534
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334542"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a>Postupy: Přejmenování souboru v jazyce Visual Basic

Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name. This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.  
  
### <a name="to-rename-a-file"></a>To rename a file  
  
- Use the `My.Computer.FileSystem.RenameFile` method to rename a file. This example renames the file named `Test.txt` to `SecondTest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 This code example is also available as an IntelliSense code snippet. In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**. For more information, see [Code Snippets](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).  
  
- `newName` contains path information (<xref:System.ArgumentException>).  
  
- The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).  
  
- `newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).  
  
- The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).  
  
- There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).  
  
- The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).  
  
- A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).  
  
- The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).  
  
- The user does not have the required permission (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [Postupy: Přesunutí souboru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)
- [Vytváření, odstraňování a přesouvání souborů a adresářů](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
- [Postupy: Vytvoření kopie souboru ve stejném adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Postupy: Vytvoření kopie souboru v jiném adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
