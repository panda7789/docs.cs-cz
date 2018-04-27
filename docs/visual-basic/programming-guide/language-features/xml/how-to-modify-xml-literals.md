---
title: 'Postupy: Změna literálů XML (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 230cf17fec8356b8f16ea2118b0bda0589ecd04a
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="09472-102">Postupy: Změna literálů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09472-102">How to: Modify XML Literals (Visual Basic)</span></span>
<span data-ttu-id="09472-103">Visual Basic poskytuje praktické způsoby, jak změna literálů XML.</span><span class="sxs-lookup"><span data-stu-id="09472-103">Visual Basic provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="09472-104">Můžete přidat nebo odstranit elementů a atributů, a můžete také nahradit existující element nového elementu XML.</span><span class="sxs-lookup"><span data-stu-id="09472-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="09472-105">Toto téma obsahuje několik příkladů, jak upravit existující literál XML.</span><span class="sxs-lookup"><span data-stu-id="09472-105">This topic provides several examples of how to modify an existing XML literal.</span></span>  
  
### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="09472-106">Chcete-li změnit hodnotu literál XML</span><span class="sxs-lookup"><span data-stu-id="09472-106">To modify the value of an XML literal</span></span>  
  
1.  <span data-ttu-id="09472-107">Chcete-li upravit hodnotu literál XML, získat odkaz na soubor XML literálu a nastavené `Value` vlastnost na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="09472-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>  
  
     <span data-ttu-id="09472-108">Následující příklad kódu aktualizuje hodnotu všech \<cena > elementy v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="09472-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>  
  
     [!code-vb[VbXmlSamples2#4](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]  
  
     <span data-ttu-id="09472-109">Následující ukazuje ukázkový zdroj XML a změnit z tento příklad kódu XML.</span><span class="sxs-lookup"><span data-stu-id="09472-109">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
    >  <span data-ttu-id="09472-110">`Value` Vlastnost odkazuje na první XML element v kolekci.</span><span class="sxs-lookup"><span data-stu-id="09472-110">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="09472-111">Pokud existuje více než jeden element, který má stejný název v kolekci, nastavení `Value` vlastnost ovlivňuje pouze první prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="09472-111">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>  
  
### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="09472-112">K přidání atributu do literál XML</span><span class="sxs-lookup"><span data-stu-id="09472-112">To add an attribute to an XML literal</span></span>  
  
1.  <span data-ttu-id="09472-113">Chcete-li přidat atribut literálu XML, nejprve získejte odkaz na literál XML.</span><span class="sxs-lookup"><span data-stu-id="09472-113">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="09472-114">Potom můžete přidat atribut přidáním nové vlastnost osy atributu XML.</span><span class="sxs-lookup"><span data-stu-id="09472-114">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="09472-115">Můžete také přidat nový <xref:System.Xml.Linq.XAttribute> objekt literálu pomocí XML <xref:System.Xml.Linq.XContainer.Add%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="09472-115">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="09472-116">Následující příklad ukazuje obě možnosti.</span><span class="sxs-lookup"><span data-stu-id="09472-116">The following example shows both options.</span></span>  
  
     [!code-vb[VbXmlSamples2#5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]  
  
     <span data-ttu-id="09472-117">Následující ukazuje ukázkový zdroj XML a změnit z tento příklad kódu XML.</span><span class="sxs-lookup"><span data-stu-id="09472-117">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
     <span data-ttu-id="09472-118">Další informace o vlastnosti osy atributu XML, najdete v části [vlastnost osy atributu XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span><span class="sxs-lookup"><span data-stu-id="09472-118">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>  
  
### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="09472-119">Chcete-li přidat element do literál XML</span><span class="sxs-lookup"><span data-stu-id="09472-119">To add an element to an XML literal</span></span>  
  
1.  <span data-ttu-id="09472-120">Chcete-li přidat element do literál XML, nejprve získejte odkaz na literál XML.</span><span class="sxs-lookup"><span data-stu-id="09472-120">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="09472-121">Poté můžete přidat nové <xref:System.Xml.Linq.XElement> objektu jako poslední dílčí element elementu s použitím <xref:System.Xml.Linq.XContainer.Add%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="09472-121">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="09472-122">Můžete přidat nové <xref:System.Xml.Linq.XElement> objektu jako první dílčí element pomocí <xref:System.Xml.Linq.XContainer.AddFirst%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="09472-122">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>  
  
     <span data-ttu-id="09472-123">Chcete-li přidat nového elementu do určitého umístění relativně k další dílčí prvky, nejprve získejte odkaz na sousedících dílčí element.</span><span class="sxs-lookup"><span data-stu-id="09472-123">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="09472-124">Poté můžete přidat nové <xref:System.Xml.Linq.XElement> objekt před přiléhající dílčí element pomocí <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="09472-124">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="09472-125">Můžete také přidat nové <xref:System.Xml.Linq.XElement> objektu po přiléhající dílčí element pomocí <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="09472-125">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>  
  
     <span data-ttu-id="09472-126">Následující příklad ukazuje příklady každé z těchto postupů.</span><span class="sxs-lookup"><span data-stu-id="09472-126">The following example shows examples of each of these techniques.</span></span>  
  
     [!code-vb[VbXmlSamples2#6](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]  
  
     <span data-ttu-id="09472-127">Následující ukazuje ukázkový zdroj XML a změnit z tento příklad kódu XML.</span><span class="sxs-lookup"><span data-stu-id="09472-127">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="09472-128">Elementu nebo atributu odebrání literál XML</span><span class="sxs-lookup"><span data-stu-id="09472-128">To remove an element or attribute from an XML literal</span></span>  
  
1.  <span data-ttu-id="09472-129">Chcete-li odebrat ze literál XML elementu nebo atributu, získat odkaz na element nebo atribut a volání `Remove` metoda, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="09472-129">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>  
  
     [!code-vb[VbXmlSamples2#7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]  
  
     <span data-ttu-id="09472-130">Následující ukazuje ukázkový zdroj XML a změnit z tento příklad kódu XML.</span><span class="sxs-lookup"><span data-stu-id="09472-130">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
     <span data-ttu-id="09472-131">Chcete-li odebrat všechny elementy nebo atributy ze literál XML, získat odkaz na literál XML a volejte <xref:System.Xml.Linq.XElement.RemoveAll%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="09472-131">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>  
  
### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="09472-132">Chcete-li upravit literál XML</span><span class="sxs-lookup"><span data-stu-id="09472-132">To modify an XML literal</span></span>  
  
1.  <span data-ttu-id="09472-133">Chcete-li změnit název elementu XML, nejprve získejte odkaz na element.</span><span class="sxs-lookup"><span data-stu-id="09472-133">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="09472-134">Potom můžete vytvořit nový <xref:System.Xml.Linq.XElement> objekt, který má nový název a předejte nové <xref:System.Xml.Linq.XElement> do objektu <xref:System.Xml.Linq.XNode.ReplaceWith%2A> metodu existující <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="09472-134">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     <span data-ttu-id="09472-135">Pokud má element, který chcete nahradit dílčí prvky, které je potřeba zachovat, nastavte hodnotu nové <xref:System.Xml.Linq.XElement> do objektu <xref:System.Xml.Linq.XContainer.Nodes%2A> vlastnosti existujícího elementu.</span><span class="sxs-lookup"><span data-stu-id="09472-135">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="09472-136">Tato hodnota nového elementu nastaví vnitřní XML existujícího elementu.</span><span class="sxs-lookup"><span data-stu-id="09472-136">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="09472-137">Jinak můžete nastavit hodnotu nového elementu `Value` vlastnosti existujícího elementu.</span><span class="sxs-lookup"><span data-stu-id="09472-137">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>  
  
     <span data-ttu-id="09472-138">Následující příklad kódu nahradí všechny \<popis > elementů s hodnotou \<abstraktní > elementu.</span><span class="sxs-lookup"><span data-stu-id="09472-138">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="09472-139">Obsah \<popis > elementu se zachová, i v novém \<abstraktní > element pomocí <xref:System.Xml.Linq.XContainer.Nodes%2A> vlastnost \<popis > <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="09472-139">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     [!code-vb[VbXmlSamples2#8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]  
  
     <span data-ttu-id="09472-140">Následující ukazuje ukázkový zdroj XML a změnit z tento příklad kódu XML.</span><span class="sxs-lookup"><span data-stu-id="09472-140">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="09472-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="09472-141">See Also</span></span>  
 [<span data-ttu-id="09472-142">Zacházení s XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="09472-142">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 [<span data-ttu-id="09472-143">XML</span><span class="sxs-lookup"><span data-stu-id="09472-143">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="09472-144">Postupy: Načtení XML ze souboru, řetězce nebo streamu</span><span class="sxs-lookup"><span data-stu-id="09472-144">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 [<span data-ttu-id="09472-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="09472-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="09472-146">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="09472-146">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
