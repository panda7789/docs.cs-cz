---
title: 'Postupy: Transformace XML pomocí LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: 347ca45c2417c1ffb9a86f3bcb51c75f3382bfad
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524816"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a>Postupy: Transformace XML pomocí LINQ (Visual Basic)

[Literály XML](../../../../visual-basic/language-reference/xml-literals/index.md) usnadňují čtení XML z jednoho zdroje a jejich transformaci do nového formátu XML. Můžete využít výhod dotazů LINQ k načtení obsahu pro transformaci nebo změnu obsahu v existujícím dokumentu do nového formátu XML.

Příklad v tomto tématu transformuje obsah ze zdrojového dokumentu XML do HTML pro zobrazení v prohlížeči.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-transform-an-xml-document"></a>Transformace dokumentu XML

1. V aplikaci Visual Studio vytvořte nový projekt Visual Basic v šabloně projektu **Konzolová aplikace** .

2. Dvojím kliknutím na soubor Module1. vb, který jste vytvořili v projektu, upravte kód Visual Basic. Přidejte následující kód do `Sub Main` modulu `Module1`. Tento kód vytvoří zdrojový dokument XML jako objekt <xref:System.Xml.Linq.XDocument>.

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

     [Postupy: načtení XML ze souboru, řetězce nebo datového proudu](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).

3. Po vytvoření zdrojového dokumentu XML přidejte následující kód, který načte všechny prvky \<Book > z objektu a převede je na dokument HTML. Seznam > prvků \<Book je vytvořen pomocí dotazu LINQ, který vrací kolekci objektů <xref:System.Xml.Linq.XElement>, které obsahují transformovaný kód HTML. Vložené výrazy můžete použít k umístění hodnot ze zdrojového dokumentu do nového formátu XML.

     Výsledný dokument HTML je zapsán do souboru pomocí metody <xref:System.Xml.Linq.XElement.Save%2A>.

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

4. Po `Sub Main` `Module1` přidejte novou metodu (`Sub`) pro transformaci > uzlu \<Description do zadaného formátu HTML. Tato metoda je volána kódem v předchozím kroku a slouží k uchování formátu > prvků \<Description.

     Tato metoda nahrazuje dílčí prvky \<Description > elementu pomocí HTML. Metoda `ReplaceWith` slouží k zachování umístění dílčích prvků. Transformovaný obsah prvku \<Description > je obsažen v elementu odstavce HTML (\<p >). Vlastnost <xref:System.Xml.Linq.XContainer.Nodes%2A> slouží k načtení transformovanýho obsahu prvku \<Description >. Tím se zajistí, že dílčí prvky budou zahrnuty v transformovaným obsahu.

     Následující kód přidejte po `Sub Main` `Module1`.

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

5. Uložte provedené změny.

6. Stisknutím klávesy F5 spusťte kód. Výsledný uložený dokument bude vypadat přibližně takto:

    ```html
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

## <a name="see-also"></a>Viz také:

- [Literály XML](../../../../visual-basic/language-reference/xml-literals/index.md)
- [Manipulace s XML v Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Postupy: Načtení XML ze souboru, řetězce nebo streamu](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Úvod do jazyka LINQ v Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
