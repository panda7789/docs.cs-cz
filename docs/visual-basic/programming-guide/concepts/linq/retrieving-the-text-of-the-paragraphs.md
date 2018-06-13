---
title: Načítání textu odstavců (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 095fa0d9-7b1b-4cbb-9c13-e2c9d8923d31
ms.openlocfilehash: f1a7bc607fb51a8dca6121ee950af0252ab4722e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647147"
---
# <a name="retrieving-the-text-of-the-paragraphs-visual-basic"></a>Načítání textu odstavců (Visual Basic)
Tento příklad vychází na předchozí příklad, [načítání odstavců a jejich styly (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md). Tento nový příklad načte text jednotlivých odstavců jako řetězec.  
  
 K získání textu, v tomto příkladu přidá další dotaz, který iteruje kolekcí anonymní typy a projekty novou kolekci anonymní typ s přidání nového člena, `Text`. Použije <xref:System.Linq.Enumerable.Aggregate%2A> operátor standardní dotazu k řetězení více řetězců do jednoho řetězce.  
  
 Tento postup (tedy první promítnutí do kolekce anonymního typu a potom pomocí této kolekce do projektu do nové kolekce anonymního typu) je běžné a užitečné stylu. Tento dotaz může byla zapsána bez na první anonymní typ projekce. Ale kvůli opožděné vyhodnocení to tak nepoužívá mnoho dalších výpočetní výkon. Stylu vytváří více krátké povahy objektů v haldě, ale to nesnižuje podstatně výkon.  
  
 Samozřejmě by bylo možné vytvořit jeden dotaz, který obsahuje funkci pro načtení odstavců, styl jednotlivých odstavců a každý odstavec. Ale často je užitečné rozdělit složitější dotaz do více dotazů, protože výsledný kód je více modulární a jednodušší správu. Kromě toho pokud potřebujete znovu použít část dotazu, aby bylo jednodušší refactor Pokud dotazy jsou zapsány tímto způsobem.  
  
 Tyto dotazy, které jsou zřetězené společně, použijte zpracování modelu, který je podrobně v tématu [kurz: odložený provádění (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad zpracuje WordprocessingML dokumentu, určení uzlu elementu, název stylu a každý odstavec. Tento příklad vychází v předchozích příkladech v tomto kurzu. Nový dotaz se nazývá v komentáře v kódu níže.  
  
 Pokyny pro vytvoření zdrojový dokument v tomto příkladu najdete v tématu [vytváření zdroj Office otevřít dokument XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 Tento příklad používá třídy z WindowsBase sestavení. Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    ' Following function is required because VB does not support short circuit evaluation  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, _  
                                         ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = _  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = _  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
                  docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = _  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    '  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        Dim defaultStyle As String = _  
            ( _  
                From style In styleDoc.Root.<w:style> _  
                Where style.@w:type = "paragraph" And _  
                      style.@w:default = "1" _  
                Select style _  
            ).First().@w:styleId  
  
        ' Find all paragraphs in the document.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        ' Following is the new query that retrieves the text of  
        ' each paragraph.  
        Dim paraWithText = _  
            From para In paragraphs _  
            Select New With { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = para.ParagraphNode.<w:r>.<w:t> _  
                    .Aggregate(New StringBuilder(), _  
                               Function(s As StringBuilder, i As String) s.Append(CStr(i)), _  
                               Function(s As StringBuilder) s.ToString) _  
            }  
  
        For Each p In paraWithText  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)  
        Next  
  
    End Sub  
End Module  
```  
  
 Tento příklad vytvoří následující výstup v případě použitého pro dokument popsané v [vytváření zdroj Office otevřít dokument XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
```  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >Imports System<  
StyleName:Code ><  
StyleName:Code >Class Program<  
StyleName:Code >    Public Shared  Sub Main(ByVal args() As String)<  
StyleName:Code >        Console.WriteLine("Hello World")<  
StyleName:Code >   End Sub<  
StyleName:Code >End Class<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
## <a name="next-steps"></a>Další kroky  
 Další příklad ukazuje, jak používat metody rozšíření, místo <xref:System.Linq.Enumerable.Aggregate%2A>, aby řetězení více řetězců do jednoho řetězce.  
  
-   [Refaktoring pomocí metody rozšíření (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a>Viz také  
 [Kurz: Manipulace se obsah v dokumentu WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
 [Odložené provedení a opožděné vyhodnocení v technologii LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
