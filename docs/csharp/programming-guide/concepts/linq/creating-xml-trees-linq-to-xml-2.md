---
title: Vytváření stromů XML v jazyce C# (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 4fcd0c14970dd4aabe4d51335f9a0a0a991ef019
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335459"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="f6c33-102">Vytváření stromů XML v jazyce C# (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f6c33-102">Creating XML Trees in C# (LINQ to XML)</span></span>
<span data-ttu-id="f6c33-103">Tato část obsahuje informace o vytváření stromů XML v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="f6c33-103">This section provides information about creating XML trees in C#.</span></span>  
  
 <span data-ttu-id="f6c33-104">Informace o používání výsledky dotazů LINQ jako obsah pro <xref:System.Xml.Linq.XElement>, najdete v části [funkční konstrukce (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f6c33-104">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional Construction (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="constructing-elements"></a><span data-ttu-id="f6c33-105">Vytváření elementů</span><span class="sxs-lookup"><span data-stu-id="f6c33-105">Constructing Elements</span></span>  
 <span data-ttu-id="f6c33-106">Signatur <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory umožňují předat obsah elementu nebo atributu jako argumenty pro konstruktor.</span><span class="sxs-lookup"><span data-stu-id="f6c33-106">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="f6c33-107">Protože jeden z konstruktorů přijímá proměnný počet argumentů, které lze předat libovolný počet podřízených prvků.</span><span class="sxs-lookup"><span data-stu-id="f6c33-107">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="f6c33-108">Samozřejmě každý z těchto podřízených elementů může obsahovat vlastní podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="f6c33-108">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="f6c33-109">Pro libovolný element můžete přidat libovolný počet atributů.</span><span class="sxs-lookup"><span data-stu-id="f6c33-109">For any element, you can add any number of attributes.</span></span>  
  
 <span data-ttu-id="f6c33-110">Při přidávání <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement>) nebo <xref:System.Xml.Linq.XAttribute> objekty, pokud se nový obsah nemá nadřazený, jsou objekty jednoduše připojené k stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="f6c33-110">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="f6c33-111">Pokud nový obsah už je nadřazena a je součástí jiného stromu XML, naklonována nový obsah a nově naklonovaný obsah je připojen k stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="f6c33-111">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="f6c33-112">Poslední příklad v tomto tématu ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="f6c33-112">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="f6c33-113">Chcete-li vytvořit `contacts` <xref:System.Xml.Linq.XElement>, můžete použít následující kód:</span><span class="sxs-lookup"><span data-stu-id="f6c33-113">To create a `contacts`<xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>  
  
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
  
 <span data-ttu-id="f6c33-114">Pokud odsazeny správně, kód k vytvoření <xref:System.Xml.Linq.XElement> objekty velmi podobá strukturu základní XML.</span><span class="sxs-lookup"><span data-stu-id="f6c33-114">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>  
  
## <a name="xelement-constructors"></a><span data-ttu-id="f6c33-115">XElement konstruktory</span><span class="sxs-lookup"><span data-stu-id="f6c33-115">XElement Constructors</span></span>  
 <span data-ttu-id="f6c33-116"><xref:System.Xml.Linq.XElement> Třída používá těchto konstruktorů pro tvorbu funkční.</span><span class="sxs-lookup"><span data-stu-id="f6c33-116">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="f6c33-117">Všimněte si, že jsou některé konstruktory pro <xref:System.Xml.Linq.XElement>, ale vzhledem k tomu, že se nepoužívají pro funkční konstrukce zde nejsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="f6c33-117">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they are not used for functional construction they are not listed here.</span></span>  
  
|<span data-ttu-id="f6c33-118">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="f6c33-118">Constructor</span></span>|<span data-ttu-id="f6c33-119">Popis</span><span class="sxs-lookup"><span data-stu-id="f6c33-119">Description</span></span>|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|<span data-ttu-id="f6c33-120">Vytvoří <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="f6c33-120">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="f6c33-121">`name` Parametr určuje název elementu; `content` určuje obsah elementu.</span><span class="sxs-lookup"><span data-stu-id="f6c33-121">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|  
|`XElement(XName name)`|<span data-ttu-id="f6c33-122">Vytvoří <xref:System.Xml.Linq.XElement> s jeho <xref:System.Xml.Linq.XName> inicializována tak, aby zadaný název.</span><span class="sxs-lookup"><span data-stu-id="f6c33-122">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|  
|`XElement(XName name, params object[] content)`|<span data-ttu-id="f6c33-123">Vytvoří <xref:System.Xml.Linq.XElement> s jeho <xref:System.Xml.Linq.XName> inicializována tak, aby zadaný název.</span><span class="sxs-lookup"><span data-stu-id="f6c33-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="f6c33-124">Atributy nebo podřízené elementy jsou vytvořené pomocí obsah seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="f6c33-124">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|  
  
 <span data-ttu-id="f6c33-125">`content` Parametr je velmi flexibilní.</span><span class="sxs-lookup"><span data-stu-id="f6c33-125">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="f6c33-126">Podporuje jakéhokoli typu objektu, který je platný podřízeným <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="f6c33-126">It supports any type of object that is a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="f6c33-127">Pro různé typy objektů předán v tomto parametru platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="f6c33-127">The following rules apply to different types of objects passed in this parameter:</span></span>  
  
-   <span data-ttu-id="f6c33-128">Řetězec se přidá jako textového obsahu.</span><span class="sxs-lookup"><span data-stu-id="f6c33-128">A string is added as text content.</span></span>  
  
-   <span data-ttu-id="f6c33-129"><xref:System.Xml.Linq.XElement> Je přidána jako podřízený element.</span><span class="sxs-lookup"><span data-stu-id="f6c33-129">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>  
  
-   <span data-ttu-id="f6c33-130"><xref:System.Xml.Linq.XAttribute> Se přidá jako atribut.</span><span class="sxs-lookup"><span data-stu-id="f6c33-130">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>  
  
-   <span data-ttu-id="f6c33-131"><xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, Nebo <xref:System.Xml.Linq.XText> je přidána jako podřízený obsah.</span><span class="sxs-lookup"><span data-stu-id="f6c33-131">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>  
  
-   <span data-ttu-id="f6c33-132"><xref:System.Collections.IEnumerable> Je výčet, a tato pravidla jsou použita rekurzivně výsledky.</span><span class="sxs-lookup"><span data-stu-id="f6c33-132">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>  
  
-   <span data-ttu-id="f6c33-133">U ostatních typů jeho `ToString` metoda je volána a výsledek je přidána jako textového obsahu.</span><span class="sxs-lookup"><span data-stu-id="f6c33-133">For any other type, its `ToString` method is called and the result is added as text content.</span></span>  
  
### <a name="creating-an-xelement-with-content"></a><span data-ttu-id="f6c33-134">Vytvoření XElement s obsahem</span><span class="sxs-lookup"><span data-stu-id="f6c33-134">Creating an XElement with Content</span></span>  
 <span data-ttu-id="f6c33-135">Můžete vytvořit <xref:System.Xml.Linq.XElement> obsahující jednoduchý obsah pomocí volání jedné metody.</span><span class="sxs-lookup"><span data-stu-id="f6c33-135">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="f6c33-136">K tomuto účelu určete obsah jako druhý parametr následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f6c33-136">To do this, specify the content as the second parameter, as follows:</span></span>  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="f6c33-137">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f6c33-137">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 <span data-ttu-id="f6c33-138">Jako obsah můžete předat libovolný typ objektu.</span><span class="sxs-lookup"><span data-stu-id="f6c33-138">You can pass any type of object as the content.</span></span> <span data-ttu-id="f6c33-139">Například následující kód vytvoří elementu, který obsahuje plovoucí bodu číslo jako obsah:</span><span class="sxs-lookup"><span data-stu-id="f6c33-139">For example, the following code creates an element that contains a floating point number as content:</span></span>  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="f6c33-140">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f6c33-140">This example produces the following output:</span></span>  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 <span data-ttu-id="f6c33-141">Plovoucí bod je číslo do pole a v předaný konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="f6c33-141">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="f6c33-142">Pevně určené číslo je převedeno na řetězec a použít jako obsah elementu.</span><span class="sxs-lookup"><span data-stu-id="f6c33-142">The boxed number is converted to a string and used as the content of the element.</span></span>  
  
### <a name="creating-an-xelement-with-a-child-element"></a><span data-ttu-id="f6c33-143">Vytvoření XElement s podřízený Element</span><span class="sxs-lookup"><span data-stu-id="f6c33-143">Creating an XElement with a Child Element</span></span>  
 <span data-ttu-id="f6c33-144">Pokud předáte instanci <xref:System.Xml.Linq.XElement> třída obsahu argument konstruktoru vytvoří element s podřízený element:</span><span class="sxs-lookup"><span data-stu-id="f6c33-144">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 <span data-ttu-id="f6c33-145">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f6c33-145">This example produces the following output:</span></span>  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="f6c33-146">Vytvoření XElement s více podřízených elementů</span><span class="sxs-lookup"><span data-stu-id="f6c33-146">Creating an XElement with Multiple Child Elements</span></span>  
 <span data-ttu-id="f6c33-147">Můžete předat za počet <xref:System.Xml.Linq.XElement> objekty pro obsah.</span><span class="sxs-lookup"><span data-stu-id="f6c33-147">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="f6c33-148">Každý z <xref:System.Xml.Linq.XElement> objekty se dodává jako podřízený element.</span><span class="sxs-lookup"><span data-stu-id="f6c33-148">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 <span data-ttu-id="f6c33-149">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f6c33-149">This example produces the following output:</span></span>  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 <span data-ttu-id="f6c33-150">Tím, že rozšíří výše uvedeném příkladu, můžete vytvořit celý strom XML, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f6c33-150">By extending the above example, you can create an entire XML tree, as follows:</span></span>  
  
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
  
 <span data-ttu-id="f6c33-151">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f6c33-151">This example produces the following output:</span></span>  
  
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
  
### <a name="creating-an-empty-element"></a><span data-ttu-id="f6c33-152">Vytvoření prázdného prvku</span><span class="sxs-lookup"><span data-stu-id="f6c33-152">Creating an Empty Element</span></span>  
 <span data-ttu-id="f6c33-153">Chcete-li vytvořit prázdnou <xref:System.Xml.Linq.XElement>, můžete do konstruktoru nepředávejte žádný obsah.</span><span class="sxs-lookup"><span data-stu-id="f6c33-153">To create an empty <xref:System.Xml.Linq.XElement>, you do not pass any content to the constructor.</span></span> <span data-ttu-id="f6c33-154">Následující příklad vytvoří prázdný element:</span><span class="sxs-lookup"><span data-stu-id="f6c33-154">The following example creates an empty element:</span></span>  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="f6c33-155">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f6c33-155">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a><span data-ttu-id="f6c33-156">Připojení vs. Klonování</span><span class="sxs-lookup"><span data-stu-id="f6c33-156">Attaching vs. Cloning</span></span>  
 <span data-ttu-id="f6c33-157">Jak je uvedeno nahoře, při přidávání <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement>) nebo <xref:System.Xml.Linq.XAttribute> objekty, pokud se nový obsah nemá nadřazený, jsou objekty jednoduše připojené k stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="f6c33-157">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="f6c33-158">Pokud nový obsah už je nadřazena a je součástí jiného stromu XML, naklonována nový obsah a nově naklonovaný obsah je připojen k stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="f6c33-158">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
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
```  
  
 <span data-ttu-id="f6c33-159">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f6c33-159">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6c33-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6c33-160">See Also</span></span>  
 [<span data-ttu-id="f6c33-161">Vytváření stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="f6c33-161">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
