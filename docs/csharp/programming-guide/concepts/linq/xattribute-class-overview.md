---
title: XAttribute – Přehled třídy (C#)
description: Atributy jsou páry název-hodnota přidružené k elementu. XAttribute představuje atributy XML. Přečtěte si o práci s atributy v LINQ to XML v jazyce C#.
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 8a19de601041bbb20241c959e909483b97bcf797
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302227"
---
# <a name="xattribute-class-overview-c"></a><span data-ttu-id="93c43-105">XAttribute – Přehled třídy (C#)</span><span class="sxs-lookup"><span data-stu-id="93c43-105">XAttribute Class Overview (C#)</span></span>
<span data-ttu-id="93c43-106">Atributy jsou páry název-hodnota, které jsou přidruženy k elementu.</span><span class="sxs-lookup"><span data-stu-id="93c43-106">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="93c43-107"><xref:System.Xml.Linq.XAttribute>Třída představuje atributy XML.</span><span class="sxs-lookup"><span data-stu-id="93c43-107">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="93c43-108">Přehled</span><span class="sxs-lookup"><span data-stu-id="93c43-108">Overview</span></span>  
 <span data-ttu-id="93c43-109">Práce s atributy v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je podobná práci s prvky.</span><span class="sxs-lookup"><span data-stu-id="93c43-109">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="93c43-110">Jejich konstruktory jsou podobné.</span><span class="sxs-lookup"><span data-stu-id="93c43-110">Their constructors are similar.</span></span> <span data-ttu-id="93c43-111">Metody, které použijete k načtení kolekcí, jsou podobné.</span><span class="sxs-lookup"><span data-stu-id="93c43-111">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="93c43-112">Výraz dotazu LINQ pro kolekci atributů vypadá velmi podobně jako výraz dotazu LINQ pro kolekci prvků.</span><span class="sxs-lookup"><span data-stu-id="93c43-112">A LINQ query expression for a collection of attributes looks very similar to a LINQ query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="93c43-113">Pořadí, ve kterém byly přidány atributy do prvku, je zachováno.</span><span class="sxs-lookup"><span data-stu-id="93c43-113">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="93c43-114">To znamená, že při iteraci pomocí atributů se zobrazí ve stejném pořadí, v jakém byly přidány.</span><span class="sxs-lookup"><span data-stu-id="93c43-114">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="93c43-115">Konstruktor XAttribute</span><span class="sxs-lookup"><span data-stu-id="93c43-115">The XAttribute Constructor</span></span>  
 <span data-ttu-id="93c43-116">Následující konstruktor <xref:System.Xml.Linq.XAttribute> třídy je ten, který se nejčastěji používá:</span><span class="sxs-lookup"><span data-stu-id="93c43-116">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="93c43-117">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="93c43-117">Constructor</span></span>|<span data-ttu-id="93c43-118">Popis</span><span class="sxs-lookup"><span data-stu-id="93c43-118">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="93c43-119">Vytvoří objekt <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="93c43-119">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="93c43-120">`name`Argument určuje název atributu; `content` určuje obsah atributu.</span><span class="sxs-lookup"><span data-stu-id="93c43-120">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="93c43-121">Vytvoření elementu s atributem</span><span class="sxs-lookup"><span data-stu-id="93c43-121">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="93c43-122">Následující kód ukazuje běžný úkol při vytváření prvku, který obsahuje atribut:</span><span class="sxs-lookup"><span data-stu-id="93c43-122">The following code shows the common task of creating an element that contains an attribute:</span></span>  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="93c43-123">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="93c43-123">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="93c43-124">Funkční konstrukce atributů</span><span class="sxs-lookup"><span data-stu-id="93c43-124">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="93c43-125">Objekty lze vytvořit <xref:System.Xml.Linq.XAttribute> v řádku pomocí konstrukce <xref:System.Xml.Linq.XElement> objektů, a to následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="93c43-125">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
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
  
 <span data-ttu-id="93c43-126">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="93c43-126">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="93c43-127">Atributy nejsou uzly.</span><span class="sxs-lookup"><span data-stu-id="93c43-127">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="93c43-128">Mezi atributy a elementy existují rozdíly.</span><span class="sxs-lookup"><span data-stu-id="93c43-128">There are some differences between attributes and elements.</span></span> <span data-ttu-id="93c43-129"><xref:System.Xml.Linq.XAttribute>objekty nejsou uzly ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="93c43-129"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="93c43-130">Jsou to páry název-hodnota přidružené k elementu XML.</span><span class="sxs-lookup"><span data-stu-id="93c43-130">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="93c43-131">Na rozdíl od model DOM (Document Object Model) (DOM) to přesněji odráží strukturu XML.</span><span class="sxs-lookup"><span data-stu-id="93c43-131">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="93c43-132">Přestože <xref:System.Xml.Linq.XAttribute> objekty nejsou ve skutečnosti uzly ve stromu XML, práce s <xref:System.Xml.Linq.XAttribute> objekty je velmi podobná práci s <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="93c43-132">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="93c43-133">Toto rozlišení je primárně důležité pouze pro vývojáře, kteří píší kód, který pracuje s stromy XML na úrovni uzlu.</span><span class="sxs-lookup"><span data-stu-id="93c43-133">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="93c43-134">Toto rozlišení se netýká mnoha vývojářů.</span><span class="sxs-lookup"><span data-stu-id="93c43-134">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93c43-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93c43-135">See also</span></span>

- [<span data-ttu-id="93c43-136">Přehled programování LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="93c43-136">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
