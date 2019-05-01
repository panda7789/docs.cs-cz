---
title: 'Postupy: Změna literálů XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 003715b04f3a5c0fb41e846beb189f117378ea58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053025"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a>Postupy: Změna literálů XML (Visual Basic)

Visual Basic poskytuje pohodlný způsob změna literálů XML. Můžete přidat nebo odstranit elementy a atributy, a můžete také nahradit existující prvek nový prvek XML. Toto téma obsahuje několik příkladů toho, jak změnit existující literálu XML.

### <a name="to-modify-the-value-of-an-xml-literal"></a>Chcete-li změnit hodnotu literál XML

1. Chcete-li změnit hodnotu literál XML, získat odkaz na XML literál a nastavte `Value` vlastnost na požadovanou hodnotu.

    Následující příklad kódu aktualizuje hodnotu všech \<cena > elementy v dokumentu XML.

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    Následující znázorňuje vzorový zdroj XML a změnit tento příklad kódu XML.

    Zdrojového kódu XML:

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

    Upravené XML:

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
    > `Value` Vlastnost odkazuje na první prvek XML v kolekci. Pokud existuje více než jeden element, který má stejný název v kolekci, nastavení `Value` vlastnost ovlivňuje pouze první prvek v kolekci.

### <a name="to-add-an-attribute-to-an-xml-literal"></a>Chcete-li přidat atribut literál XML

1. Pokud chcete přidat atribut literálu XML, nejprve získejte odkaz na literál XML. Potom můžete přidat atribut tak, že přidáte novou vlastnost osy atributu XML. Můžete také přidat nový <xref:System.Xml.Linq.XAttribute> objekt pomocí literálů XML <xref:System.Xml.Linq.XContainer.Add%2A> metody. Následující příklad ukazuje obě možnosti.

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    Následující znázorňuje vzorový zdroj XML a změnit tento příklad kódu XML.

    Zdrojového kódu XML:

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

    Upravené XML:

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

    Další informace o vlastnosti osy atributu XML, naleznete v tématu [vlastnost osy atributu XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).

### <a name="to-add-an-element-to-an-xml-literal"></a>Chcete-li přidat prvek literál XML

1. Chcete-li přidat element do literálů XML, nejprve získejte odkaz na literál XML. Poté můžete přidat nový <xref:System.Xml.Linq.XElement> objektu jako poslední dílčí element elementu s použitím <xref:System.Xml.Linq.XContainer.Add%2A> metody. Můžete přidat nový <xref:System.Xml.Linq.XElement> objekt jako první dílčí element s použitím <xref:System.Xml.Linq.XContainer.AddFirst%2A> metody.

    Chcete-li přidat nový prvek v konkrétním umístění vzhledem k další dílčí prvky, nejprve získejte odkaz na sousední dílčí element. Poté můžete přidat nové <xref:System.Xml.Linq.XElement> objektu před sousední dílčí element s použitím <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> metody. Můžete také přidat nové <xref:System.Xml.Linq.XElement> objektu po sousední dílčí element s použitím <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> metody.

    Následující příklad ukazuje příklady každého z následujících postupů.

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    Následující znázorňuje vzorový zdroj XML a změnit tento příklad kódu XML.

    Zdrojového kódu XML:

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

    Upravené XML:

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

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a>K odebrání literál XML elementu nebo atributu

1. Chcete-li odebrat ze literál XML elementu nebo atributu, získat odkaz na element nebo atribut a volání `Remove` způsob, jak je znázorněno v následujícím příkladu.

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    Následující znázorňuje vzorový zdroj XML a změnit tento příklad kódu XML.

    Zdrojového kódu XML:

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

    Upravené XML:

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

    Pokud chcete odebrat všechny elementy nebo atributy ze literál XML, získejte odkaz na literál XML a volat <xref:System.Xml.Linq.XElement.RemoveAll%2A> metody.

### <a name="to-modify-an-xml-literal"></a>Chcete-li změnit literál XML

1. Chcete-li změnit název elementu XML, nejprve získejte odkaz na element. Potom můžete vytvořit nový <xref:System.Xml.Linq.XElement> objekt, který se má nový název a předejte nový <xref:System.Xml.Linq.XElement> objektu <xref:System.Xml.Linq.XNode.ReplaceWith%2A> metoda existující <xref:System.Xml.Linq.XElement> objektu.

    Pokud má element, který chcete nahradit dílčím prvkům, které musí být zachovány, nastavte hodnotu nového <xref:System.Xml.Linq.XElement> objektu <xref:System.Xml.Linq.XContainer.Nodes%2A> vlastnosti existujícího elementu. To se nastavit hodnotu nového elementu na vnitřní XML z existujícího elementu. V opačném případě můžete nastavit hodnotu nový prvek `Value` vlastnosti existujícího elementu.

    Následující příklad kódu nahradí všechny \<popis > elementy \<abstraktní > element. Obsah \<popis > element je zachováno v novém \<abstraktní > elementu s použitím <xref:System.Xml.Linq.XContainer.Nodes%2A> vlastnost \<popis > <xref:System.Xml.Linq.XElement> objektu.

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    Následující znázorňuje vzorový zdroj XML a změnit tento příklad kódu XML.

    Zdrojového kódu XML:

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

    Upravené XML:

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

## <a name="see-also"></a>Viz také:

- [Manipulace s kódem XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Postupy: Načtení XML ze souboru, řetězce nebo Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Úvod do LINQ v JAZYKU Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
