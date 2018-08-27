---
title: Přehled třídy XAttribute (C#)
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: e0020a8cd8841ef9a35781b534c82db5e15c257f
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934810"
---
# <a name="xattribute-class-overview-c"></a><span data-ttu-id="f8947-102">Přehled třídy XAttribute (C#)</span><span class="sxs-lookup"><span data-stu-id="f8947-102">XAttribute Class Overview (C#)</span></span>
<span data-ttu-id="f8947-103">Atributy jsou páry název/hodnota, které jsou spojeny s elementem.</span><span class="sxs-lookup"><span data-stu-id="f8947-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="f8947-104"><xref:System.Xml.Linq.XAttribute> Třída reprezentuje atributy ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="f8947-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="f8947-105">Přehled</span><span class="sxs-lookup"><span data-stu-id="f8947-105">Overview</span></span>  
 <span data-ttu-id="f8947-106">Práce s atributy v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je podobně jako při práci s prvky.</span><span class="sxs-lookup"><span data-stu-id="f8947-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="f8947-107">Jejich konstruktory jsou podobné.</span><span class="sxs-lookup"><span data-stu-id="f8947-107">Their constructors are similar.</span></span> <span data-ttu-id="f8947-108">Metody, které můžete použít k načtení kolekce z nich jsou podobné.</span><span class="sxs-lookup"><span data-stu-id="f8947-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="f8947-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazu dotazu pro kolekci atributů vypadá podobně jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazu pro kolekci elementů dotazu.</span><span class="sxs-lookup"><span data-stu-id="f8947-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of attributes looks very similar to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="f8947-110">Zachování pořadí, ve kterém byly přidány atributy pro element.</span><span class="sxs-lookup"><span data-stu-id="f8947-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="f8947-111">To znamená když iteraci atributy, uvidíte je ve stejném pořadí, v jakém byly přidány.</span><span class="sxs-lookup"><span data-stu-id="f8947-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="f8947-112">Konstruktor XAttribute</span><span class="sxs-lookup"><span data-stu-id="f8947-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="f8947-113">Následující konstruktor třídy <xref:System.Xml.Linq.XAttribute> třída je ten, který budete používat nejčastěji:</span><span class="sxs-lookup"><span data-stu-id="f8947-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="f8947-114">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="f8947-114">Constructor</span></span>|<span data-ttu-id="f8947-115">Popis</span><span class="sxs-lookup"><span data-stu-id="f8947-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="f8947-116">Vytvoří <xref:System.Xml.Linq.XAttribute> objektu.</span><span class="sxs-lookup"><span data-stu-id="f8947-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="f8947-117">`name` Argument určuje název atributu. `content` určuje obsah atributu.</span><span class="sxs-lookup"><span data-stu-id="f8947-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="f8947-118">Vytvoření elementu s atributem</span><span class="sxs-lookup"><span data-stu-id="f8947-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="f8947-119">Následující kód ukazuje běžné úlohy vytváření element, který obsahuje atribut:</span><span class="sxs-lookup"><span data-stu-id="f8947-119">The following code shows the common task of creating an element that contains an attribute:</span></span>  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="f8947-120">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f8947-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="f8947-121">Funkční konstrukce atributů</span><span class="sxs-lookup"><span data-stu-id="f8947-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="f8947-122">Můžete vytvořit <xref:System.Xml.Linq.XAttribute> objekty v řádku s konstrukci <xref:System.Xml.Linq.XElement> objekty, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f8947-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
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
  
 <span data-ttu-id="f8947-123">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f8947-123">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="f8947-124">Atributy nejsou uzly</span><span class="sxs-lookup"><span data-stu-id="f8947-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="f8947-125">Existuje několik rozdílů mezi elementy a atributy.</span><span class="sxs-lookup"><span data-stu-id="f8947-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="f8947-126"><xref:System.Xml.Linq.XAttribute> objekty nejsou uzlů ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="f8947-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="f8947-127">Jsou páry název/hodnota přidružený platný element XML.</span><span class="sxs-lookup"><span data-stu-id="f8947-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="f8947-128">Na rozdíl od Document Object Model (DOM), to lépe odpovídá struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="f8947-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="f8947-129">I když <xref:System.Xml.Linq.XAttribute> objekty nejsou ve skutečnosti uzlů ve stromu XML, práce s <xref:System.Xml.Linq.XAttribute> je velmi podobně jako při práci s objekty <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="f8947-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="f8947-130">Tento rozdíl je důležité především pouze pro vývojáře, kteří jsou psaní kódu, který funguje s stromů XML na úrovni uzlu.</span><span class="sxs-lookup"><span data-stu-id="f8947-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="f8947-131">Mnoho vývojářů nesmí být obeznámeni s toto rozlišení.</span><span class="sxs-lookup"><span data-stu-id="f8947-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8947-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8947-132">See Also</span></span>  
 [<span data-ttu-id="f8947-133">Přehled LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="f8947-133">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
