---
title: 'Postupy: Zápis textu do souborů v adresáři MyDocuments'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: bc62f2bc63a2ea185b8ea4c8d271dd28d347d6f0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334524"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a>Postupy: Zápis textu do souborů v adresáři MyDocuments v jazyce Visual Basic

The `My.Computer.FileSystem.SpecialDirectories` object allows you to access special directories, such as the **MyDocuments** directory.  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>To write new text files in the My Documents directory  
  
1. Use the `My.Computer.FileSystem.SpecialDirectories.MyDocuments` property to supply the path.  
  
     [!code-vb[VbFileIOWrite#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#1)]  
  
2. Use the `WriteAllText` method to write text to the specified file.  
  
     [!code-vb[VbVbcnMyFileSystem#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#14)]  
  
## <a name="example"></a>Příklad  

 [!code-vb[VbFileIOWrite#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  

 Replace `test.txt` with the name of the file you want to write to.  
  
## <a name="robust-programming"></a>Robustní programování  

 This code rethrows all the exceptions that may occur when writing text to the file. You can reduce the likelihood of exceptions by using Windows Forms controls such as the [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) and the [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) components that limit the user choices to valid file names. Using these controls is not foolproof, however. The file system can change between the time the user selects a file and the time that the code executes. Exception handling is therefore nearly always necessary when with working with files.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  

 If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges. For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).  
  
 This example creates a new file. If an application needs to create a file, that application needs Create permission for the folder. Permissions are set using access control lists. If the file already exists, the application needs only Write permission, a lesser privilege. Where possible, it is more secure to create the file during deployment, and only grant Read privileges to a single file, rather than to grant Create privileges for a folder. Also, it is more secure to write data to user folders than to the root folder or the **Program Files** folder. For more information, see [ACL Technology Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
