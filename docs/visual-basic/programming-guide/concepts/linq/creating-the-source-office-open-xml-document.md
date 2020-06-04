---
title: Vytvoření zdrojového dokumentu Office Open XML
ms.date: 07/20/2015
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
ms.openlocfilehash: 9f44c8d0f4080224c461736fdbdf3acd854e4a89
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410835"
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a>Vytvoření zdrojového dokumentu XML pro Office Open Source (Visual Basic)
V tomto tématu se dozvíte, jak vytvořit dokument Office Open XML WordprocessingML, který se používá v dalších příkladech tohoto kurzu. Pokud budete postupovat podle těchto pokynů, váš výstup bude odpovídat výstupu uvedenému v každém příkladu.  
  
 Příklady v tomto kurzu ale budou fungovat s jakýmkoli platným dokumentem WordprocessingML.  
  
 Pokud chcete vytvořit dokument, který používá tento kurz, musíte mít nainstalovanou systém Microsoft Office 2007 nebo novější, nebo musíte mít systém Microsoft Office 2003 pomocí sady systém Microsoft Office Compatibility Pack pro Word, Excel a PowerPoint 2007 formats.  
  
## <a name="creating-the-wordprocessingml-document"></a>Vytvoření dokumentu WordprocessingML  
  
#### <a name="to-create-the-wordprocessingml-document"></a>Vytvoření dokumentu WordprocessingML  
  
1. Vytvoří nový dokument aplikace Microsoft Word.  
  
2. Vložte do nového dokumentu následující text:  
  
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
  
3. Naformátuje první řádek stylem "Nadpis 1".  
  
4. Vyberte řádky, které obsahují kód Visual Basic. První řádek začíná `Imports` klíčovým slovem. Poslední řádek je "End Class". Naformátujte čáry pomocí písma Courier. Naformátujte je pomocí nového stylu a pojmenujte nový styl "Code".  
  
5. Nakonec vyberte celý řádek obsahující výstup a naformátujte ho pomocí `Code` stylu.  
  
6. Uložte dokument a pojmenujte ho SampleDoc. docx.  
  
    > [!NOTE]
    > Pokud používáte Microsoft Word 2003, vyberte v rozevíracím seznamu **Uložit jako typ** možnost **dokument Word 2007** .  
  
## <a name="see-also"></a>Viz také

- [Kurz: manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
