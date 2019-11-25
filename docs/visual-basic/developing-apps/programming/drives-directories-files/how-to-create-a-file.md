---
title: 'Postupy: Vytvoření souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: 20533ec01d3198d499312ed0c15ec8cca2ff70bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348798"
---
# <a name="how-to-create-a-file-in-visual-basic"></a>Postupy: Vytvoření souboru v jazyce Visual Basic

This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.  
  
## <a name="example"></a>Příklad  

 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  

 Use the `file` variable to write to the file.  
  
## <a name="robust-programming"></a>Robustní programování  

 If the file already exists, it is replaced.  
  
 Následující podmínky mohou způsobit výjimku:  
  
- The path name is malformed. For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).  
  
- The path is read-only (<xref:System.IO.IOException>).  
  
- The path name is `Nothing` (<xref:System.ArgumentNullException>).  
  
- The path name is too long (<xref:System.IO.PathTooLongException>).  
  
- The path is invalid (<xref:System.IO.DirectoryNotFoundException>).  
  
- The path is only a colon ":" (<xref:System.NotSupportedException>).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  

 A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.  
  
 The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.  
  
 An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [Using Libraries from Partially Trusted Code](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md)
