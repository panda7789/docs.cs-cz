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
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="5a6db-102">Postupy: Změna literálů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a6db-102">How to: Modify XML Literals (Visual Basic)</span></span>

<span data-ttu-id="5a6db-103">Visual Basic poskytuje pohodlný způsob, jak upravit literály XML.</span><span class="sxs-lookup"><span data-stu-id="5a6db-103">Visual Basic provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="5a6db-104">Můžete přidat nebo odstranit prvky a atributy a můžete také nahradit existující element novým elementem XML.</span><span class="sxs-lookup"><span data-stu-id="5a6db-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="5a6db-105">Toto téma poskytuje několik příkladů, jak upravit existující literál XML.</span><span class="sxs-lookup"><span data-stu-id="5a6db-105">This topic provides several examples of how to modify an existing XML literal.</span></span>

### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="5a6db-106">Úprava hodnoty literálu XML</span><span class="sxs-lookup"><span data-stu-id="5a6db-106">To modify the value of an XML literal</span></span>

1. <span data-ttu-id="5a6db-107">Chcete-li změnit hodnotu literálu XML, získejte odkaz na literál XML a nastavte `Value` vlastnost na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5a6db-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>

    <span data-ttu-id="5a6db-108">Následující příklad kódu aktualizuje hodnotu všech \<Price> prvků v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="5a6db-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    <span data-ttu-id="5a6db-109">Následující ukázka ukazuje zdrojový kód XML a upravený kód XML z tohoto příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="5a6db-109">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="5a6db-110">Zdrojový kód XML:</span><span class="sxs-lookup"><span data-stu-id="5a6db-110">Source XML:</span></span>

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

    <span data-ttu-id="5a6db-111">Upravený kód XML:</span><span class="sxs-lookup"><span data-stu-id="5a6db-111">Modified XML:</span></span>

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
    > <span data-ttu-id="5a6db-112">`Value`Vlastnost odkazuje na první prvek XML v kolekci.</span><span class="sxs-lookup"><span data-stu-id="5a6db-112">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="5a6db-113">Pokud je v kolekci více než jeden prvek, který má stejný název, nastavení `Value` vlastnosti ovlivní pouze první prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="5a6db-113">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>

### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="5a6db-114">Přidání atributu do literálu XML</span><span class="sxs-lookup"><span data-stu-id="5a6db-114">To add an attribute to an XML literal</span></span>

1. <span data-ttu-id="5a6db-115">Chcete-li přidat atribut do literálu XML, nejprve získejte odkaz na literál XML.</span><span class="sxs-lookup"><span data-stu-id="5a6db-115">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="5a6db-116">Pak můžete přidat atribut přidáním nové vlastnosti osa atributu XML.</span><span class="sxs-lookup"><span data-stu-id="5a6db-116">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="5a6db-117"><xref:System.Xml.Linq.XAttribute>Do literálu XML můžete také přidat nový objekt pomocí <xref:System.Xml.Linq.XContainer.Add%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5a6db-117">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="5a6db-118">Následující příklad ukazuje obě možnosti.</span><span class="sxs-lookup"><span data-stu-id="5a6db-118">The following example shows both options.</span></span>

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    <span data-ttu-id="5a6db-119">Následující ukázka ukazuje zdrojový kód XML a upravený kód XML z tohoto příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="5a6db-119">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="5a6db-120">Zdrojový kód XML:</span><span class="sxs-lookup"><span data-stu-id="5a6db-120">Source XML:</span></span>

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

    <span data-ttu-id="5a6db-121">Upravený kód XML:</span><span class="sxs-lookup"><span data-stu-id="5a6db-121">Modified XML:</span></span>

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

    <span data-ttu-id="5a6db-122">Další informace o vlastnostech osy atributu XML naleznete v tématu [Vlastnosti osy atributu XML](../../../language-reference/xml-axis/xml-attribute-axis-property.md).</span><span class="sxs-lookup"><span data-stu-id="5a6db-122">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>

### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="5a6db-123">Přidání elementu do literálu XML</span><span class="sxs-lookup"><span data-stu-id="5a6db-123">To add an element to an XML literal</span></span>

1. <span data-ttu-id="5a6db-124">Chcete-li přidat prvek do literálu XML, nejprve získejte odkaz na literál XML.</span><span class="sxs-lookup"><span data-stu-id="5a6db-124">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="5a6db-125">Pak můžete přidat nový <xref:System.Xml.Linq.XElement> objekt jako poslední dílčí prvek elementu pomocí <xref:System.Xml.Linq.XContainer.Add%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5a6db-125">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="5a6db-126">Můžete přidat nový <xref:System.Xml.Linq.XElement> objekt jako první dílčí prvek pomocí <xref:System.Xml.Linq.XContainer.AddFirst%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5a6db-126">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>

    <span data-ttu-id="5a6db-127">Chcete-li přidat nový prvek v určitém umístění relativně k jiným dílčím prvkům, nejprve získejte odkaz na sousední dílčí prvek.</span><span class="sxs-lookup"><span data-stu-id="5a6db-127">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="5a6db-128">Pak můžete přidat nový <xref:System.Xml.Linq.XElement> objekt před sousední dílčí element pomocí <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5a6db-128">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="5a6db-129">Můžete také přidat nový <xref:System.Xml.Linq.XElement> objekt za sousední dílčí prvek pomocí <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5a6db-129">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>

    <span data-ttu-id="5a6db-130">Následující příklad ukazuje příklady každé z těchto technik.</span><span class="sxs-lookup"><span data-stu-id="5a6db-130">The following example shows examples of each of these techniques.</span></span>

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    <span data-ttu-id="5a6db-131">Následující ukázka ukazuje zdrojový kód XML a upravený kód XML z tohoto příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="5a6db-131">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="5a6db-132">Zdrojový kód XML:</span><span class="sxs-lookup"><span data-stu-id="5a6db-132">Source XML:</span></span>

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

    <span data-ttu-id="5a6db-133">Upravený kód XML:</span><span class="sxs-lookup"><span data-stu-id="5a6db-133">Modified XML:</span></span>

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

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="5a6db-134">Odebrání elementu nebo atributu z literálu XML</span><span class="sxs-lookup"><span data-stu-id="5a6db-134">To remove an element or attribute from an XML literal</span></span>

1. <span data-ttu-id="5a6db-135">Chcete-li odebrat element nebo atribut z literálu XML, získejte odkaz na element nebo atribut a zavolejte `Remove` metodu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5a6db-135">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    <span data-ttu-id="5a6db-136">Následující ukázka ukazuje zdrojový kód XML a upravený kód XML z tohoto příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="5a6db-136">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="5a6db-137">Zdrojový kód XML:</span><span class="sxs-lookup"><span data-stu-id="5a6db-137">Source XML:</span></span>

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

    <span data-ttu-id="5a6db-138">Upravený kód XML:</span><span class="sxs-lookup"><span data-stu-id="5a6db-138">Modified XML:</span></span>

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

    <span data-ttu-id="5a6db-139">Chcete-li odebrat všechny prvky nebo atributy z literálu XML, získejte odkaz na literál XML a zavolejte <xref:System.Xml.Linq.XElement.RemoveAll%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="5a6db-139">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>

### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="5a6db-140">Úprava literálu XML</span><span class="sxs-lookup"><span data-stu-id="5a6db-140">To modify an XML literal</span></span>

1. <span data-ttu-id="5a6db-141">Chcete-li změnit název elementu XML, nejprve získejte odkaz na prvek.</span><span class="sxs-lookup"><span data-stu-id="5a6db-141">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="5a6db-142">Pak můžete vytvořit nový <xref:System.Xml.Linq.XElement> objekt, který má nový název a předat novému <xref:System.Xml.Linq.XElement> objektu <xref:System.Xml.Linq.XNode.ReplaceWith%2A> metodě stávajícího <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="5a6db-142">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>

    <span data-ttu-id="5a6db-143">Pokud element, který chcete nahradit, má dílčí prvky, které musí být zachovány, nastavte hodnotu nového <xref:System.Xml.Linq.XElement> objektu na <xref:System.Xml.Linq.XContainer.Nodes%2A> vlastnost existujícího elementu.</span><span class="sxs-lookup"><span data-stu-id="5a6db-143">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="5a6db-144">Tím se nastaví hodnota nového prvku na vnitřní XML existujícího elementu.</span><span class="sxs-lookup"><span data-stu-id="5a6db-144">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="5a6db-145">V opačném případě můžete nastavit hodnotu nového prvku na `Value` vlastnost existujícího elementu.</span><span class="sxs-lookup"><span data-stu-id="5a6db-145">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>

    <span data-ttu-id="5a6db-146">Následující příklad kódu nahradí všechny \<Description> prvky \<Abstract> elementem.</span><span class="sxs-lookup"><span data-stu-id="5a6db-146">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="5a6db-147">Obsah \<Description> elementu se zachová v novém \<Abstract> elementu pomocí <xref:System.Xml.Linq.XContainer.Nodes%2A> vlastnosti \<Description> <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="5a6db-147">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    <span data-ttu-id="5a6db-148">Následující ukázka ukazuje zdrojový kód XML a upravený kód XML z tohoto příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="5a6db-148">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="5a6db-149">Zdrojový kód XML:</span><span class="sxs-lookup"><span data-stu-id="5a6db-149">Source XML:</span></span>

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

    <span data-ttu-id="5a6db-150">Upravený kód XML:</span><span class="sxs-lookup"><span data-stu-id="5a6db-150">Modified XML:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5a6db-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a6db-151">See also</span></span>

- [<span data-ttu-id="5a6db-152">Zacházení s XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5a6db-152">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
- [<span data-ttu-id="5a6db-153">XML</span><span class="sxs-lookup"><span data-stu-id="5a6db-153">XML</span></span>](index.md)
- [<span data-ttu-id="5a6db-154">Postupy: Načtení XML ze souboru, řetězce nebo proudu</span><span class="sxs-lookup"><span data-stu-id="5a6db-154">How to: Load XML from a File, String, or Stream</span></span>](how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="5a6db-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="5a6db-155">LINQ</span></span>](../linq/index.md)
- [<span data-ttu-id="5a6db-156">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5a6db-156">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
