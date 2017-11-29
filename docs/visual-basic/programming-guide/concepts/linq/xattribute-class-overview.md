---
title: "Přehled XAttribute třídy (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 900f047ec0db8ed1e2399345d2d4c3fba34afd5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="xattribute-class-overview-visual-basic"></a><span data-ttu-id="b65ff-102">Přehled XAttribute třídy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b65ff-102">XAttribute Class Overview (Visual Basic)</span></span>
<span data-ttu-id="b65ff-103">Atributy jsou páry název/hodnota, které jsou spojeny s elementem.</span><span class="sxs-lookup"><span data-stu-id="b65ff-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="b65ff-104"><xref:System.Xml.Linq.XAttribute> Třída reprezentuje atributy XML.</span><span class="sxs-lookup"><span data-stu-id="b65ff-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="b65ff-105">Přehled</span><span class="sxs-lookup"><span data-stu-id="b65ff-105">Overview</span></span>  
 <span data-ttu-id="b65ff-106">Práce s atributy v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je podobná práci s elementy.</span><span class="sxs-lookup"><span data-stu-id="b65ff-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="b65ff-107">Jejich konstruktory jsou podobné.</span><span class="sxs-lookup"><span data-stu-id="b65ff-107">Their constructors are similar.</span></span> <span data-ttu-id="b65ff-108">Metody, které můžete použít k načtení kolekce z nich jsou podobné.</span><span class="sxs-lookup"><span data-stu-id="b65ff-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="b65ff-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výraz dotazu pro sadu atributů vypadá velmi podobné [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz výraz pro kolekci elementů.</span><span class="sxs-lookup"><span data-stu-id="b65ff-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of attributes looks very similar to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="b65ff-110">Pořadí, ve kterém byly přidány atributy pro element je zachovaná.</span><span class="sxs-lookup"><span data-stu-id="b65ff-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="b65ff-111">To znamená pokud iteraci atributy, uvidíte je ve stejném pořadí, v jakém byly přidány.</span><span class="sxs-lookup"><span data-stu-id="b65ff-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="b65ff-112">Konstruktor XAttribute</span><span class="sxs-lookup"><span data-stu-id="b65ff-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="b65ff-113">Následující konstruktoru <xref:System.Xml.Linq.XAttribute> třída je ten, který nejčastěji budete používat:</span><span class="sxs-lookup"><span data-stu-id="b65ff-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="b65ff-114">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="b65ff-114">Constructor</span></span>|<span data-ttu-id="b65ff-115">Popis</span><span class="sxs-lookup"><span data-stu-id="b65ff-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="b65ff-116">Vytvoří <xref:System.Xml.Linq.XAttribute> objektu.</span><span class="sxs-lookup"><span data-stu-id="b65ff-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="b65ff-117">`name` Argument určuje název atributu. `content` určuje obsah atributu.</span><span class="sxs-lookup"><span data-stu-id="b65ff-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="b65ff-118">Vytváření Element s atributem</span><span class="sxs-lookup"><span data-stu-id="b65ff-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="b65ff-119">Následující kód ukazuje elementu, který obsahuje atribut pomocí literálů XML v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="b65ff-119">The following code shows an element that contains an attribute using XML literals in Visual Basic:</span></span>  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 <span data-ttu-id="b65ff-120">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b65ff-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="b65ff-121">Funkční konstrukce atributů</span><span class="sxs-lookup"><span data-stu-id="b65ff-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="b65ff-122">Můžete vytvořit <xref:System.Xml.Linq.XAttribute> objekty v řádku s konstrukce <xref:System.Xml.Linq.XElement> objekty, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b65ff-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
```vb  
Dim c As XElement = _  
    <Customers>  
        <Customer>  
            <Name>John Doe</Name>  
            <PhoneNumbers>  
                <Phone type="home">555-555-5555</Phone>  
                <Phone type="work">666-666-6666</Phone>  
            </PhoneNumbers>  
        </Customer>  
    </Customers>  
Console.WriteLine(c)  
```  
  
 <span data-ttu-id="b65ff-123">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b65ff-123">This example produces the following output:</span></span>  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="b65ff-124">Atributy nejsou uzly</span><span class="sxs-lookup"><span data-stu-id="b65ff-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="b65ff-125">Existují určité rozdíly mezi atributy a elementy.</span><span class="sxs-lookup"><span data-stu-id="b65ff-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="b65ff-126"><xref:System.Xml.Linq.XAttribute>objekty nejsou uzly ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="b65ff-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="b65ff-127">Jsou páry název/hodnota, které jsou spojené s elementem XML.</span><span class="sxs-lookup"><span data-stu-id="b65ff-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="b65ff-128">Na rozdíl od modelu DOM (Document Object), tím přesněji odráží strukturu XML.</span><span class="sxs-lookup"><span data-stu-id="b65ff-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="b65ff-129">I když <xref:System.Xml.Linq.XAttribute> objekty nejsou ve skutečnosti uzly ve stromové struktuře XML, práce s <xref:System.Xml.Linq.XAttribute> je velmi podobný práce s objekty <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="b65ff-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="b65ff-130">Tento rozdíl je primárně důležitý pouze pro vývojáře, kteří jsou psaní kódu, který funguje s stromy XML na úrovni uzlu.</span><span class="sxs-lookup"><span data-stu-id="b65ff-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="b65ff-131">Celá řada vývojářů nebude na těchto rozdílech nevadí.</span><span class="sxs-lookup"><span data-stu-id="b65ff-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b65ff-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="b65ff-132">See Also</span></span>  
 [<span data-ttu-id="b65ff-133">Technologie LINQ to přehled programování v XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b65ff-133">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
