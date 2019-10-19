---
title: Načítání odstavců a jejich stylů (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: 4bc20556fb668db2db3e6bcfa42e96cc0d963b93
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582152"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a>Načítání odstavců a jejich stylů (Visual Basic)
V tomto příkladu zapíšeme dotaz, který načte uzly odstavců z dokumentu WordprocessingML. Určuje také styl každého odstavce.  
  
 Tento dotaz sestaví na dotazu v předchozím příkladu a hledá [výchozí styl odstavce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), který načte výchozí styl ze seznamu stylů. Tyto informace jsou požadovány, aby dotaz mohl identifikovat styl odstavců, které nemají explicitně nastaven styl. Odstavcové styly jsou nastaveny pomocí elementu `w:pPr`; Pokud odstavec neobsahuje tento prvek, je naformátován s výchozím stylem.  
  
 Toto téma vysvětluje význam některých částí dotazu a pak zobrazuje dotaz jako součást kompletního a funkčního příkladu.  
  
## <a name="example"></a>Příklad  
 Zdroj dotazu pro načtení všech odstavců v dokumentu a jejich stylů je následující:  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 Tento výraz je podobný zdroji dotazu v předchozím příkladu, kde je [nalezen výchozí styl odstavce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md). Hlavní rozdíl spočívá v tom, že místo <xref:System.Xml.Linq.XContainer.Elements%2A> osy používá osu <xref:System.Xml.Linq.XContainer.Descendants%2A>. Dotaz používá <xref:System.Xml.Linq.XContainer.Descendants%2A> osu, protože v dokumentech, které mají oddíly, nebudou odstavce přímo podřízeny elementu těla; místo toho se v hierarchii budou v těchto odstavcích vycházet dvě úrovně. Pomocí <xref:System.Xml.Linq.XContainer.Descendants%2A> osy bude kód fungovat bez ohledu na to, jestli dokument používá oddíly.  
  
## <a name="example"></a>Příklad  
 Dotaz používá klauzuli `Let` k určení prvku, který obsahuje uzel Style. Pokud není žádný element, `styleNode` je nastaven na `Nothing`:  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 Klauzule `Let` nejprve používá <xref:System.Xml.Linq.XContainer.Elements%2A> osu k vyhledání všech prvků s názvem `pPr`, poté používá metodu rozšíření <xref:System.Xml.Linq.Extensions.Elements%2A> k nalezení všech podřízených elementů s názvem `pStyle` a nakonec používá operátor dotazu <xref:System.Linq.Enumerable.FirstOrDefault%2A> Standard k převedení kolekce na typ singleton. Pokud je kolekce prázdná, `styleNode` je nastavená na `Nothing`. Toto je užitečná idiom k vyhledání podřízeného uzlu `pStyle`. Všimněte si, že pokud `pPr` podřízený uzel neexistuje, kód selže ani selže vyvoláním výjimky; místo toho je `styleNode` nastaveno na `Nothing`, což je požadované chování této klauzule `Let`.  
  
 Dotaz projektuje kolekci anonymního typu se dvěma členy `StyleName` a `ParagraphNode`.  
  
## <a name="example"></a>Příklad  
 Tento příklad zpracovává dokument WordprocessingML a načítá uzly odstavců z dokumentu WordprocessingML. Určuje také styl každého odstavce. Tento příklad sestaví na předchozích příkladech v tomto kurzu. Nový dotaz se zavolá v komentářích v následujícím kódu.  
  
 Pokyny pro vytvoření zdrojového dokumentu pro tento příklad najdete v [tématu vytvoření zdrojového dokumentu XML pro Office Open (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 Tento příklad používá třídy nalezené v sestavení WindowsBase. Používá typy v oboru názvů <xref:System.IO.Packaging?displayProperty=nameWithType>.  
  
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
  
 Tento příklad vytvoří následující výstup při použití v dokumentu popsaném v [tématu vytvoření zdrojového dokumentu XML pro Office Open (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
```console  
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
 V dalším tématu [načtení textu odstavců (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md)vytvoříte dotaz pro načtení textu odstavců.  
  
## <a name="see-also"></a>Viz také:

- [Kurz: manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
