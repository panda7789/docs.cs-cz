---
title: Načítání odstavců a jejich styly (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: 5b8075b5aa05c32d2dc894149a8fa53f103138c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a>Načítání odstavců a jejich styly (Visual Basic)
V tomto příkladu jsme vytvořit dotaz, který načte odstavce uzly z WordprocessingML dokumentu. Také identifikuje styl jednotlivých odstavců.  
  
 Tento dotaz založený na dotaz v předchozím příkladu [hledání výchozí styl odstavce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), který načte výchozí styl ze seznamu stylů. Tyto informace jsou nezbytné, aby dotaz můžete identifikovat styl odstavců, které nemají styl explicitně nastaven. Styly odstavce, se konfigurují pomocí `w:pPr` element; Pokud odstavec neobsahuje tento prvek, je formátován pomocí výchozí styl.  
  
 Toto téma vysvětluje význam některé jeho součásti dotazu a potom jako součást dokončení práce příklad ukazuje dotaz.  
  
## <a name="example"></a>Příklad  
 Zdroj dotaz pro načtení všech odstavců v dokumentu a jejich styly vypadá takto:  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 Tento výraz je podobná zdroj dotazu v předchozím příkladu [hledání styl odstavce výchozí (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md). Hlavní rozdíl je, že používá <xref:System.Xml.Linq.XContainer.Descendants%2A> osy místo <xref:System.Xml.Linq.XContainer.Elements%2A> osy. Dotaz používá <xref:System.Xml.Linq.XContainer.Descendants%2A> osy protože v dokumentech, které mají oddíly, odstavců nebude přímé podřízené objekty daného elementu body; místo toho odstavců bude dvě úrovně dolů v hierarchii. Pomocí <xref:System.Xml.Linq.XContainer.Descendants%2A> osy, bude kód pracovat z zda dokument používá oddíly.  
  
## <a name="example"></a>Příklad  
 Dotaz používá `Let` klauzule k určení elementu, který obsahuje uzel stylu. Pokud neexistuje žádný element pak `styleNode` je nastaven na `Nothing`:  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 `Let` Nejdřív pomocí klauzule <xref:System.Xml.Linq.XContainer.Elements%2A> osy k vyhledání všech elementů s názvem `pPr`, použije <xref:System.Xml.Linq.Extensions.Elements%2A> rozšíření metody k vyhledání všech podřízených elementů s názvem `pStyle`a nakonec používá <xref:System.Linq.Enumerable.FirstOrDefault%2A> standardní dotazu operátor převést kolekci typu singleton. Pokud je kolekce prázdná, `styleNode` je nastaven na `Nothing`. To je užitečné, stylu a Hledat `pStyle` podřízený uzel. Všimněte si, že pokud `pPr` podřízený uzel neexistuje, kód nemá ani selhání došlo k výjimce; místo toho `styleNode` je nastaven na `Nothing`, což je toto chování žádoucí tohoto `Let` klauzule.  
  
 Dotaz projekty kolekce anonymní typ s dva členy `StyleName` a `ParagraphNode`.  
  
## <a name="example"></a>Příklad  
 Tento příklad zpracuje WordprocessingML dokumentu, načítání odstavce uzly z WordprocessingML dokumentu. Také identifikuje styl jednotlivých odstavců. Tento příklad vychází v předchozích příkladech v tomto kurzu. Nový dotaz se nazývá v komentáře v kódu níže.  
  
 Pokyny pro vytvoření zdrojový dokument v tomto příkladu můžete najít [vytváření zdroj Office otevřít dokument XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 Tento příklad používá třídy v sestavení WindowsBase. Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
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
  
        ' Following is the new query that finds all paragraphs in the  
        ' document and their styles.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault() _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        For Each p In paragraphs  
            Console.WriteLine("StyleName:{0}", p.StyleName)  
        Next  
  
    End Sub  
End Module  
```  
  
 Tento příklad vytvoří následující výstup v případě použitého pro dokument popsané v [vytváření zdroj Office otevřít dokument XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
```  
StyleName:Heading1  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
```  
  
## <a name="next-steps"></a>Další kroky  
 V dalším tématu [načítání textu odstavců (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), vytvoříte dotaz pro načtení textu odstavce.  
  
## <a name="see-also"></a>Viz také  
 [Kurz: Manipulace se obsah v dokumentu WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
