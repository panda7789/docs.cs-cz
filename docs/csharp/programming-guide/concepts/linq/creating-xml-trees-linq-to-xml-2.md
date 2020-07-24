---
title: Vytváření stromů XML v jazyce C# (LINQ to XML)
description: Přečtěte si o vytváření stromů XML v jazyce C#, včetně vytváření prvků a použití konstruktorů XElement.
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 3991f461c4c870a64320853ccd1d45026a8a6bf6
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105477"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="20e91-103">Vytváření stromů XML v jazyce C# (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="20e91-103">Creating XML trees in C# (LINQ to XML)</span></span>
<span data-ttu-id="20e91-104">Tato část poskytuje informace o vytváření stromů XML v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="20e91-104">This section provides information about creating XML trees in C#.</span></span>  
  
 <span data-ttu-id="20e91-105">Informace o použití výsledků dotazů LINQ jako obsahu pro naleznete <xref:System.Xml.Linq.XElement> v tématu [funkční konstrukce (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="20e91-105">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="constructing-elements"></a><span data-ttu-id="20e91-106">Vytváření elementů</span><span class="sxs-lookup"><span data-stu-id="20e91-106">Constructing elements</span></span>
 <span data-ttu-id="20e91-107">Signatury <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> konstruktorů a umožňují předat obsah elementu nebo atributu jako argumenty konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="20e91-107">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="20e91-108">Vzhledem k tomu, že jeden z konstruktorů přebírá proměnný počet argumentů, můžete předat libovolný počet podřízených elementů.</span><span class="sxs-lookup"><span data-stu-id="20e91-108">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="20e91-109">Každý z těchto podřízených elementů samozřejmě může obsahovat vlastní podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="20e91-109">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="20e91-110">Pro libovolný prvek můžete přidat libovolný počet atributů.</span><span class="sxs-lookup"><span data-stu-id="20e91-110">For any element, you can add any number of attributes.</span></span>  
  
 <span data-ttu-id="20e91-111">Při přidávání <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement> ) nebo <xref:System.Xml.Linq.XAttribute> objektů, pokud nový obsah nemá žádný nadřazený objekt, jsou objekty jednoduše připojeny ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="20e91-111">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="20e91-112">Pokud nový obsah již je nadřazený a je součástí jiného stromu XML, bude nový obsah naklonován a nově Klonovaný obsah je připojen ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="20e91-112">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="20e91-113">Příklad ukazuje poslední příklad v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="20e91-113">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="20e91-114">Chcete-li vytvořit `contacts` <xref:System.Xml.Linq.XElement> , můžete použít následující kód:</span><span class="sxs-lookup"><span data-stu-id="20e91-114">To create a `contacts`<xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="20e91-115">Pokud je znak správně odsazený, kód pro sestavování <xref:System.Xml.Linq.XElement> objektů se těsně podobá struktuře podkladového XML.</span><span class="sxs-lookup"><span data-stu-id="20e91-115">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>  
  
## <a name="xelement-constructors"></a><span data-ttu-id="20e91-116">XElement konstruktory</span><span class="sxs-lookup"><span data-stu-id="20e91-116">XElement constructors</span></span>  
 <span data-ttu-id="20e91-117"><xref:System.Xml.Linq.XElement>Třída používá následující konstruktory pro konstrukci funkčnosti.</span><span class="sxs-lookup"><span data-stu-id="20e91-117">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="20e91-118">Všimněte si, že existují další konstruktory pro <xref:System.Xml.Linq.XElement> , ale vzhledem k tomu, že nejsou používány pro funkční konstrukce, nejsou zde uvedeny.</span><span class="sxs-lookup"><span data-stu-id="20e91-118">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they are not used for functional construction they are not listed here.</span></span>  
  
|<span data-ttu-id="20e91-119">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="20e91-119">Constructor</span></span>|<span data-ttu-id="20e91-120">Popis</span><span class="sxs-lookup"><span data-stu-id="20e91-120">Description</span></span>|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|<span data-ttu-id="20e91-121">Vytvoří <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="20e91-121">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="20e91-122">`name`Parametr určuje název elementu; `content` určuje obsah elementu.</span><span class="sxs-lookup"><span data-stu-id="20e91-122">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|  
|`XElement(XName name)`|<span data-ttu-id="20e91-123">Vytvoří <xref:System.Xml.Linq.XElement> s názvem, který <xref:System.Xml.Linq.XName> je inicializován na zadaný název.</span><span class="sxs-lookup"><span data-stu-id="20e91-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|  
|`XElement(XName name, params object[] content)`|<span data-ttu-id="20e91-124">Vytvoří <xref:System.Xml.Linq.XElement> s názvem, který <xref:System.Xml.Linq.XName> je inicializován na zadaný název.</span><span class="sxs-lookup"><span data-stu-id="20e91-124">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="20e91-125">Atributy nebo podřízené prvky jsou vytvořeny z obsahu seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="20e91-125">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|  
  
 <span data-ttu-id="20e91-126">`content`Parametr je velice flexibilní.</span><span class="sxs-lookup"><span data-stu-id="20e91-126">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="20e91-127">Podporuje jakýkoliv typ objektu, který je platným podřízeným prvku <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="20e91-127">It supports any type of object that is a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="20e91-128">Následující pravidla platí pro různé typy objektů předaných v tomto parametru:</span><span class="sxs-lookup"><span data-stu-id="20e91-128">The following rules apply to different types of objects passed in this parameter:</span></span>  
  
- <span data-ttu-id="20e91-129">Řetězec se přidá jako textový obsah.</span><span class="sxs-lookup"><span data-stu-id="20e91-129">A string is added as text content.</span></span>  
  
- <span data-ttu-id="20e91-130"><xref:System.Xml.Linq.XElement>Je přidán jako podřízený element.</span><span class="sxs-lookup"><span data-stu-id="20e91-130">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>  
  
- <span data-ttu-id="20e91-131"><xref:System.Xml.Linq.XAttribute>Přidá se jako atribut.</span><span class="sxs-lookup"><span data-stu-id="20e91-131">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>  
  
- <span data-ttu-id="20e91-132"><xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment> Nebo <xref:System.Xml.Linq.XText> se přidá jako podřízený obsah.</span><span class="sxs-lookup"><span data-stu-id="20e91-132">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>  
  
- <span data-ttu-id="20e91-133"><xref:System.Collections.IEnumerable>Vytvoří se výčet a tato pravidla se rekurzivně aplikují na výsledky.</span><span class="sxs-lookup"><span data-stu-id="20e91-133">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>  
  
- <span data-ttu-id="20e91-134">Pro jakýkoliv jiný typ je jeho `ToString` metoda volána a výsledek je přidán jako textový obsah.</span><span class="sxs-lookup"><span data-stu-id="20e91-134">For any other type, its `ToString` method is called and the result is added as text content.</span></span>  
  
### <a name="creating-an-xelement-with-content"></a><span data-ttu-id="20e91-135">Vytvoření XElement s obsahem</span><span class="sxs-lookup"><span data-stu-id="20e91-135">Creating an XElement with content</span></span>  
 <span data-ttu-id="20e91-136">Můžete vytvořit <xref:System.Xml.Linq.XElement> , který obsahuje jednoduchý obsah s jedinou voláním metody.</span><span class="sxs-lookup"><span data-stu-id="20e91-136">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="20e91-137">Chcete-li to provést, zadejte jako druhý parametr obsah následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="20e91-137">To do this, specify the content as the second parameter, as follows:</span></span>  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="20e91-138">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="20e91-138">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 <span data-ttu-id="20e91-139">Jako obsah můžete předat libovolný typ objektu.</span><span class="sxs-lookup"><span data-stu-id="20e91-139">You can pass any type of object as the content.</span></span> <span data-ttu-id="20e91-140">Například následující kód vytvoří prvek, který obsahuje číslo s plovoucí desetinnou čárkou jako obsah:</span><span class="sxs-lookup"><span data-stu-id="20e91-140">For example, the following code creates an element that contains a floating point number as content:</span></span>  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="20e91-141">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="20e91-141">This example produces the following output:</span></span>  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 <span data-ttu-id="20e91-142">Číslo s plovoucí desetinnou čárkou je v krabici a předáno do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="20e91-142">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="20e91-143">Zabalené číslo je převedeno na řetězec a použito jako obsah elementu.</span><span class="sxs-lookup"><span data-stu-id="20e91-143">The boxed number is converted to a string and used as the content of the element.</span></span>  
  
### <a name="creating-an-xelement-with-a-child-element"></a><span data-ttu-id="20e91-144">Vytvoření XElement s podřízeným elementem</span><span class="sxs-lookup"><span data-stu-id="20e91-144">Creating an XElement with a child element</span></span>  
 <span data-ttu-id="20e91-145">Pokud předáte instanci <xref:System.Xml.Linq.XElement> třídy pro argument obsahu, konstruktor vytvoří prvek s podřízeným elementem:</span><span class="sxs-lookup"><span data-stu-id="20e91-145">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 <span data-ttu-id="20e91-146">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="20e91-146">This example produces the following output:</span></span>  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="20e91-147">Vytvoření XElement s více podřízenými elementy</span><span class="sxs-lookup"><span data-stu-id="20e91-147">Creating an XElement with multiple child elements</span></span>  
 <span data-ttu-id="20e91-148">Pro obsah můžete předat několik <xref:System.Xml.Linq.XElement> objektů.</span><span class="sxs-lookup"><span data-stu-id="20e91-148">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="20e91-149">Každý <xref:System.Xml.Linq.XElement> objekt je zahrnut jako podřízený element.</span><span class="sxs-lookup"><span data-stu-id="20e91-149">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 <span data-ttu-id="20e91-150">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="20e91-150">This example produces the following output:</span></span>  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 <span data-ttu-id="20e91-151">Rozšířením výše uvedeného příkladu můžete vytvořit celý strom XML následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="20e91-151">By extending the above example, you can create an entire XML tree, as follows:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
Console.WriteLine(contacts);  
```  
  
 <span data-ttu-id="20e91-152">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="20e91-152">This example produces the following output:</span></span>  
  
```xml  
<Contacts>  
  <Contact>  
    <Name>Patrick Hines</Name>  
    <Phone>206-555-0144</Phone>  
    <Address>  
      <Street1>123 Main St</Street1>  
      <City>Mercer Island</City>  
      <State>WA</State>  
      <Postal>68042</Postal>  
    </Address>  
  </Contact>  
</Contacts>  
```  

### <a name="creating-an-xelement-with-an-xattribute"></a><span data-ttu-id="20e91-153">Vytvoření XElement pomocí XAttribute</span><span class="sxs-lookup"><span data-stu-id="20e91-153">Creating an XElement with an XAttribute</span></span>
 <span data-ttu-id="20e91-154">Pokud předáte instanci <xref:System.Xml.Linq.XAttribute> třídy pro argument obsahu, konstruktor vytvoří element s atributem:</span><span class="sxs-lookup"><span data-stu-id="20e91-154">If you pass an instance of the <xref:System.Xml.Linq.XAttribute> class for the content argument, the constructor creates an element with an attribute:</span></span>

```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="20e91-155">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="20e91-155">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>
```

### <a name="creating-an-empty-element"></a><span data-ttu-id="20e91-156">Vytvoření prázdného prvku</span><span class="sxs-lookup"><span data-stu-id="20e91-156">Creating an empty element</span></span>  
 <span data-ttu-id="20e91-157">Chcete-li vytvořit prázdnou, nemusíte <xref:System.Xml.Linq.XElement> do konstruktoru předávat žádný obsah.</span><span class="sxs-lookup"><span data-stu-id="20e91-157">To create an empty <xref:System.Xml.Linq.XElement>, you do not pass any content to the constructor.</span></span> <span data-ttu-id="20e91-158">Následující příklad vytvoří prázdný element:</span><span class="sxs-lookup"><span data-stu-id="20e91-158">The following example creates an empty element:</span></span>  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="20e91-159">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="20e91-159">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a><span data-ttu-id="20e91-160">Připojení vs. klonování</span><span class="sxs-lookup"><span data-stu-id="20e91-160">Attaching vs. cloning</span></span>  
 <span data-ttu-id="20e91-161">Jak bylo uvedeno dříve, při přidávání <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement> ) nebo <xref:System.Xml.Linq.XAttribute> objektů, pokud nový obsah nemá žádný nadřazený objekt, objekty jsou jednoduše připojeny ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="20e91-161">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="20e91-162">Pokud je nový obsah již nadřazený a je součástí jiného stromu XML, bude nový obsah klonován a nově Klonovaný obsah je připojen ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="20e91-162">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  

<span data-ttu-id="20e91-163">Následující příklad ukazuje chování při přidání nadřazeného elementu do stromu a při přidání elementu bez nadřazeného prvku do stromu.</span><span class="sxs-lookup"><span data-stu-id="20e91-163">The following example demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>

```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  

// The example displays the following output:  
//    Child1 was cloned  
//    Child2 was attached  
```

## <a name="see-also"></a><span data-ttu-id="20e91-164">Viz také</span><span class="sxs-lookup"><span data-stu-id="20e91-164">See also</span></span>

- [<span data-ttu-id="20e91-165">Vytváření stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="20e91-165">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
