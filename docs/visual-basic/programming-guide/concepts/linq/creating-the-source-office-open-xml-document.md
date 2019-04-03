---
title: Vytváří se zdrojového dokumentu Office Open XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
ms.openlocfilehash: dad832aeef4d6519c272589033acc6d2fe3c2676
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838851"
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a>Vytváří se zdrojového dokumentu Office Open XML (Visual Basic)
Toto téma ukazuje, jak vytvořit dokumentu Office Open XML WordprocessingML, použít další příklady v tomto kurzu. Pokud budete postupovat podle těchto pokynů, výstup bude odpovídat výstup poskytovaný v každém příkladu.  
  
 Příklady v tomto kurzu ale bude fungovat s libovolný platný dokument WordprocessingML.  
  
 Vytvoření dokumentu, který tento kurz používá, musí mít buď Microsoft Office 2007 nebo novější, nebo musí mít Microsoft Office 2003 Microsoft Office Compatibility Pack pro Word, Excel a PowerPoint 2007 formátů.  
  
## <a name="creating-the-wordprocessingml-document"></a>Vytvoření dokumentu WordprocessingML  
  
#### <a name="to-create-the-wordprocessingml-document"></a>Vytvoření dokumentu WordprocessingML  
  
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
  
3.  Naformátuje styl "Nadpis 1" na prvním řádku.  
  
4.  Vyberte řádky, které obsahují kód jazyka Visual Basic. První řádek začíná `Imports` – klíčové slovo. Poslední řádek je "End Class". Formátování řádků s Kurýrní písma. Formát se nový styl a pojmenujte nový styl "Kód".  
  
5.  Nakonec označit celý řádek, který obsahuje výstup a naformátovat ho `Code` style.  
  
6.  Uložte dokument a pojmenujte ho SampleDoc.docx.  
  
    > [!NOTE]
    >  Pokud používáte aplikaci Microsoft Word 2003, vyberte **dokument aplikace Word 2007** v **uložit jako typ** rozevíracího seznamu.  
  
## <a name="see-also"></a>Viz také:

- [Kurz: Manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
