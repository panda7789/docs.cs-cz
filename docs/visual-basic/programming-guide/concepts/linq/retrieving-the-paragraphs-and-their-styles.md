---
title: Načtení odstavců a jejich stylů (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: a726c3b609d778d8d91be61091a3627ec1358dfc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716023"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a>Načtení odstavců a jejich stylů (Visual Basic)
V tomto příkladu jsme vytvořit dotaz, který načte uzly odstavců z dokumentu WordprocessingML. Styl k jednotlivým odstavcům také identifikuje.  
  
 Tento dotaz je založena na dotazu v předchozím příkladu [vyhledání výchozího stylu odstavce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), který načte výchozí styl seznamu styly. Tyto informace jsou nezbytné, aby dotaz můžete identifikovat styl odstavce, které nemají explicitně nastavit styl. Styly odstavci, se konfigurují pomocí `w:pPr` element; Pokud odstavce neobsahuje tohoto prvku, je naformátována pomocí výchozího stylu.  
  
 Toto téma vysvětluje význam některé části dotazu a potom se zobrazí dotaz jako součást kompletní, funkční příklad.  
  
## <a name="example"></a>Příklad  
 Zdrojový dotaz pro načtení všech odstavce v dokumentu a jejich stylů vypadá takto:  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 Tento výraz je podobný zdroje dotazu v předchozím příkladu [hledání (Visual Basic) výchozí styl odstavce](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md). Hlavním rozdílem je, že používá <xref:System.Xml.Linq.XContainer.Descendants%2A> osy místo <xref:System.Xml.Linq.XContainer.Elements%2A> osy. Použije dotaz <xref:System.Xml.Linq.XContainer.Descendants%2A> osy vzhledem k tomu, že v dokumentech, které mají oddíly, odstavců nebudou přímé podřízené objekty daného elementu těla; místo toho odstavců bude dvě úrovně dolů v hierarchii. S použitím <xref:System.Xml.Linq.XContainer.Descendants%2A> osy, kód bude fungovat z Určuje, jestli dokument používá oddíly.  
  
## <a name="example"></a>Příklad  
 Použije dotaz `Let` klauzule určit element, který obsahuje uzel stylu. Pokud neexistuje žádný element, pak `styleNode` je nastavena na `Nothing`:  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 `Let` Nejdřív pomocí klauzule <xref:System.Xml.Linq.XContainer.Elements%2A> osy k vyhledání všech elementů s názvem `pPr`, použije <xref:System.Xml.Linq.Extensions.Elements%2A> metodu rozšíření k vyhledání všech podřízených elementů s názvem `pStyle`a nakonec používá <xref:System.Linq.Enumerable.FirstOrDefault%2A> standardního dotazu operátor pro převod kolekce na jednotlivý prvek. Pokud kolekce je prázdná, `styleNode` je nastavena na `Nothing`. To je užitečné idiom Hledat `pStyle` uzel potomka. Všimněte si, že pokud `pPr` podřízený uzel se buď neexistuje, kód neodpovídá ani selhání vyvoláním výjimky; místo toho `styleNode` je nastavena na `Nothing`, což je požadované chování tohoto `Let` klauzuli.  
  
 Dotaz projekty kolekce anonymního typu se dvěma členy `StyleName` a `ParagraphNode`.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu zpracovává dokumentu WordprocessingML načítání uzly odstavců z dokumentu WordprocessingML. Styl k jednotlivým odstavcům také identifikuje. Tento příklad je založen na předchozí příklady v tomto kurzu. Nový dotaz je uvedeny v komentářích v následujícím kódu.  
  
 Můžete najít pokyny pro vytvoření zdrojového dokumentu v tomto příkladu v [vytváření zdroj Office otevřít dokument XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
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
  
 Tento příklad vytvoří následující výstup při použití u dokumentu je popsáno v [vytváření zdroj Office otevřít dokument XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
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
 V dalším tématu [načtení textu odstavců (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), vytvoříte dotaz pro načtení textu odstavců.  
  
## <a name="see-also"></a>Viz také:
- [Kurz: Manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
