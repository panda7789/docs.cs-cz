---
title: 'Postupy: Změna literálů XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 17da86d6d10fb1602c16fc2a8c4d6f9f8acf8ff7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-modify-xml-literals-visual-basic"></a>Postupy: Změna literálů XML (Visual Basic)
Visual Basic poskytuje praktické způsoby, jak změna literálů XML. Můžete přidat nebo odstranit elementů a atributů, a můžete také nahradit existující element nového elementu XML. Toto téma obsahuje několik příkladů, jak upravit existující literál XML.  
  
### <a name="to-modify-the-value-of-an-xml-literal"></a>Chcete-li změnit hodnotu literál XML  
  
1.  Chcete-li upravit hodnotu literál XML, získat odkaz na soubor XML literálu a nastavené `Value` vlastnost na požadovanou hodnotu.  
  
     Následující příklad kódu aktualizuje hodnotu všech \<cena > elementy v dokumentu XML.  
  
     [!code-vb[VbXmlSamples2#4](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]  
  
     Následující ukazuje ukázkový zdroj XML a změnit z tento příklad kódu XML.  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
    >  `Value` Vlastnost odkazuje na první XML element v kolekci. Pokud existuje více než jeden element, který má stejný název v kolekci, nastavení `Value` vlastnost ovlivňuje pouze první prvek v kolekci.  
  
### <a name="to-add-an-attribute-to-an-xml-literal"></a>K přidání atributu do literál XML  
  
1.  Chcete-li přidat atribut literálu XML, nejprve získejte odkaz na literál XML. Potom můžete přidat atribut přidáním nové vlastnost osy atributu XML. Můžete také přidat nový <xref:System.Xml.Linq.XAttribute> objekt literálu pomocí XML <xref:System.Xml.Linq.XContainer.Add%2A> metoda. Následující příklad ukazuje obě možnosti.  
  
     [!code-vb[VbXmlSamples2#5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]  
  
     Následující ukazuje ukázkový zdroj XML a změnit z tento příklad kódu XML.  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
  
     Další informace o vlastnosti osy atributu XML, najdete v části [vlastnost osy atributu XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).  
  
### <a name="to-add-an-element-to-an-xml-literal"></a>Chcete-li přidat element do literál XML  
  
1.  Chcete-li přidat element do literál XML, nejprve získejte odkaz na literál XML. Poté můžete přidat nové <xref:System.Xml.Linq.XElement> objektu jako poslední dílčí element elementu s použitím <xref:System.Xml.Linq.XContainer.Add%2A> metoda. Můžete přidat nové <xref:System.Xml.Linq.XElement> objektu jako první dílčí element pomocí <xref:System.Xml.Linq.XContainer.AddFirst%2A> metoda.  
  
     Chcete-li přidat nového elementu do určitého umístění relativně k další dílčí prvky, nejprve získejte odkaz na sousedících dílčí element. Poté můžete přidat nové <xref:System.Xml.Linq.XElement> objekt před přiléhající dílčí element pomocí <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> metoda. Můžete také přidat nové <xref:System.Xml.Linq.XElement> objektu po přiléhající dílčí element pomocí <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> metoda.  
  
     Následující příklad ukazuje příklady každé z těchto postupů.  
  
     [!code-vb[VbXmlSamples2#6](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]  
  
     Následující ukazuje ukázkový zdroj XML a změnit z tento příklad kódu XML.  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
  
### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a>Elementu nebo atributu odebrání literál XML  
  
1.  Chcete-li odebrat ze literál XML elementu nebo atributu, získat odkaz na element nebo atribut a volání `Remove` metoda, jak je znázorněno v následujícím příkladu.  
  
     [!code-vb[VbXmlSamples2#7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]  
  
     Následující ukazuje ukázkový zdroj XML a změnit z tento příklad kódu XML.  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
  
     Chcete-li odebrat všechny elementy nebo atributy ze literál XML, získat odkaz na literál XML a volejte <xref:System.Xml.Linq.XElement.RemoveAll%2A> metoda.  
  
### <a name="to-modify-an-xml-literal"></a>Chcete-li upravit literál XML  
  
1.  Chcete-li změnit název elementu XML, nejprve získejte odkaz na element. Potom můžete vytvořit nový <xref:System.Xml.Linq.XElement> objekt, který má nový název a předejte nové <xref:System.Xml.Linq.XElement> do objektu <xref:System.Xml.Linq.XNode.ReplaceWith%2A> metodu existující <xref:System.Xml.Linq.XElement> objektu.  
  
     Pokud má element, který chcete nahradit dílčí prvky, které je potřeba zachovat, nastavte hodnotu nové <xref:System.Xml.Linq.XElement> do objektu <xref:System.Xml.Linq.XContainer.Nodes%2A> vlastnosti existujícího elementu. Tato hodnota nového elementu nastaví vnitřní XML existujícího elementu. Jinak můžete nastavit hodnotu nového elementu `Value` vlastnosti existujícího elementu.  
  
     Následující příklad kódu nahradí všechny \<popis > elementů s hodnotou \<abstraktní > elementu. Obsah \<popis > elementu se zachová, i v novém \<abstraktní > element pomocí <xref:System.Xml.Linq.XContainer.Nodes%2A> vlastnost \<popis > <xref:System.Xml.Linq.XElement> objektu.  
  
     [!code-vb[VbXmlSamples2#8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]  
  
     Následující ukazuje ukázkový zdroj XML a změnit z tento příklad kódu XML.  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
 [Zacházení s XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Postupy: Načtení XML ze souboru, řetězce nebo streamu](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Úvod do LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
