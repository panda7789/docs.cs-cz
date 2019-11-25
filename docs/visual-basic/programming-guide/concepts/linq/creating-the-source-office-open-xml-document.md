---
title: Vytvoření zdrojového dokumentu Office Open XML
ms.date: 07/20/2015
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
ms.openlocfilehash: 5f7a9baebd2d1db73ab17924e0ff8a7408637ee8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346419"
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a>Creating the Source Office Open XML Document (Visual Basic)
This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use. If you follow these instructions, your output will match the output provided in each example.  
  
 However, the examples in this tutorial will work with any valid WordprocessingML document.  
  
 To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.  
  
## <a name="creating-the-wordprocessingml-document"></a>Creating the WordprocessingML Document  
  
#### <a name="to-create-the-wordprocessingml-document"></a>To create the WordprocessingML document  
  
1. Create a new Microsoft Word document.  
  
2. Paste the following text into the new document:  
  
    ```text  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    Imports System  
  
    Class Program  
        Public Shared  Sub Main(ByVal args() As String)  
            Console.WriteLine("Hello World")  
        End Sub  
    End Class  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3. Format the first line with the style "Heading 1".  
  
4. Select the lines that contain the Visual Basic code. The first line starts with the `Imports` keyword. The last line is "End Class". Format the lines with the courier font. Format them with a new style, and name the new style "Code".  
  
5. Finally, select the entire line that contains the output, and format it with the `Code` style.  
  
6. Save the document, and name it SampleDoc.docx.  
  
    > [!NOTE]
    > If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.  
  
## <a name="see-also"></a>Viz také:

- [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
