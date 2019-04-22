---
title: Přehled třídy XAttribute (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: 6b24f429a69067f6af1a61efe4102a5638db3031
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836113"
---
# <a name="xattribute-class-overview-visual-basic"></a><span data-ttu-id="303d4-102">Přehled třídy XAttribute (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="303d4-102">XAttribute Class Overview (Visual Basic)</span></span>
<span data-ttu-id="303d4-103">Atributy jsou páry název/hodnota, které jsou spojeny s elementem.</span><span class="sxs-lookup"><span data-stu-id="303d4-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="303d4-104"><xref:System.Xml.Linq.XAttribute> Třída reprezentuje atributy ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="303d4-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="303d4-105">Přehled</span><span class="sxs-lookup"><span data-stu-id="303d4-105">Overview</span></span>  
 <span data-ttu-id="303d4-106">Práce s atributy v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je podobně jako při práci s prvky.</span><span class="sxs-lookup"><span data-stu-id="303d4-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="303d4-107">Jejich konstruktory jsou podobné.</span><span class="sxs-lookup"><span data-stu-id="303d4-107">Their constructors are similar.</span></span> <span data-ttu-id="303d4-108">Metody, které můžete použít k načtení kolekce z nich jsou podobné.</span><span class="sxs-lookup"><span data-stu-id="303d4-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="303d4-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazu dotazu pro kolekci atributů vypadá podobně jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazu pro kolekci elementů dotazu.</span><span class="sxs-lookup"><span data-stu-id="303d4-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of attributes looks very similar to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="303d4-110">Zachování pořadí, ve kterém byly přidány atributy pro element.</span><span class="sxs-lookup"><span data-stu-id="303d4-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="303d4-111">To znamená když iteraci atributy, uvidíte je ve stejném pořadí, v jakém byly přidány.</span><span class="sxs-lookup"><span data-stu-id="303d4-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="303d4-112">Konstruktor XAttribute</span><span class="sxs-lookup"><span data-stu-id="303d4-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="303d4-113">Následující konstruktor třídy <xref:System.Xml.Linq.XAttribute> třída je ten, který budete používat nejčastěji:</span><span class="sxs-lookup"><span data-stu-id="303d4-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="303d4-114">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="303d4-114">Constructor</span></span>|<span data-ttu-id="303d4-115">Popis</span><span class="sxs-lookup"><span data-stu-id="303d4-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="303d4-116">Vytvoří <xref:System.Xml.Linq.XAttribute> objektu.</span><span class="sxs-lookup"><span data-stu-id="303d4-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="303d4-117">`name` Argument určuje název atributu. `content` určuje obsah atributu.</span><span class="sxs-lookup"><span data-stu-id="303d4-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="303d4-118">Vytvoření elementu s atributem</span><span class="sxs-lookup"><span data-stu-id="303d4-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="303d4-119">Následující kód ukazuje element, který obsahuje atribut pomocí literálů XML v jazyce Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="303d4-119">The following code shows an element that contains an attribute using XML literals in Visual Basic:</span></span>  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 <span data-ttu-id="303d4-120">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="303d4-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="303d4-121">Funkční konstrukce atributů</span><span class="sxs-lookup"><span data-stu-id="303d4-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="303d4-122">Můžete vytvořit <xref:System.Xml.Linq.XAttribute> objekty v řádku s konstrukci <xref:System.Xml.Linq.XElement> objekty, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="303d4-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
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
  
 <span data-ttu-id="303d4-123">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="303d4-123">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="303d4-124">Atributy nejsou uzly</span><span class="sxs-lookup"><span data-stu-id="303d4-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="303d4-125">Existuje několik rozdílů mezi elementy a atributy.</span><span class="sxs-lookup"><span data-stu-id="303d4-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="303d4-126"><xref:System.Xml.Linq.XAttribute> objekty nejsou uzlů ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="303d4-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="303d4-127">Jsou páry název/hodnota přidružený platný element XML.</span><span class="sxs-lookup"><span data-stu-id="303d4-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="303d4-128">Na rozdíl od Document Object Model (DOM), to lépe odpovídá struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="303d4-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="303d4-129">I když <xref:System.Xml.Linq.XAttribute> objekty nejsou ve skutečnosti uzlů ve stromu XML, práce s <xref:System.Xml.Linq.XAttribute> je velmi podobně jako při práci s objekty <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="303d4-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="303d4-130">Tento rozdíl je důležité především pouze pro vývojáře, kteří jsou psaní kódu, který funguje s stromů XML na úrovni uzlu.</span><span class="sxs-lookup"><span data-stu-id="303d4-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="303d4-131">Mnoho vývojářů nesmí být obeznámeni s toto rozlišení.</span><span class="sxs-lookup"><span data-stu-id="303d4-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="303d4-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="303d4-132">See also</span></span>

- [<span data-ttu-id="303d4-133">Přehled LINQ to XML programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="303d4-133">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
