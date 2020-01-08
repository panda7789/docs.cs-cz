---
title: XAttribute – Přehled třídyC#()
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 7a806314664c6319fc45cff0dddedbe38027059d
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635662"
---
# <a name="xattribute-class-overview-c"></a><span data-ttu-id="a1f8f-102">XAttribute – Přehled třídyC#()</span><span class="sxs-lookup"><span data-stu-id="a1f8f-102">XAttribute Class Overview (C#)</span></span>
<span data-ttu-id="a1f8f-103">Atributy jsou páry název-hodnota, které jsou přidruženy k elementu.</span><span class="sxs-lookup"><span data-stu-id="a1f8f-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="a1f8f-104">Třída <xref:System.Xml.Linq.XAttribute> představuje atributy XML.</span><span class="sxs-lookup"><span data-stu-id="a1f8f-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="a1f8f-105">Přehled</span><span class="sxs-lookup"><span data-stu-id="a1f8f-105">Overview</span></span>  
 <span data-ttu-id="a1f8f-106">Práce s atributy v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je podobná práci s prvky.</span><span class="sxs-lookup"><span data-stu-id="a1f8f-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="a1f8f-107">Jejich konstruktory jsou podobné.</span><span class="sxs-lookup"><span data-stu-id="a1f8f-107">Their constructors are similar.</span></span> <span data-ttu-id="a1f8f-108">Metody, které použijete k načtení kolekcí, jsou podobné.</span><span class="sxs-lookup"><span data-stu-id="a1f8f-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="a1f8f-109">Výraz dotazu LINQ pro kolekci atributů vypadá velmi podobně jako výraz dotazu LINQ pro kolekci prvků.</span><span class="sxs-lookup"><span data-stu-id="a1f8f-109">A LINQ query expression for a collection of attributes looks very similar to a LINQ query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="a1f8f-110">Pořadí, ve kterém byly přidány atributy do prvku, je zachováno.</span><span class="sxs-lookup"><span data-stu-id="a1f8f-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="a1f8f-111">To znamená, že při iteraci pomocí atributů se zobrazí ve stejném pořadí, v jakém byly přidány.</span><span class="sxs-lookup"><span data-stu-id="a1f8f-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="a1f8f-112">Konstruktor XAttribute</span><span class="sxs-lookup"><span data-stu-id="a1f8f-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="a1f8f-113">Následující konstruktor třídy <xref:System.Xml.Linq.XAttribute> je ten, který se nejčastěji používá:</span><span class="sxs-lookup"><span data-stu-id="a1f8f-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="a1f8f-114">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="a1f8f-114">Constructor</span></span>|<span data-ttu-id="a1f8f-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a1f8f-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="a1f8f-116">Vytvoří <xref:System.Xml.Linq.XAttribute> objektu.</span><span class="sxs-lookup"><span data-stu-id="a1f8f-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="a1f8f-117">Argument `name` Určuje název atributu. `content` určuje obsah atributu.</span><span class="sxs-lookup"><span data-stu-id="a1f8f-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="a1f8f-118">Vytvoření elementu s atributem</span><span class="sxs-lookup"><span data-stu-id="a1f8f-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="a1f8f-119">Následující kód ukazuje běžný úkol při vytváření prvku, který obsahuje atribut:</span><span class="sxs-lookup"><span data-stu-id="a1f8f-119">The following code shows the common task of creating an element that contains an attribute:</span></span>  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="a1f8f-120">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a1f8f-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="a1f8f-121">Funkční konstrukce atributů</span><span class="sxs-lookup"><span data-stu-id="a1f8f-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="a1f8f-122">Objekty <xref:System.Xml.Linq.XAttribute> lze vytvořit v řádku s konstrukcí objektů <xref:System.Xml.Linq.XElement>, a to následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a1f8f-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
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
  
 <span data-ttu-id="a1f8f-123">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a1f8f-123">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="a1f8f-124">Atributy nejsou uzly.</span><span class="sxs-lookup"><span data-stu-id="a1f8f-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="a1f8f-125">Mezi atributy a elementy existují rozdíly.</span><span class="sxs-lookup"><span data-stu-id="a1f8f-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="a1f8f-126"><xref:System.Xml.Linq.XAttribute> objekty nejsou uzly ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="a1f8f-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="a1f8f-127">Jsou to páry název-hodnota přidružené k elementu XML.</span><span class="sxs-lookup"><span data-stu-id="a1f8f-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="a1f8f-128">Na rozdíl od model DOM (Document Object Model) (DOM) to přesněji odráží strukturu XML.</span><span class="sxs-lookup"><span data-stu-id="a1f8f-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="a1f8f-129">I když <xref:System.Xml.Linq.XAttribute> objekty nejsou ve skutečnosti uzly ve stromu XML, práce s objekty <xref:System.Xml.Linq.XAttribute> je velmi podobná práci s objekty <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="a1f8f-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="a1f8f-130">Toto rozlišení je primárně důležité pouze pro vývojáře, kteří píší kód, který pracuje s stromy XML na úrovni uzlu.</span><span class="sxs-lookup"><span data-stu-id="a1f8f-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="a1f8f-131">Toto rozlišení se netýká mnoha vývojářů.</span><span class="sxs-lookup"><span data-stu-id="a1f8f-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1f8f-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1f8f-132">See also</span></span>

- [<span data-ttu-id="a1f8f-133">Přehled programování LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a1f8f-133">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
