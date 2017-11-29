---
title: "Vytvoření zdrojového dokumentu XML otevřete Office (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c573f703ea3d7550dabd994f538e28e197874715
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a>Vytvoření zdrojového dokumentu XML otevřete Office (Visual Basic)
Toto téma ukazuje, jak vytvořit dokument XML WordprocessingML otevřete Office, používaných v předchozích příkladech v tomto kurzu. Pokud budete postupovat podle těchto pokynů, bude odpovídat výstupu výstupu, zadané v obou příkladech.  
  
 V příkladech v tomto kurzu však bude fungovat s platnou WordprocessingML dokumentu.  
  
 Vytvoření dokumentu, který tento kurz používá, musí mít Microsoft Office 2007 nebo novější nebo Microsoft Office 2003 pomocí sady Microsoft Office kompatibility Pack musí mít pro Word, Excel a PowerPoint formáty souborů 2007.  
  
## <a name="creating-the-wordprocessingml-document"></a>Vytváření WordprocessingML dokumentu  
  
#### <a name="to-create-the-wordprocessingml-document"></a>Chcete-li vytvořit WordprocessingML dokumentu  
  
1.  Vytvoříte nový textový dokument aplikace Microsoft Word.  
  
2.  Vložte následující text do nového dokumentu:  
  
    ```  
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
  
3.  Formát první řádek s styl "Nadpis 1".  
  
4.  Vyberte řádky, které obsahují kód jazyka Visual Basic. První řádek začíná `Imports` – klíčové slovo. Poslední řádek je "End Class". Formátování řádků s Kurýrní písmo. Formátovat pomocí nového stylu a pojmenujte nový styl "Kódu".  
  
5.  Nakonec vyberte celý řádek, který obsahuje výstup a naformátujte ho pomocí `Code` stylu.  
  
6.  Uložte dokument a pojmenujte ji SampleDoc.docx.  
  
    > [!NOTE]
    >  Pokud používáte aplikace Microsoft Word 2003, vyberte **dokument aplikace Word 2007** v **uložit jako typ** rozevíracího seznamu.  
  
## <a name="see-also"></a>Viz také  
 [Kurz: Manipulace se obsah v dokumentu WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
