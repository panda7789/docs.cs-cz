---
title: XAttribute – Přehled třídyC#()
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 79ef00aa79be0c743423cfba1a911b238ff9a7ca
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590924"
---
# <a name="xattribute-class-overview-c"></a><span data-ttu-id="535c2-102">XAttribute – Přehled třídyC#()</span><span class="sxs-lookup"><span data-stu-id="535c2-102">XAttribute Class Overview (C#)</span></span>
<span data-ttu-id="535c2-103">Atributy jsou páry název-hodnota, které jsou přidruženy k elementu.</span><span class="sxs-lookup"><span data-stu-id="535c2-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="535c2-104"><xref:System.Xml.Linq.XAttribute> Třída představuje atributy XML.</span><span class="sxs-lookup"><span data-stu-id="535c2-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="535c2-105">Přehled</span><span class="sxs-lookup"><span data-stu-id="535c2-105">Overview</span></span>  
 <span data-ttu-id="535c2-106">Práce s atributy v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je podobná práci s prvky.</span><span class="sxs-lookup"><span data-stu-id="535c2-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="535c2-107">Jejich konstruktory jsou podobné.</span><span class="sxs-lookup"><span data-stu-id="535c2-107">Their constructors are similar.</span></span> <span data-ttu-id="535c2-108">Metody, které použijete k načtení kolekcí, jsou podobné.</span><span class="sxs-lookup"><span data-stu-id="535c2-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="535c2-109">Výraz dotazu pro kolekci atributů vypadá velmi podobně jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výraz dotazu pro kolekci prvků. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="535c2-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of attributes looks very similar to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="535c2-110">Pořadí, ve kterém byly přidány atributy do prvku, je zachováno.</span><span class="sxs-lookup"><span data-stu-id="535c2-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="535c2-111">To znamená, že při iteraci pomocí atributů se zobrazí ve stejném pořadí, v jakém byly přidány.</span><span class="sxs-lookup"><span data-stu-id="535c2-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="535c2-112">Konstruktor XAttribute</span><span class="sxs-lookup"><span data-stu-id="535c2-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="535c2-113">Následující konstruktor <xref:System.Xml.Linq.XAttribute> třídy je ten, který se nejčastěji používá:</span><span class="sxs-lookup"><span data-stu-id="535c2-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="535c2-114">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="535c2-114">Constructor</span></span>|<span data-ttu-id="535c2-115">Popis</span><span class="sxs-lookup"><span data-stu-id="535c2-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="535c2-116">Vytvoří <xref:System.Xml.Linq.XAttribute> objektu.</span><span class="sxs-lookup"><span data-stu-id="535c2-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="535c2-117">`name` Argument určuje název atributu; `content` určuje obsah atributu.</span><span class="sxs-lookup"><span data-stu-id="535c2-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="535c2-118">Vytvoření elementu s atributem</span><span class="sxs-lookup"><span data-stu-id="535c2-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="535c2-119">Následující kód ukazuje běžný úkol při vytváření prvku, který obsahuje atribut:</span><span class="sxs-lookup"><span data-stu-id="535c2-119">The following code shows the common task of creating an element that contains an attribute:</span></span>  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="535c2-120">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="535c2-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="535c2-121">Funkční konstrukce atributů</span><span class="sxs-lookup"><span data-stu-id="535c2-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="535c2-122">Objekty lze vytvořit <xref:System.Xml.Linq.XAttribute> v řádku pomocí <xref:System.Xml.Linq.XElement> konstrukce objektů, a to následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="535c2-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
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
  
 <span data-ttu-id="535c2-123">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="535c2-123">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="535c2-124">Atributy nejsou uzly.</span><span class="sxs-lookup"><span data-stu-id="535c2-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="535c2-125">Mezi atributy a elementy existují rozdíly.</span><span class="sxs-lookup"><span data-stu-id="535c2-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="535c2-126"><xref:System.Xml.Linq.XAttribute>objekty nejsou uzly ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="535c2-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="535c2-127">Jsou to páry název-hodnota přidružené k elementu XML.</span><span class="sxs-lookup"><span data-stu-id="535c2-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="535c2-128">Na rozdíl od model DOM (Document Object Model) (DOM) to přesněji odráží strukturu XML.</span><span class="sxs-lookup"><span data-stu-id="535c2-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="535c2-129">Přestože <xref:System.Xml.Linq.XAttribute> objekty nejsou ve skutečnosti uzly ve stromu XML, práce s <xref:System.Xml.Linq.XAttribute> objekty je velmi podobná práci s <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="535c2-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="535c2-130">Toto rozlišení je primárně důležité pouze pro vývojáře, kteří píší kód, který pracuje s stromy XML na úrovni uzlu.</span><span class="sxs-lookup"><span data-stu-id="535c2-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="535c2-131">Toto rozlišení se netýká mnoha vývojářů.</span><span class="sxs-lookup"><span data-stu-id="535c2-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="535c2-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="535c2-132">See also</span></span>

- [<span data-ttu-id="535c2-133">Přehled programování LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="535c2-133">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
