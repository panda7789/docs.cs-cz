---
title: 'Postupy: Vytvoření dokumentu s obory názvů (C#) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 9277253e885ac27ccb7d98221366d404ce0902e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618526"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a><span data-ttu-id="83958-102">Postupy: Vytvoření dokumentu s obory názvů (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="83958-102">How to: Create a Document with Namespaces (C#) (LINQ to XML)</span></span>
<span data-ttu-id="83958-103">Toto téma ukazuje, jak vytvářet dokumenty s obory názvů.</span><span class="sxs-lookup"><span data-stu-id="83958-103">This topic shows how to create documents with namespaces.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83958-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="83958-104">Example</span></span>  
 <span data-ttu-id="83958-105">Chcete-li vytvořit element nebo atribut, který je v oboru názvů, nejprve deklarujete a inicializujete <xref:System.Xml.Linq.XNamespace> objektu.</span><span class="sxs-lookup"><span data-stu-id="83958-105">To create an element or an attribute that is in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="83958-106">Potom použijte přetížení operátoru sčítání kombinovat obor názvů s místním názvem vyjádřená jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="83958-106">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>  
  
 <span data-ttu-id="83958-107">Následující příklad vytvoří dokument s jeden obor názvů.</span><span class="sxs-lookup"><span data-stu-id="83958-107">The following example creates a document with one namespace.</span></span> <span data-ttu-id="83958-108">Ve výchozím nastavení [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializuje tento dokument s výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="83958-108">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializes this document with a default namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="83958-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="83958-109">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="83958-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="83958-110">Example</span></span>  
 <span data-ttu-id="83958-111">Následující příklad vytvoří dokument s jeden obor názvů.</span><span class="sxs-lookup"><span data-stu-id="83958-111">The following example creates a document with one namespace.</span></span> <span data-ttu-id="83958-112">Vytvoří také atribut, který deklaruje předponu oboru názvů z oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="83958-112">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="83958-113">Chcete-li vytvořit atribut, který deklaruje oboru názvů s předponou, vytvořte atribut kde název atributu je Předpona oboru názvů, a tento název se <xref:System.Xml.Linq.XNamespace.Xmlns%2A> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="83958-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="83958-114">Hodnota tohoto atributu je identifikátor URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="83958-114">The value of this attribute is the URI of the namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="83958-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="83958-115">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="83958-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="83958-116">Example</span></span>  
 <span data-ttu-id="83958-117">Následující příklad ukazuje vytvoření dokumentu, který obsahuje dva obory názvů.</span><span class="sxs-lookup"><span data-stu-id="83958-117">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="83958-118">Jeden je výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="83958-118">One is the default namespace.</span></span> <span data-ttu-id="83958-119">Další je obor názvů s předponou.</span><span class="sxs-lookup"><span data-stu-id="83958-119">Another is a namespace with a prefix.</span></span>  
  
 <span data-ttu-id="83958-120">Zahrnutím atributy oboru názvů v kořenovém prvku serializují obory názvů tak, aby `http://www.adventure-works.com` je výchozí obor názvů a `www.fourthcoffee.com` serializovat s předponou "fc".</span><span class="sxs-lookup"><span data-stu-id="83958-120">By including namespace attributes in the root element, the namespaces are serialized so that `http://www.adventure-works.com` is the default namespace, and `www.fourthcoffee.com` is serialized with a prefix of "fc".</span></span> <span data-ttu-id="83958-121">Chcete-li vytvořit atribut, který deklaruje výchozí obor názvů, vytvořte atribut se názvu "xmlns", bez oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="83958-121">To create an attribute that declares a default namespace, you create an attribute with the name "xmlns", without a namespace.</span></span> <span data-ttu-id="83958-122">Hodnota atributu je výchozí obor názvů identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="83958-122">The value of the attribute is the default namespace URI.</span></span>  
  
```csharp  
// The http://www.adventure-works.com namespace is forced to be the default namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute("xmlns", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="83958-123">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="83958-123">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="83958-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="83958-124">Example</span></span>  
 <span data-ttu-id="83958-125">Následující příklad vytvoří dokument, který obsahuje dva obory názvů, jak u předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="83958-125">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", aw.NamespaceName),  
    new XAttribute(XNamespace.Xmlns + "fc", fc.NamespaceName),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="83958-126">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="83958-126">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="83958-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="83958-127">Example</span></span>  
 <span data-ttu-id="83958-128">Jiný způsob k dosažení stejného výsledku je použít rozšířené názvy namísto deklarování a vytváření <xref:System.Xml.Linq.XNamespace> objektu.</span><span class="sxs-lookup"><span data-stu-id="83958-128">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>  
  
 <span data-ttu-id="83958-129">Tento přístup má vliv na výkon.</span><span class="sxs-lookup"><span data-stu-id="83958-129">This approach has performance implications.</span></span> <span data-ttu-id="83958-130">Pokaždé, když předáte řetězec, který obsahuje rozbalený název má [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] musíte analyzovat název, najít atomizované objekty obor názvů a vyhledání názvu atomizované objekty.</span><span class="sxs-lookup"><span data-stu-id="83958-130">Each time you pass a string that contains an expanded name to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="83958-131">Tento proces trvá čas procesoru.</span><span class="sxs-lookup"><span data-stu-id="83958-131">This process takes CPU time.</span></span> <span data-ttu-id="83958-132">Pokud je důležitý výkon, může být vhodné k deklarování a použití <xref:System.Xml.Linq.XNamespace> objekt explicitně.</span><span class="sxs-lookup"><span data-stu-id="83958-132">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>  
  
 <span data-ttu-id="83958-133">Pokud výkon je důležitý problém, přečtěte si téma [předběžná atomizace XName objektů (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) Další informace</span><span class="sxs-lookup"><span data-stu-id="83958-133">If performance is an important issue, see [Pre-Atomization of XName Objects (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) for more information</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="83958-134">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="83958-134">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="83958-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83958-135">See also</span></span>

- [<span data-ttu-id="83958-136">Práce s názvovými prostory XML (C#)</span><span class="sxs-lookup"><span data-stu-id="83958-136">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
