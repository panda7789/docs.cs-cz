---
title: "Přehled třídy XAttribute (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e9cfedb476f44ef8c3eaeb45bac571d17802d525
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="xattribute-class-overview-c"></a><span data-ttu-id="861e5-102">Přehled třídy XAttribute (C#)</span><span class="sxs-lookup"><span data-stu-id="861e5-102">XAttribute Class Overview (C#)</span></span>
<span data-ttu-id="861e5-103">Atributy jsou páry název/hodnota, které jsou spojeny s elementem.</span><span class="sxs-lookup"><span data-stu-id="861e5-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="861e5-104"><xref:System.Xml.Linq.XAttribute> Třída reprezentuje atributy XML.</span><span class="sxs-lookup"><span data-stu-id="861e5-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="861e5-105">Přehled</span><span class="sxs-lookup"><span data-stu-id="861e5-105">Overview</span></span>  
 <span data-ttu-id="861e5-106">Práce s atributy v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je podobná práci s elementy.</span><span class="sxs-lookup"><span data-stu-id="861e5-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="861e5-107">Jejich konstruktory jsou podobné.</span><span class="sxs-lookup"><span data-stu-id="861e5-107">Their constructors are similar.</span></span> <span data-ttu-id="861e5-108">Metody, které můžete použít k načtení kolekce z nich jsou podobné.</span><span class="sxs-lookup"><span data-stu-id="861e5-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="861e5-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výraz dotazu pro sadu atributů vypadá velmi podobné [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz výraz pro kolekci elementů.</span><span class="sxs-lookup"><span data-stu-id="861e5-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of attributes looks very similar to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="861e5-110">Pořadí, ve kterém byly přidány atributy pro element je zachovaná.</span><span class="sxs-lookup"><span data-stu-id="861e5-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="861e5-111">To znamená pokud iteraci atributy, uvidíte je ve stejném pořadí, v jakém byly přidány.</span><span class="sxs-lookup"><span data-stu-id="861e5-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="861e5-112">Konstruktor XAttribute</span><span class="sxs-lookup"><span data-stu-id="861e5-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="861e5-113">Následující konstruktoru <xref:System.Xml.Linq.XAttribute> třída je ten, který nejčastěji budete používat:</span><span class="sxs-lookup"><span data-stu-id="861e5-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="861e5-114">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="861e5-114">Constructor</span></span>|<span data-ttu-id="861e5-115">Popis</span><span class="sxs-lookup"><span data-stu-id="861e5-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="861e5-116">Vytvoří <xref:System.Xml.Linq.XAttribute> objektu.</span><span class="sxs-lookup"><span data-stu-id="861e5-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="861e5-117">`name` Argument určuje název atributu. `content` určuje obsah atributu.</span><span class="sxs-lookup"><span data-stu-id="861e5-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="861e5-118">Vytváření Element s atributem</span><span class="sxs-lookup"><span data-stu-id="861e5-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="861e5-119">Následující kód ukazuje běžné úlohy vytvoření elementu, který obsahuje atribut:</span><span class="sxs-lookup"><span data-stu-id="861e5-119">The following code shows the common task of creating an element that contains an attribute:</span></span>  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="861e5-120">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="861e5-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="861e5-121">Funkční konstrukce atributů</span><span class="sxs-lookup"><span data-stu-id="861e5-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="861e5-122">Můžete vytvořit <xref:System.Xml.Linq.XAttribute> objekty v řádku s konstrukce <xref:System.Xml.Linq.XElement> objekty, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="861e5-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
```csharp  
XElement c = new XElement("Customers",  
    new XElement("Customer",  
        new XElement("Name", "John Doe"),  
        new XElement("PhoneNumbers",  
            new XElement("Phone",  
                new XAttribute("type", "home"),  
                "555-555-5555"),  
            new XElement("Phone",  
                new XAttribute("type", "work"),  
                "666-666-6666")  
        )  
    )  
);  
Console.WriteLine(c);  
```  
  
 <span data-ttu-id="861e5-123">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="861e5-123">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="861e5-124">Atributy nejsou uzly</span><span class="sxs-lookup"><span data-stu-id="861e5-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="861e5-125">Existují určité rozdíly mezi atributy a elementy.</span><span class="sxs-lookup"><span data-stu-id="861e5-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="861e5-126"><xref:System.Xml.Linq.XAttribute>objekty nejsou uzly ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="861e5-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="861e5-127">Jsou páry název/hodnota, které jsou spojené s elementem XML.</span><span class="sxs-lookup"><span data-stu-id="861e5-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="861e5-128">Na rozdíl od modelu DOM (Document Object), tím přesněji odráží strukturu XML.</span><span class="sxs-lookup"><span data-stu-id="861e5-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="861e5-129">I když <xref:System.Xml.Linq.XAttribute> objekty nejsou ve skutečnosti uzly ve stromové struktuře XML, práce s <xref:System.Xml.Linq.XAttribute> je velmi podobný práce s objekty <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="861e5-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="861e5-130">Tento rozdíl je primárně důležitý pouze pro vývojáře, kteří jsou psaní kódu, který funguje s stromy XML na úrovni uzlu.</span><span class="sxs-lookup"><span data-stu-id="861e5-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="861e5-131">Celá řada vývojářů nebude na těchto rozdílech nevadí.</span><span class="sxs-lookup"><span data-stu-id="861e5-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="861e5-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="861e5-132">See Also</span></span>  
 [<span data-ttu-id="861e5-133">Technologie LINQ to XML přehled programování (C#)</span><span class="sxs-lookup"><span data-stu-id="861e5-133">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
