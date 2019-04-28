---
title: Vytváření stromů XML v jazyce C# (LINQ to XML)
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 3bac7b62d04c9690cdd08d1993b64db33c4e6ab8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702617"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="72044-102">Vytváření stromů XML v jazyce C# (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="72044-102">Creating XML trees in C# (LINQ to XML)</span></span>
<span data-ttu-id="72044-103">Tato část obsahuje informace o vytváření stromů XML v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="72044-103">This section provides information about creating XML trees in C#.</span></span>  
  
 <span data-ttu-id="72044-104">Další informace o použití výsledků dotazů LINQ jako obsah pro <xref:System.Xml.Linq.XElement>, naleznete v tématu [funkční konstrukce (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="72044-104">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional Construction (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="constructing-elements"></a><span data-ttu-id="72044-105">Vytváření elementů</span><span class="sxs-lookup"><span data-stu-id="72044-105">Constructing elements</span></span>
 <span data-ttu-id="72044-106">Podpisy <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory umožňují obsah elementu nebo atributu předat jako argumenty konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="72044-106">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="72044-107">Protože jeden z konstruktorů přebírá proměnný počet argumentů, můžete předat libovolný počet podřízených elementů.</span><span class="sxs-lookup"><span data-stu-id="72044-107">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="72044-108">Samozřejmě každá z těchto podřízených elementů může obsahovat vlastní podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="72044-108">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="72044-109">Pro libovolný element můžete přidat libovolný počet atributů.</span><span class="sxs-lookup"><span data-stu-id="72044-109">For any element, you can add any number of attributes.</span></span>  
  
 <span data-ttu-id="72044-110">Při přidávání <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement>) nebo <xref:System.Xml.Linq.XAttribute> objektů, pokud se nový obsah nemá žádný nadřazený objekt, objekty jsou jednoduše připojené do stromu XML.</span><span class="sxs-lookup"><span data-stu-id="72044-110">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="72044-111">Pokud nový obsah už je nadřazena a je součástí jiného stromu XML, naklonované nový obsah a nově naklonovaného obsahu je připojen ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="72044-111">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="72044-112">V poslední příkladu v tomto tématu ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="72044-112">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="72044-113">Chcete-li vytvořit `contacts` <xref:System.Xml.Linq.XElement>, můžete použít následující kód:</span><span class="sxs-lookup"><span data-stu-id="72044-113">To create a `contacts`<xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>  
  
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
  
 <span data-ttu-id="72044-114">Pokud odsazena správně, kód k vytvoření <xref:System.Xml.Linq.XElement> objekty podobá struktuře základní XML.</span><span class="sxs-lookup"><span data-stu-id="72044-114">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>  
  
## <a name="xelement-constructors"></a><span data-ttu-id="72044-115">Konstruktory XElement</span><span class="sxs-lookup"><span data-stu-id="72044-115">XElement constructors</span></span>  
 <span data-ttu-id="72044-116"><xref:System.Xml.Linq.XElement> Třída používá následující konstruktory pro funkční konstrukce.</span><span class="sxs-lookup"><span data-stu-id="72044-116">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="72044-117">Všimněte si, že jsou některé konstruktory pro <xref:System.Xml.Linq.XElement>, ale vzhledem k tomu, že nejsou použity pro funkční konstrukce, které zde nejsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="72044-117">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they are not used for functional construction they are not listed here.</span></span>  
  
|<span data-ttu-id="72044-118">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="72044-118">Constructor</span></span>|<span data-ttu-id="72044-119">Popis</span><span class="sxs-lookup"><span data-stu-id="72044-119">Description</span></span>|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|<span data-ttu-id="72044-120">Vytvoří <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="72044-120">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="72044-121">`name` Parametr určuje název elementu; `content` určuje obsah elementu.</span><span class="sxs-lookup"><span data-stu-id="72044-121">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|  
|`XElement(XName name)`|<span data-ttu-id="72044-122">Vytvoří <xref:System.Xml.Linq.XElement> s jeho <xref:System.Xml.Linq.XName> inicializovány na zadaný název.</span><span class="sxs-lookup"><span data-stu-id="72044-122">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|  
|`XElement(XName name, params object[] content)`|<span data-ttu-id="72044-123">Vytvoří <xref:System.Xml.Linq.XElement> s jeho <xref:System.Xml.Linq.XName> inicializovány na zadaný název.</span><span class="sxs-lookup"><span data-stu-id="72044-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="72044-124">Atributy a podřízené prvky jsou vytvořeny z obsahu seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="72044-124">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|  
  
 <span data-ttu-id="72044-125">`content` Parametr je velmi flexibilní.</span><span class="sxs-lookup"><span data-stu-id="72044-125">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="72044-126">Podporuje jakýkoli typ objektu, který je platný podřízený <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="72044-126">It supports any type of object that is a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="72044-127">Následující pravidla platí pro různé druhy objektů předaných v tomto parametru:</span><span class="sxs-lookup"><span data-stu-id="72044-127">The following rules apply to different types of objects passed in this parameter:</span></span>  
  
- <span data-ttu-id="72044-128">Řetězec se přidá jako textový obsah.</span><span class="sxs-lookup"><span data-stu-id="72044-128">A string is added as text content.</span></span>  
  
- <span data-ttu-id="72044-129"><xref:System.Xml.Linq.XElement> Je přidán jako podřízený element.</span><span class="sxs-lookup"><span data-stu-id="72044-129">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>  
  
- <span data-ttu-id="72044-130"><xref:System.Xml.Linq.XAttribute> Se přidá jako atribut.</span><span class="sxs-lookup"><span data-stu-id="72044-130">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>  
  
- <span data-ttu-id="72044-131"><xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, Nebo <xref:System.Xml.Linq.XText> je přidán jako podřízený obsah.</span><span class="sxs-lookup"><span data-stu-id="72044-131">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>  
  
- <span data-ttu-id="72044-132"><xref:System.Collections.IEnumerable> Výčtu a tato pravidla jsou aplikována rekurzivně na výsledky.</span><span class="sxs-lookup"><span data-stu-id="72044-132">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>  
  
- <span data-ttu-id="72044-133">Pro jakýkoli jiný typ jeho `ToString` volání metody a výsledek se přidá jako textový obsah.</span><span class="sxs-lookup"><span data-stu-id="72044-133">For any other type, its `ToString` method is called and the result is added as text content.</span></span>  
  
### <a name="creating-an-xelement-with-content"></a><span data-ttu-id="72044-134">Vytváření s obsahem na XElement</span><span class="sxs-lookup"><span data-stu-id="72044-134">Creating an XElement with content</span></span>  
 <span data-ttu-id="72044-135">Můžete vytvořit <xref:System.Xml.Linq.XElement> , který obsahuje jednoduchý obsah pomocí jedné metody volání.</span><span class="sxs-lookup"><span data-stu-id="72044-135">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="72044-136">Chcete-li to provést, určení obsahu jako druhý parametr následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="72044-136">To do this, specify the content as the second parameter, as follows:</span></span>  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="72044-137">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="72044-137">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 <span data-ttu-id="72044-138">Libovolný typ objektu lze předat jako obsah.</span><span class="sxs-lookup"><span data-stu-id="72044-138">You can pass any type of object as the content.</span></span> <span data-ttu-id="72044-139">Například následující kód vytvoří element, který obsahuje plovoucí číslo jako obsah bodu:</span><span class="sxs-lookup"><span data-stu-id="72044-139">For example, the following code creates an element that contains a floating point number as content:</span></span>  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="72044-140">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="72044-140">This example produces the following output:</span></span>  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 <span data-ttu-id="72044-141">Plovoucí desetinná čárka je číslo v poli a předaná do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="72044-141">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="72044-142">Pevně určené číslo je převedeno na řetězec a použít jako obsah elementu.</span><span class="sxs-lookup"><span data-stu-id="72044-142">The boxed number is converted to a string and used as the content of the element.</span></span>  
  
### <a name="creating-an-xelement-with-a-child-element"></a><span data-ttu-id="72044-143">Vytváření s podřízeným elementem na XElement</span><span class="sxs-lookup"><span data-stu-id="72044-143">Creating an XElement with a child element</span></span>  
 <span data-ttu-id="72044-144">Pokud předáte instanci <xref:System.Xml.Linq.XElement> třídy obsahu argument konstruktoru vytvoří element s podřízený element:</span><span class="sxs-lookup"><span data-stu-id="72044-144">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 <span data-ttu-id="72044-145">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="72044-145">This example produces the following output:</span></span>  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="72044-146">Vytváření XElement s více podřízených prvků</span><span class="sxs-lookup"><span data-stu-id="72044-146">Creating an XElement with multiple child elements</span></span>  
 <span data-ttu-id="72044-147">Můžete předat několik <xref:System.Xml.Linq.XElement> objekty pro obsah.</span><span class="sxs-lookup"><span data-stu-id="72044-147">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="72044-148">Každá z <xref:System.Xml.Linq.XElement> objekty je dostupná jako podřízený element.</span><span class="sxs-lookup"><span data-stu-id="72044-148">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 <span data-ttu-id="72044-149">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="72044-149">This example produces the following output:</span></span>  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 <span data-ttu-id="72044-150">Tím, že rozšíří výše uvedeném příkladu, můžete vytvořit celý strom XML následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="72044-150">By extending the above example, you can create an entire XML tree, as follows:</span></span>  
  
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
  
 <span data-ttu-id="72044-151">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="72044-151">This example produces the following output:</span></span>  
  
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

### <a name="creating-an-xelement-with-an-xattribute"></a><span data-ttu-id="72044-152">Vytvoření pomocí XAttribute XElement</span><span class="sxs-lookup"><span data-stu-id="72044-152">Creating an XElement with an XAttribute</span></span>
 <span data-ttu-id="72044-153">Pokud předáte instanci <xref:System.Xml.Linq.XAttribute> třídy obsahu argument konstruktoru vytvoří element se atribut:</span><span class="sxs-lookup"><span data-stu-id="72044-153">If you pass an instance of the <xref:System.Xml.Linq.XAttribute> class for the content argument, the constructor creates an element with an attribute:</span></span>

```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="72044-154">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="72044-154">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>
```   

### <a name="creating-an-empty-element"></a><span data-ttu-id="72044-155">Vytvořit prázdný element</span><span class="sxs-lookup"><span data-stu-id="72044-155">Creating an empty element</span></span>  
 <span data-ttu-id="72044-156">Chcete-li vytvořit prázdnou <xref:System.Xml.Linq.XElement>, konstruktoru nepředáte žádný obsah.</span><span class="sxs-lookup"><span data-stu-id="72044-156">To create an empty <xref:System.Xml.Linq.XElement>, you do not pass any content to the constructor.</span></span> <span data-ttu-id="72044-157">Následující příklad vytvoří prázdný element:</span><span class="sxs-lookup"><span data-stu-id="72044-157">The following example creates an empty element:</span></span>  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="72044-158">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="72044-158">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a><span data-ttu-id="72044-159">Připojení a klonování</span><span class="sxs-lookup"><span data-stu-id="72044-159">Attaching vs. cloning</span></span>  
 <span data-ttu-id="72044-160">Jak už bylo zmíněno dříve, při přidávání <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement>) nebo <xref:System.Xml.Linq.XAttribute> objektů, pokud se nový obsah nemá žádný nadřazený objekt, objekty jsou jednoduše připojené do stromu XML.</span><span class="sxs-lookup"><span data-stu-id="72044-160">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="72044-161">Pokud nový obsah už je nadřazena a je součástí jiného stromu XML, naklonované nový obsah a nově naklonovaného obsahu je připojen ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="72044-161">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  

<span data-ttu-id="72044-162">Následující příklad ukazuje chování při přidávání nadřazeným prvkem elementu do stromu a přidejte element s žádný nadřazený objekt na strom.</span><span class="sxs-lookup"><span data-stu-id="72044-162">The following example demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="72044-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72044-163">See also</span></span>

- [<span data-ttu-id="72044-164">Vytváření stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="72044-164">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
