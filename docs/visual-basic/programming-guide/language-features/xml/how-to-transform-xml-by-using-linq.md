---
title: 'Postupy: Transformace XML pomocí LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: 94ad5180c7921a5ace09f9161de5f275475e46d4
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2018
ms.locfileid: "42924906"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a>Postupy: Transformace XML pomocí LINQ (Visual Basic)
[Literály XML](../../../../visual-basic/language-reference/xml-literals/index.md) usnadňují přečíst XML z jednoho zdroje a transformovat ho do nového formátu XML. Můžete využívat dotazy LINQ načítat obsah, který umožňuje transformovat nebo změnit obsah v existující dokument na nový formát XML.  
  
 V příkladu v tomto tématu transformuje obsah ze zdrojového dokumentu XML do formátu HTML, které lze zobrazit v prohlížeči.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-transform-an-xml-document"></a>K transformaci dokumentu XML  
  
1.  V sadě Visual Studio vytvořte nový projekt v jazyce Visual Basic **konzolovou aplikaci** šablony projektu.  
  
2.  Poklikejte na soubor Module1.vb vytvořen v projektu a upravte kód jazyka Visual Basic. Přidejte následující kód, který `Sub Main` z `Module1` modulu. Tento kód vytvoří zdrojovém dokumentu XML jako <xref:System.Xml.Linq.XDocument> objektu.  
  
    ```vb  
    Dim catalog =   
      <?xml version="1.0"?>  
        <Catalog>  
          <Book id="bk101">  
            <Author>Garghentini, Davide</Author>  
            <Title>XML Developer's Guide</Title>  
            <Price>44.95</Price>  
            <Description>  
              An in-depth look at creating applications  
              with <technology>XML</technology>. For   
              <audience>beginners</audience> or   
              <audience>advanced</audience> developers.  
            </Description>  
          </Book>  
          <Book id="bk331">  
            <Author>Spencer, Phil</Author>  
            <Title>Developing Applications with Visual Basic .NET</Title>  
            <Price>45.95</Price>  
            <Description>  
              Get the expert insights, practical code samples,   
              and best practices you need   
              to advance your expertise with <technology>Visual   
              Basic .NET</technology>.   
              Learn how to create faster, more reliable applications  
              based on professional,   
              pragmatic guidance by today's top <audience>developers</audience>.  
            </Description>  
          </Book>  
        </Catalog>  
    ```  
  
     [Postupy: načtení XML ze souboru, řetězce nebo Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).  
  
3.  Za kód k vytvoření zdrojového dokumentu XML, přidejte následující kód k načtení všech \<knihy > prvky z objektu a transformují je na dokument HTML. Seznam \<knihy > prvků je vytvořena pomocí dotaz LINQ, který vrátí kolekci <xref:System.Xml.Linq.XElement> objektů, které obsahují kód HTML pro transformovaná. Vložené výrazy můžete použít pro převedení hodnot ze zdrojového dokumentu v novém formátu XML.  
  
     Výsledný dokumentu HTML je zapsána do souboru s použitím <xref:System.Xml.Linq.XElement.Save%2A> metody.  
  
    ```vb  
    Dim htmlOutput =   
      <html>  
        <body>  
          <%= From book In catalog.<Catalog>.<Book>   
              Select <div>  
                       <h1><%= book.<Title>.Value %></h1>  
                       <h3><%= "By " & book.<Author>.Value %></h3>  
                        <h3><%= "Price = " & book.<Price>.Value %></h3>  
                        <h2>Description</h2>  
                        <%= TransformDescription(book.<Description>(0)) %>  
                        <hr/>  
                      </div> %>  
        </body>  
      </html>  
  
    htmlOutput.Save("BookDescription.html")  
    ```  
  
4.  Po `Sub Main` z `Module1`, přidejte novou metodu (`Sub`) k transformaci \<popis > uzlu na zadaném formátu HTML. Tato metoda je volána kód v předchozím kroku a používá k zachování formát \<popis > elementy.  
  
     Tato metoda nahrazuje dílčí prvky \<popis > element s HTML. `ReplaceWith` Metoda se používá k zachování umístění podřízených elementů. Transformovaný obsah \<popis > element je součástí HTML odstavec (\<p >) element. <xref:System.Xml.Linq.XContainer.Nodes%2A> Vlastnost se používá k načtení transformovaný obsah \<popis > element. Tím se zajistí, že dílčí prvky jsou součástí převedeného obsahu.  
  
     Přidejte následující kód za `Sub Main` z `Module1`.  
  
    ```vb  
    Public Function TransformDescription(ByVal desc As XElement) As XElement  
  
      ' Replace <technology> elements with <b>.  
      Dim content = (From element In desc...<technology>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<b><%= content(i).Value %></b>)  
        Next  
      End If  
  
      ' Replace <audience> elements with <i>.  
      content = (From element In desc...<audience>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<i><%= content(i).Value %></i>)  
        Next  
      End If  
  
      ' Return the updated contents of the <Description> element.  
      Return <p><%= desc.Nodes %></p>  
    End Function  
    ```  
  
5.  Uložte provedené změny.  
  
6.  Stisknutím klávesy F5 spusťte kód. Výsledná uložit dokument bude vypadat takto:  
  
    ```  
    <?xml version="1.0"?>  
    <html>  
      <body>  
        <div>  
          <h1>XML Developer's Guide</h1>  
          <h3>By Garghentini, Davide</h3>  
          <h3>Price = 44.95</h3>  
          <h2>Description</h2>  
          <p>  
            An in-depth look at creating applications  
            with <b>XML</b>. For   
            <i>beginners</i> or   
            <i>advanced</i> developers.  
          </p>  
          <hr />  
        </div>  
        <div>  
          <h1>Developing Applications with Visual Basic .NET</h1>  
          <h3>By Spencer, Phil</h3>  
          <h3>Price = 45.95</h3>  
          <h2>Description</h2>  
          <p>  
            Get the expert insights, practical code   
            samples, and best practices you need   
            to advance your expertise with <b>Visual   
            Basic .NET</b>. Learn how to create faster,  
            more reliable applications based on  
            professional, pragmatic guidance by today's   
            top <i>developers</i>.  
          </p>  
          <hr />  
        </div>  
      </body>  
    </html>  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Literály XML](../../../../visual-basic/language-reference/xml-literals/index.md)  
 [Manipulace s kódem XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Postupy: Načtení XML ze souboru, řetězce nebo streamu](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Úvod do LINQ v JAZYKU Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
