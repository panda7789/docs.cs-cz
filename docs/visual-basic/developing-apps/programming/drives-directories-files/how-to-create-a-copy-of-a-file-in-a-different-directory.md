---
title: 'Postupy: Vytvoření kopie souboru v jiném adresáři'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: e9a14e1f3743979548b92a3db653d09a470a1875
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348833"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a>Postupy: Vytvoření kopie souboru v jiném adresáři v jazyce Visual Basic

The `My.Computer.FileSystem.CopyFile` method allows you to copy files. Its parameters provide the ability to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.  
  
### <a name="to-copy-a-text-file-to-another-folder"></a>To copy a text file to another folder  
  
- Use the `CopyFile` method to copy a file, specifying a source file and the target directory. The `overwrite` parameter allows you to specify whether or not to overwrite existing files. The following code examples demonstrate how to use `CopyFile`.  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
## <a name="robust-programming"></a>Robustní programování  

 The following conditions may cause an exception to be thrown:  
  
- The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).  
  
- The system could not retrieve the absolute path (<xref:System.ArgumentException>).  
  
- The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).  
  
- The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).  
  
- The combined path points to an existing directory (<xref:System.IO.IOException>).  
  
- The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).  
  
- The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).  
  
- A file in the target folder with the same name is in use (<xref:System.IO.IOException>).  
  
- A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).  
  
- `ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).  
  
- `ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).  
  
- The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).  
  
- The user does not have required permission (<xref:System.UnauthorizedAccessException>).  
  
- The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [Postupy: Vytvoření kopie souboru ve stejném adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Postupy: Zkopírování adresáře do jiného adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [Postupy: Přejmenování souboru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
