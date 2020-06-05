---
title: 'Postupy: Změna literálů XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: a2ac2e9802d4c8ab522bb430d15cce5616430437
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374872"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a>Postupy: Změna literálů XML (Visual Basic)

Visual Basic poskytuje pohodlný způsob, jak upravit literály XML. Můžete přidat nebo odstranit prvky a atributy a můžete také nahradit existující element novým elementem XML. Toto téma poskytuje několik příkladů, jak upravit existující literál XML.

### <a name="to-modify-the-value-of-an-xml-literal"></a>Úprava hodnoty literálu XML

1. Chcete-li změnit hodnotu literálu XML, získejte odkaz na literál XML a nastavte `Value` vlastnost na požadovanou hodnotu.

    Následující příklad kódu aktualizuje hodnotu všech \<Price> prvků v dokumentu XML.

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    Následující ukázka ukazuje zdrojový kód XML a upravený kód XML z tohoto příkladu kódu.

    Zdrojový kód XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    Upravený kód XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>47.20</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>48.25</Price>
      </Book>
    </Catalog>
    ```

    > [!NOTE]
    > `Value`Vlastnost odkazuje na první prvek XML v kolekci. Pokud je v kolekci více než jeden prvek, který má stejný název, nastavení `Value` vlastnosti ovlivní pouze první prvek v kolekci.

### <a name="to-add-an-attribute-to-an-xml-literal"></a>Přidání atributu do literálu XML

1. Chcete-li přidat atribut do literálu XML, nejprve získejte odkaz na literál XML. Pak můžete přidat atribut přidáním nové vlastnosti osa atributu XML. <xref:System.Xml.Linq.XAttribute>Do literálu XML můžete také přidat nový objekt pomocí <xref:System.Xml.Linq.XContainer.Add%2A> metody. Následující příklad ukazuje obě možnosti.

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    Následující ukázka ukazuje zdrojový kód XML a upravený kód XML z tohoto příkladu kódu.

    Zdrojový kód XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    Upravený kód XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    Další informace o vlastnostech osy atributu XML naleznete v tématu [Vlastnosti osy atributu XML](../../../language-reference/xml-axis/xml-attribute-axis-property.md).

### <a name="to-add-an-element-to-an-xml-literal"></a>Přidání elementu do literálu XML

1. Chcete-li přidat prvek do literálu XML, nejprve získejte odkaz na literál XML. Pak můžete přidat nový <xref:System.Xml.Linq.XElement> objekt jako poslední dílčí prvek elementu pomocí <xref:System.Xml.Linq.XContainer.Add%2A> metody. Můžete přidat nový <xref:System.Xml.Linq.XElement> objekt jako první dílčí prvek pomocí <xref:System.Xml.Linq.XContainer.AddFirst%2A> metody.

    Chcete-li přidat nový prvek v určitém umístění relativně k jiným dílčím prvkům, nejprve získejte odkaz na sousední dílčí prvek. Pak můžete přidat nový <xref:System.Xml.Linq.XElement> objekt před sousední dílčí element pomocí <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> metody. Můžete také přidat nový <xref:System.Xml.Linq.XElement> objekt za sousední dílčí prvek pomocí <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> metody.

    Následující příklad ukazuje příklady každé z těchto technik.

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    Následující ukázka ukazuje zdrojový kód XML a upravený kód XML z tohoto příkladu kódu.

    Zdrojový kód XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    Upravený kód XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331">
        <Publisher>Microsoft Press</Publisher>
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
        <PublishDate>2005-2-14</PublishDate>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a>Odebrání elementu nebo atributu z literálu XML

1. Chcete-li odebrat element nebo atribut z literálu XML, získejte odkaz na element nebo atribut a zavolejte `Remove` metodu, jak je znázorněno v následujícím příkladu.

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    Následující ukázka ukazuje zdrojový kód XML a upravený kód XML z tohoto příkladu kódu.

    Zdrojový kód XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

    Upravený kód XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book></Catalog>
    ```

    Chcete-li odebrat všechny prvky nebo atributy z literálu XML, získejte odkaz na literál XML a zavolejte <xref:System.Xml.Linq.XElement.RemoveAll%2A> metodu.

### <a name="to-modify-an-xml-literal"></a>Úprava literálu XML

1. Chcete-li změnit název elementu XML, nejprve získejte odkaz na prvek. Pak můžete vytvořit nový <xref:System.Xml.Linq.XElement> objekt, který má nový název a předat novému <xref:System.Xml.Linq.XElement> objektu <xref:System.Xml.Linq.XNode.ReplaceWith%2A> metodě stávajícího <xref:System.Xml.Linq.XElement> objektu.

    Pokud element, který chcete nahradit, má dílčí prvky, které musí být zachovány, nastavte hodnotu nového <xref:System.Xml.Linq.XElement> objektu na <xref:System.Xml.Linq.XContainer.Nodes%2A> vlastnost existujícího elementu. Tím se nastaví hodnota nového prvku na vnitřní XML existujícího elementu. V opačném případě můžete nastavit hodnotu nového prvku na `Value` vlastnost existujícího elementu.

    Následující příklad kódu nahradí všechny \<Description> prvky \<Abstract> elementem. Obsah \<Description> elementu se zachová v novém \<Abstract> elementu pomocí <xref:System.Xml.Linq.XContainer.Nodes%2A> vlastnosti \<Description> <xref:System.Xml.Linq.XElement> objektu.

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    Následující ukázka ukazuje zdrojový kód XML a upravený kód XML z tohoto příkladu kódu.

    Zdrojový kód XML:

    ```xml
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
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Description>
      </Book>
    </Catalog>
    ```

    Upravený kód XML:

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <MSRP>44.95</MSRP>    <Abstract>
          An in-depth look at creating applications
          with <technology>XML</technology>. For
          <audience>beginners</audience> or
          <audience>advanced</audience> developers.
        </Abstract>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <MSRP>45.95</MSRP>    <Abstract>
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Abstract>
      </Book>
    </Catalog>
    ```

## <a name="see-also"></a>Viz také

- [Zacházení s XML v jazyce Visual Basic](manipulating-xml.md)
- [XML](index.md)
- [Postupy: Načtení XML ze souboru, řetězce nebo proudu](how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../linq/index.md)
- [Představení technologie LINQ v jazyce Visual Basic](../linq/introduction-to-linq.md)
