---
title: Vytváření stromů XML v jazyce C# (LINQ to XML)
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 4794e4fe019b30d8f2acb3eb255bb77ba2f7f290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169542"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="c4e24-102">Vytváření stromů XML v jazyce C# (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c4e24-102">Creating XML trees in C# (LINQ to XML)</span></span>
<span data-ttu-id="c4e24-103">Tato část obsahuje informace o vytváření stromů XML v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="c4e24-103">This section provides information about creating XML trees in C#.</span></span>  
  
 <span data-ttu-id="c4e24-104">Informace o použití výsledků dotazů LINQ jako <xref:System.Xml.Linq.XElement>obsahu pro , naleznete v tématu [funkční konstrukce (LINQ na XML) (C#)](./functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c4e24-104">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="constructing-elements"></a><span data-ttu-id="c4e24-105">Vytváření prvků</span><span class="sxs-lookup"><span data-stu-id="c4e24-105">Constructing elements</span></span>
 <span data-ttu-id="c4e24-106">Podpisy <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory umožňují předat obsah prvku nebo atributjako argumenty konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c4e24-106">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="c4e24-107">Vzhledem k tomu, že jeden z konstruktorů má proměnný počet argumentů, můžete předat libovolný počet podřízených prvků.</span><span class="sxs-lookup"><span data-stu-id="c4e24-107">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="c4e24-108">Samozřejmě, každý z těchto podřízených prvků může obsahovat své vlastní podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="c4e24-108">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="c4e24-109">Pro libovolný prvek můžete přidat libovolný počet atributů.</span><span class="sxs-lookup"><span data-stu-id="c4e24-109">For any element, you can add any number of attributes.</span></span>  
  
 <span data-ttu-id="c4e24-110">Při <xref:System.Xml.Linq.XNode> přidávání <xref:System.Xml.Linq.XElement>(včetně) nebo <xref:System.Xml.Linq.XAttribute> objektů, pokud nový obsah nemá nadřazený obsah, objekty jsou jednoduše připojeny ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="c4e24-110">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="c4e24-111">Pokud je nový obsah již nadřazený a je součástí jiného stromu XML, nový obsah je klonován a nově klonovaný obsah je připojen ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="c4e24-111">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="c4e24-112">Poslední příklad v tomto tématu ukazuje toto.</span><span class="sxs-lookup"><span data-stu-id="c4e24-112">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="c4e24-113">Chcete-li `contacts` <xref:System.Xml.Linq.XElement>vytvořit , můžete použít následující kód:</span><span class="sxs-lookup"><span data-stu-id="c4e24-113">To create a `contacts`<xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>  
  
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
  
 <span data-ttu-id="c4e24-114">Pokud je správně odsazeno, kód pro vytvoření <xref:System.Xml.Linq.XElement> objektů se velmi podobá struktuře podkladového XML.</span><span class="sxs-lookup"><span data-stu-id="c4e24-114">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>  
  
## <a name="xelement-constructors"></a><span data-ttu-id="c4e24-115">Konstruktory XElement</span><span class="sxs-lookup"><span data-stu-id="c4e24-115">XElement constructors</span></span>  
 <span data-ttu-id="c4e24-116">Třída <xref:System.Xml.Linq.XElement> používá následující konstruktory pro funkční konstrukci.</span><span class="sxs-lookup"><span data-stu-id="c4e24-116">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="c4e24-117">Všimněte si, že existují <xref:System.Xml.Linq.XElement>některé další konstruktory pro , ale protože nejsou použity pro funkční konstrukce nejsou uvedeny zde.</span><span class="sxs-lookup"><span data-stu-id="c4e24-117">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they are not used for functional construction they are not listed here.</span></span>  
  
|<span data-ttu-id="c4e24-118">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="c4e24-118">Constructor</span></span>|<span data-ttu-id="c4e24-119">Popis</span><span class="sxs-lookup"><span data-stu-id="c4e24-119">Description</span></span>|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|<span data-ttu-id="c4e24-120">Vytvoří <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="c4e24-120">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="c4e24-121">Parametr `name` určuje název prvku; `content` určuje obsah prvku.</span><span class="sxs-lookup"><span data-stu-id="c4e24-121">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|  
|`XElement(XName name)`|<span data-ttu-id="c4e24-122">Vytvoří <xref:System.Xml.Linq.XElement> s <xref:System.Xml.Linq.XName> jeho inicializována na zadaný název.</span><span class="sxs-lookup"><span data-stu-id="c4e24-122">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|  
|`XElement(XName name, params object[] content)`|<span data-ttu-id="c4e24-123">Vytvoří <xref:System.Xml.Linq.XElement> s <xref:System.Xml.Linq.XName> jeho inicializována na zadaný název.</span><span class="sxs-lookup"><span data-stu-id="c4e24-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="c4e24-124">Atributy nebo podřízené prvky jsou vytvořeny z obsahu seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="c4e24-124">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|  
  
 <span data-ttu-id="c4e24-125">Parametr `content` je velmi flexibilní.</span><span class="sxs-lookup"><span data-stu-id="c4e24-125">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="c4e24-126">Podporuje jakýkoli typ objektu, který je <xref:System.Xml.Linq.XElement>platný podřízený .</span><span class="sxs-lookup"><span data-stu-id="c4e24-126">It supports any type of object that is a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="c4e24-127">Následující pravidla platí pro různé typy objektů předaných v tomto parametru:</span><span class="sxs-lookup"><span data-stu-id="c4e24-127">The following rules apply to different types of objects passed in this parameter:</span></span>  
  
- <span data-ttu-id="c4e24-128">Řetězec je přidán jako textový obsah.</span><span class="sxs-lookup"><span data-stu-id="c4e24-128">A string is added as text content.</span></span>  
  
- <span data-ttu-id="c4e24-129">Je <xref:System.Xml.Linq.XElement> přidán jako podřízený prvek.</span><span class="sxs-lookup"><span data-stu-id="c4e24-129">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>  
  
- <span data-ttu-id="c4e24-130">Je <xref:System.Xml.Linq.XAttribute> přidán jako atribut.</span><span class="sxs-lookup"><span data-stu-id="c4e24-130">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>  
  
- <span data-ttu-id="c4e24-131">A <xref:System.Xml.Linq.XProcessingInstruction> <xref:System.Xml.Linq.XComment>, <xref:System.Xml.Linq.XText> , nebo je přidán jako podřízený obsah.</span><span class="sxs-lookup"><span data-stu-id="c4e24-131">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>  
  
- <span data-ttu-id="c4e24-132">Je <xref:System.Collections.IEnumerable> výčtu a tato pravidla jsou použity rekurzivně na výsledky.</span><span class="sxs-lookup"><span data-stu-id="c4e24-132">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>  
  
- <span data-ttu-id="c4e24-133">Pro jakýkoli jiný `ToString` typ je volána jeho metoda a výsledek je přidán jako textový obsah.</span><span class="sxs-lookup"><span data-stu-id="c4e24-133">For any other type, its `ToString` method is called and the result is added as text content.</span></span>  
  
### <a name="creating-an-xelement-with-content"></a><span data-ttu-id="c4e24-134">Vytvoření prvku XElement s obsahem</span><span class="sxs-lookup"><span data-stu-id="c4e24-134">Creating an XElement with content</span></span>  
 <span data-ttu-id="c4e24-135">Můžete vytvořit, <xref:System.Xml.Linq.XElement> který obsahuje jednoduchý obsah s voláním jedné metody.</span><span class="sxs-lookup"><span data-stu-id="c4e24-135">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="c4e24-136">Chcete-li to provést, zadejte obsah jako druhý parametr takto:</span><span class="sxs-lookup"><span data-stu-id="c4e24-136">To do this, specify the content as the second parameter, as follows:</span></span>  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="c4e24-137">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c4e24-137">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 <span data-ttu-id="c4e24-138">Jako obsah můžete předat libovolný typ objektu.</span><span class="sxs-lookup"><span data-stu-id="c4e24-138">You can pass any type of object as the content.</span></span> <span data-ttu-id="c4e24-139">Například následující kód vytvoří prvek, který obsahuje číslo s plovoucí desetinnou čárkou jako obsah:</span><span class="sxs-lookup"><span data-stu-id="c4e24-139">For example, the following code creates an element that contains a floating point number as content:</span></span>  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="c4e24-140">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c4e24-140">This example produces the following output:</span></span>  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 <span data-ttu-id="c4e24-141">Číslo s plovoucí desetinnou tácem je zabaleno a předáno konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c4e24-141">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="c4e24-142">Zabalené číslo je převedeno na řetězec a použito jako obsah prvku.</span><span class="sxs-lookup"><span data-stu-id="c4e24-142">The boxed number is converted to a string and used as the content of the element.</span></span>  
  
### <a name="creating-an-xelement-with-a-child-element"></a><span data-ttu-id="c4e24-143">Vytvoření prvku XElement s podřízeným prvkem</span><span class="sxs-lookup"><span data-stu-id="c4e24-143">Creating an XElement with a child element</span></span>  
 <span data-ttu-id="c4e24-144">Pokud předáte instanci <xref:System.Xml.Linq.XElement> třídy pro argument obsahu, konstruktor vytvoří prvek s podřízeným elementem:</span><span class="sxs-lookup"><span data-stu-id="c4e24-144">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 <span data-ttu-id="c4e24-145">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c4e24-145">This example produces the following output:</span></span>  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="c4e24-146">Vytvoření prvku XElement s více podřízenými prvky</span><span class="sxs-lookup"><span data-stu-id="c4e24-146">Creating an XElement with multiple child elements</span></span>  
 <span data-ttu-id="c4e24-147">Můžete předat několik <xref:System.Xml.Linq.XElement> objektů pro obsah.</span><span class="sxs-lookup"><span data-stu-id="c4e24-147">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="c4e24-148">Každý z <xref:System.Xml.Linq.XElement> objektů je součástí jako podřízený prvek.</span><span class="sxs-lookup"><span data-stu-id="c4e24-148">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 <span data-ttu-id="c4e24-149">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c4e24-149">This example produces the following output:</span></span>  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 <span data-ttu-id="c4e24-150">Rozšířením výše uvedeného příkladu můžete vytvořit celý strom XML takto:</span><span class="sxs-lookup"><span data-stu-id="c4e24-150">By extending the above example, you can create an entire XML tree, as follows:</span></span>  
  
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
  
 <span data-ttu-id="c4e24-151">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c4e24-151">This example produces the following output:</span></span>  
  
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

### <a name="creating-an-xelement-with-an-xattribute"></a><span data-ttu-id="c4e24-152">Vytvoření prvku XElement s atributem X</span><span class="sxs-lookup"><span data-stu-id="c4e24-152">Creating an XElement with an XAttribute</span></span>
 <span data-ttu-id="c4e24-153">Pokud předáte instanci <xref:System.Xml.Linq.XAttribute> třídy pro argument obsahu, konstruktor vytvoří prvek s atributem:</span><span class="sxs-lookup"><span data-stu-id="c4e24-153">If you pass an instance of the <xref:System.Xml.Linq.XAttribute> class for the content argument, the constructor creates an element with an attribute:</span></span>

```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="c4e24-154">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c4e24-154">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>
```

### <a name="creating-an-empty-element"></a><span data-ttu-id="c4e24-155">Vytvoření prázdného prvku</span><span class="sxs-lookup"><span data-stu-id="c4e24-155">Creating an empty element</span></span>  
 <span data-ttu-id="c4e24-156">Chcete-li <xref:System.Xml.Linq.XElement>vytvořit prázdný , nepředáte žádný obsah konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c4e24-156">To create an empty <xref:System.Xml.Linq.XElement>, you do not pass any content to the constructor.</span></span> <span data-ttu-id="c4e24-157">Následující příklad vytvoří prázdný prvek:</span><span class="sxs-lookup"><span data-stu-id="c4e24-157">The following example creates an empty element:</span></span>  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="c4e24-158">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c4e24-158">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a><span data-ttu-id="c4e24-159">Připojení vs. klonování</span><span class="sxs-lookup"><span data-stu-id="c4e24-159">Attaching vs. cloning</span></span>  
 <span data-ttu-id="c4e24-160">Jak již bylo zmíněno <xref:System.Xml.Linq.XElement>dříve, <xref:System.Xml.Linq.XAttribute> při přidávání <xref:System.Xml.Linq.XNode> (včetně) nebo objektů, pokud nový obsah nemá nadřazený obsah, objekty jsou jednoduše připojeny ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="c4e24-160">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="c4e24-161">Pokud je nový obsah již nadřazený a je součástí jiného stromu XML, nový obsah je klonován a nově klonovaný obsah je připojen ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="c4e24-161">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  

<span data-ttu-id="c4e24-162">Následující příklad ukazuje chování při přidání nadřazeného prvku do stromu a při přidání prvku bez nadřazeného prvku do stromu.</span><span class="sxs-lookup"><span data-stu-id="c4e24-162">The following example demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c4e24-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4e24-163">See also</span></span>

- [<span data-ttu-id="c4e24-164">Vytváření stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c4e24-164">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
