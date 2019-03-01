---
title: 'Postupy: Změna literálů XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 6e11c1ed4cfe4edc1c88dbbff2e9f555b1a028c4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974715"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="34ffc-102">Postupy: Změna literálů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34ffc-102">How to: Modify XML Literals (Visual Basic)</span></span>
<span data-ttu-id="34ffc-103">Visual Basic poskytuje pohodlný způsob změna literálů XML.</span><span class="sxs-lookup"><span data-stu-id="34ffc-103">Visual Basic provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="34ffc-104">Můžete přidat nebo odstranit elementy a atributy, a můžete také nahradit existující prvek nový prvek XML.</span><span class="sxs-lookup"><span data-stu-id="34ffc-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="34ffc-105">Toto téma obsahuje několik příkladů toho, jak změnit existující literálu XML.</span><span class="sxs-lookup"><span data-stu-id="34ffc-105">This topic provides several examples of how to modify an existing XML literal.</span></span>  
  
### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="34ffc-106">Chcete-li změnit hodnotu literál XML</span><span class="sxs-lookup"><span data-stu-id="34ffc-106">To modify the value of an XML literal</span></span>  
  
1.  <span data-ttu-id="34ffc-107">Chcete-li změnit hodnotu literál XML, získat odkaz na XML literál a nastavte `Value` vlastnost na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="34ffc-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>  
  
     <span data-ttu-id="34ffc-108">Následující příklad kódu aktualizuje hodnotu všech \<cena > elementy v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="34ffc-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>  
  
     [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]  
  
     <span data-ttu-id="34ffc-109">Následující znázorňuje vzorový zdroj XML a změnit tento příklad kódu XML.</span><span class="sxs-lookup"><span data-stu-id="34ffc-109">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
    >  <span data-ttu-id="34ffc-110">`Value` Vlastnost odkazuje na první prvek XML v kolekci.</span><span class="sxs-lookup"><span data-stu-id="34ffc-110">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="34ffc-111">Pokud existuje více než jeden element, který má stejný název v kolekci, nastavení `Value` vlastnost ovlivňuje pouze první prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="34ffc-111">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>  
  
### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="34ffc-112">Chcete-li přidat atribut literál XML</span><span class="sxs-lookup"><span data-stu-id="34ffc-112">To add an attribute to an XML literal</span></span>  
  
1.  <span data-ttu-id="34ffc-113">Pokud chcete přidat atribut literálu XML, nejprve získejte odkaz na literál XML.</span><span class="sxs-lookup"><span data-stu-id="34ffc-113">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="34ffc-114">Potom můžete přidat atribut tak, že přidáte novou vlastnost osy atributu XML.</span><span class="sxs-lookup"><span data-stu-id="34ffc-114">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="34ffc-115">Můžete také přidat nový <xref:System.Xml.Linq.XAttribute> objekt pomocí literálů XML <xref:System.Xml.Linq.XContainer.Add%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="34ffc-115">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="34ffc-116">Následující příklad ukazuje obě možnosti.</span><span class="sxs-lookup"><span data-stu-id="34ffc-116">The following example shows both options.</span></span>  
  
     [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]  
  
     <span data-ttu-id="34ffc-117">Následující znázorňuje vzorový zdroj XML a změnit tento příklad kódu XML.</span><span class="sxs-lookup"><span data-stu-id="34ffc-117">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
     <span data-ttu-id="34ffc-118">Další informace o vlastnosti osy atributu XML, naleznete v tématu [vlastnost osy atributu XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span><span class="sxs-lookup"><span data-stu-id="34ffc-118">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>  
  
### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="34ffc-119">Chcete-li přidat prvek literál XML</span><span class="sxs-lookup"><span data-stu-id="34ffc-119">To add an element to an XML literal</span></span>  
  
1.  <span data-ttu-id="34ffc-120">Chcete-li přidat element do literálů XML, nejprve získejte odkaz na literál XML.</span><span class="sxs-lookup"><span data-stu-id="34ffc-120">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="34ffc-121">Poté můžete přidat nový <xref:System.Xml.Linq.XElement> objektu jako poslední dílčí element elementu s použitím <xref:System.Xml.Linq.XContainer.Add%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="34ffc-121">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="34ffc-122">Můžete přidat nový <xref:System.Xml.Linq.XElement> objekt jako první dílčí element s použitím <xref:System.Xml.Linq.XContainer.AddFirst%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="34ffc-122">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>  
  
     <span data-ttu-id="34ffc-123">Chcete-li přidat nový prvek v konkrétním umístění vzhledem k další dílčí prvky, nejprve získejte odkaz na sousední dílčí element.</span><span class="sxs-lookup"><span data-stu-id="34ffc-123">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="34ffc-124">Poté můžete přidat nové <xref:System.Xml.Linq.XElement> objektu před sousední dílčí element s použitím <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="34ffc-124">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="34ffc-125">Můžete také přidat nové <xref:System.Xml.Linq.XElement> objektu po sousední dílčí element s použitím <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="34ffc-125">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>  
  
     <span data-ttu-id="34ffc-126">Následující příklad ukazuje příklady každého z následujících postupů.</span><span class="sxs-lookup"><span data-stu-id="34ffc-126">The following example shows examples of each of these techniques.</span></span>  
  
     [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]  
  
     <span data-ttu-id="34ffc-127">Následující znázorňuje vzorový zdroj XML a změnit tento příklad kódu XML.</span><span class="sxs-lookup"><span data-stu-id="34ffc-127">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="34ffc-128">K odebrání literál XML elementu nebo atributu</span><span class="sxs-lookup"><span data-stu-id="34ffc-128">To remove an element or attribute from an XML literal</span></span>  
  
1.  <span data-ttu-id="34ffc-129">Chcete-li odebrat ze literál XML elementu nebo atributu, získat odkaz na element nebo atribut a volání `Remove` způsob, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="34ffc-129">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>  
  
     [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]  
  
     <span data-ttu-id="34ffc-130">Následující znázorňuje vzorový zdroj XML a změnit tento příklad kódu XML.</span><span class="sxs-lookup"><span data-stu-id="34ffc-130">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
     <span data-ttu-id="34ffc-131">Pokud chcete odebrat všechny elementy nebo atributy ze literál XML, získejte odkaz na literál XML a volat <xref:System.Xml.Linq.XElement.RemoveAll%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="34ffc-131">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>  
  
### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="34ffc-132">Chcete-li změnit literál XML</span><span class="sxs-lookup"><span data-stu-id="34ffc-132">To modify an XML literal</span></span>  
  
1.  <span data-ttu-id="34ffc-133">Chcete-li změnit název elementu XML, nejprve získejte odkaz na element.</span><span class="sxs-lookup"><span data-stu-id="34ffc-133">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="34ffc-134">Potom můžete vytvořit nový <xref:System.Xml.Linq.XElement> objekt, který se má nový název a předejte nový <xref:System.Xml.Linq.XElement> objektu <xref:System.Xml.Linq.XNode.ReplaceWith%2A> metoda existující <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="34ffc-134">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     <span data-ttu-id="34ffc-135">Pokud má element, který chcete nahradit dílčím prvkům, které musí být zachovány, nastavte hodnotu nového <xref:System.Xml.Linq.XElement> objektu <xref:System.Xml.Linq.XContainer.Nodes%2A> vlastnosti existujícího elementu.</span><span class="sxs-lookup"><span data-stu-id="34ffc-135">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="34ffc-136">To se nastavit hodnotu nového elementu na vnitřní XML z existujícího elementu.</span><span class="sxs-lookup"><span data-stu-id="34ffc-136">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="34ffc-137">V opačném případě můžete nastavit hodnotu nový prvek `Value` vlastnosti existujícího elementu.</span><span class="sxs-lookup"><span data-stu-id="34ffc-137">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>  
  
     <span data-ttu-id="34ffc-138">Následující příklad kódu nahradí všechny \<popis > elementy \<abstraktní > element.</span><span class="sxs-lookup"><span data-stu-id="34ffc-138">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="34ffc-139">Obsah \<popis > element je zachováno v novém \<abstraktní > elementu s použitím <xref:System.Xml.Linq.XContainer.Nodes%2A> vlastnost \<popis > <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="34ffc-139">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]  
  
     <span data-ttu-id="34ffc-140">Následující znázorňuje vzorový zdroj XML a změnit tento příklad kódu XML.</span><span class="sxs-lookup"><span data-stu-id="34ffc-140">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="34ffc-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34ffc-141">See also</span></span>
- [<span data-ttu-id="34ffc-142">Manipulace s kódem XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="34ffc-142">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [<span data-ttu-id="34ffc-143">XML</span><span class="sxs-lookup"><span data-stu-id="34ffc-143">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="34ffc-144">Postupy: Načtení XML ze souboru, řetězce nebo Stream</span><span class="sxs-lookup"><span data-stu-id="34ffc-144">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="34ffc-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="34ffc-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="34ffc-146">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="34ffc-146">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
