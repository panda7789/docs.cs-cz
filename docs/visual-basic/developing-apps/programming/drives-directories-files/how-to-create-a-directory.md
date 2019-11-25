---
title: 'Postupy: Vytvoření adresáře'
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 3d838352a0a3dd69a1555dc34b8acba3afba278b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348803"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a>Postupy: Vytvoření adresáře v jazyce Visual Basic

Use the `CreateDirectory` method of the `My.Computer.FileSystem` object to create directories.  
  
 If the directory already exists, no exception is thrown.  
  
### <a name="to-create-a-directory"></a>To create a directory  
  
- Use the `CreateDirectory` method by specifying the full path of the location where the directory should be created. This example creates the directory `NewDirectory` in `C:\Documents and Settings\All Users\Documents`.  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- The directory name is malformed. For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).  
  
- The parent directory of the directory to be created is read-only (<xref:System.IO.IOException>).  
  
- The directory name is `Nothing` (<xref:System.ArgumentNullException>).  
  
- The directory name is too long (<xref:System.IO.PathTooLongException>).  
  
- The directory name is a colon ":" (<xref:System.NotSupportedException>).  
  
- The user does not have permission to create the directory (<xref:System.UnauthorizedAccessException>).  
  
- The user lacks permissions in a partial-trust situation (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [Vytváření, odstraňování a přesouvání souborů a adresářů](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
