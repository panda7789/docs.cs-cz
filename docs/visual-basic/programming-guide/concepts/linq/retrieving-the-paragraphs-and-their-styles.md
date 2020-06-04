---
title: Načtení odstavců a jejich stylů
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: ad904abf9bd94e83b981859662c22787652e294f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413402"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a>Načítání odstavců a jejich stylů (Visual Basic)
V tomto příkladu zapíšeme dotaz, který načte uzly odstavců z dokumentu WordprocessingML. Určuje také styl každého odstavce.  
  
 Tento dotaz sestaví na dotazu v předchozím příkladu a hledá [výchozí styl odstavce (Visual Basic)](finding-the-default-paragraph-style.md), který načte výchozí styl ze seznamu stylů. Tyto informace jsou požadovány, aby dotaz mohl identifikovat styl odstavců, které nemají explicitně nastaven styl. Odstavcové styly se nastavují prostřednictvím `w:pPr` elementu; Pokud odstavec tento prvek neobsahuje, naformátuje se s výchozím stylem.  
  
 Toto téma vysvětluje význam některých částí dotazu a pak zobrazuje dotaz jako součást kompletního a funkčního příkladu.  
  
## <a name="example"></a>Příklad  
 Zdroj dotazu pro načtení všech odstavců v dokumentu a jejich stylů je následující:  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 Tento výraz je podobný zdroji dotazu v předchozím příkladu, kde je [nalezen výchozí styl odstavce (Visual Basic)](finding-the-default-paragraph-style.md). Hlavní rozdíl spočívá v tom, že <xref:System.Xml.Linq.XContainer.Descendants%2A> místo osy používá osu <xref:System.Xml.Linq.XContainer.Elements%2A> . Dotaz používá osu, <xref:System.Xml.Linq.XContainer.Descendants%2A> protože v dokumentech, které mají oddíly, nebudou odstavce přímo podřízeny elementu těla. místo toho budou v hierarchii tyto odstavce dvě. Pomocí <xref:System.Xml.Linq.XContainer.Descendants%2A> osy bude kód pracovat na tom, zda dokument používá oddíly.  
  
## <a name="example"></a>Příklad  
 Dotaz používá `Let` klauzuli k určení prvku, který obsahuje uzel Style. Pokud není žádný element, pak `styleNode` je nastaven na `Nothing` :  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 `Let`Klauzule nejprve používá <xref:System.Xml.Linq.XContainer.Elements%2A> osu k vyhledání všech prvků s názvem `pPr` a poté používá <xref:System.Xml.Linq.Extensions.Elements%2A> metodu rozšíření k vyhledání všech podřízených elementů s názvem `pStyle` a nakonec používá <xref:System.Linq.Enumerable.FirstOrDefault%2A> standardní operátor dotazu k převedení kolekce na typ singleton. Je-li kolekce prázdná, `styleNode` je nastavena na hodnotu `Nothing` . Toto je užitečná idiom pro vyhledání `pStyle` podřízeného uzlu. Všimněte si, že pokud `pPr` neexistuje podřízený uzel, kód selže ani selže vyvoláním výjimky; namísto toho `styleNode` je nastavena na `Nothing` , což je požadované chování této `Let` klauzule.  
  
 Dotaz projektuje kolekci anonymního typu se dvěma členy `StyleName` a `ParagraphNode` .  
  
## <a name="example"></a>Příklad  
 Tento příklad zpracovává dokument WordprocessingML a načítá uzly odstavců z dokumentu WordprocessingML. Určuje také styl každého odstavce. Tento příklad sestaví na předchozích příkladech v tomto kurzu. Nový dotaz se zavolá v komentářích v následujícím kódu.  
  
 Pokyny pro vytvoření zdrojového dokumentu pro tento příklad najdete v [tématu vytvoření zdrojového dokumentu XML pro Office Open (Visual Basic)](creating-the-source-office-open-xml-document.md).  
  
 Tento příklad používá třídy nalezené v sestavení WindowsBase. Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.  
  
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
  
 Tento příklad vytvoří následující výstup při použití v dokumentu popsaném v [tématu vytvoření zdrojového dokumentu XML pro Office Open (Visual Basic)](creating-the-source-office-open-xml-document.md).  
  
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
 V dalším tématu [načtení textu odstavců (Visual Basic)](retrieving-the-text-of-the-paragraphs.md)vytvoříte dotaz pro načtení textu odstavců.  
  
## <a name="see-also"></a>Viz také

- [Kurz: manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
