---
title: Jak vytvořit dokument s obory názvů (C#) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 429b0b0b41f2201b983f931e469b25ff406b91ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141335"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a><span data-ttu-id="cd659-102">Jak vytvořit dokument s obory názvů (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="cd659-102">How to create a document with namespaces (C#) (LINQ to XML)</span></span>
<span data-ttu-id="cd659-103">Toto téma ukazuje, jak vytvořit dokumenty pomocí oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="cd659-103">This topic shows how to create documents with namespaces.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd659-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd659-104">Example</span></span>  
 <span data-ttu-id="cd659-105">Chcete-li vytvořit prvek nebo atribut, který je v oboru názvů, nejprve deklarovat a inicializovat <xref:System.Xml.Linq.XNamespace> objekt.</span><span class="sxs-lookup"><span data-stu-id="cd659-105">To create an element or an attribute that is in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="cd659-106">Potom použít přetížení operátoru sčítání kombinovat obor názvů s místním názvem, vyjádřené jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="cd659-106">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>  
  
 <span data-ttu-id="cd659-107">Následující příklad vytvoří dokument s jedním oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="cd659-107">The following example creates a document with one namespace.</span></span> <span data-ttu-id="cd659-108">Ve výchozím [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nastavení serializuje tento dokument s výchozím oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="cd659-108">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializes this document with a default namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="cd659-109">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="cd659-109">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="cd659-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd659-110">Example</span></span>  
 <span data-ttu-id="cd659-111">Následující příklad vytvoří dokument s jedním oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="cd659-111">The following example creates a document with one namespace.</span></span> <span data-ttu-id="cd659-112">Vytvoří také atribut, který deklaruje obor názvů s předponou oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cd659-112">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="cd659-113">Chcete-li vytvořit atribut, který deklaruje obor názvů s předponou, vytvořte atribut, kde název <xref:System.Xml.Linq.XNamespace.Xmlns%2A> atributu je předpona oboru názvů a tento název je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cd659-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="cd659-114">Hodnota tohoto atributu je identifikátor URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cd659-114">The value of this attribute is the URI of the namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="cd659-115">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="cd659-115">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="cd659-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd659-116">Example</span></span>  
 <span data-ttu-id="cd659-117">Následující příklad ukazuje vytvoření dokumentu, který obsahuje dva obory názvů.</span><span class="sxs-lookup"><span data-stu-id="cd659-117">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="cd659-118">Jedním z nich je výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="cd659-118">One is the default namespace.</span></span> <span data-ttu-id="cd659-119">Dalším je obor názvů s předponou.</span><span class="sxs-lookup"><span data-stu-id="cd659-119">Another is a namespace with a prefix.</span></span>  
  
 <span data-ttu-id="cd659-120">Zahrnutím atributů oboru názvů do kořenového prvku jsou `http://www.adventure-works.com` obory názvů serializovány tak, aby se výchozí obor názvů uplatňovaly, a `www.fourthcoffee.com` jsou serializovány s předponou "fc".</span><span class="sxs-lookup"><span data-stu-id="cd659-120">By including namespace attributes in the root element, the namespaces are serialized so that `http://www.adventure-works.com` is the default namespace, and `www.fourthcoffee.com` is serialized with a prefix of "fc".</span></span> <span data-ttu-id="cd659-121">Chcete-li vytvořit atribut, který deklaruje výchozí obor názvů, vytvořte atribut s názvem xmlns bez oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cd659-121">To create an attribute that declares a default namespace, you create an attribute with the name "xmlns", without a namespace.</span></span> <span data-ttu-id="cd659-122">Hodnota atributu je výchozí identifikátor URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cd659-122">The value of the attribute is the default namespace URI.</span></span>  
  
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
  
 <span data-ttu-id="cd659-123">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="cd659-123">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="cd659-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd659-124">Example</span></span>  
 <span data-ttu-id="cd659-125">Následující příklad vytvoří dokument, který obsahuje dva obory názvů, a to jak s předčíslím oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cd659-125">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>  
  
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
  
 <span data-ttu-id="cd659-126">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="cd659-126">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="cd659-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd659-127">Example</span></span>  
 <span data-ttu-id="cd659-128">Dalším způsobem, jak dosáhnout stejného výsledku, je použít <xref:System.Xml.Linq.XNamespace> rozšířené názvy namísto deklarování a vytváření objektu.</span><span class="sxs-lookup"><span data-stu-id="cd659-128">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>  
  
 <span data-ttu-id="cd659-129">Tento přístup má vliv na výkon.</span><span class="sxs-lookup"><span data-stu-id="cd659-129">This approach has performance implications.</span></span> <span data-ttu-id="cd659-130">Pokaždé, když předáte řetězec, který [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obsahuje rozšířený název , musí analyzovat název, najít atomizovaný obor názvů a najít atomizovaný název.</span><span class="sxs-lookup"><span data-stu-id="cd659-130">Each time you pass a string that contains an expanded name to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="cd659-131">Tento proces trvá čas procesoru.</span><span class="sxs-lookup"><span data-stu-id="cd659-131">This process takes CPU time.</span></span> <span data-ttu-id="cd659-132">Pokud je výkon důležitý, můžete explicitně <xref:System.Xml.Linq.XNamespace> deklarovat a používat objekt.</span><span class="sxs-lookup"><span data-stu-id="cd659-132">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>  
  
 <span data-ttu-id="cd659-133">Pokud je výkon důležitý, další informace naleznete [v tématu Pre-Atomization of XName Objects (LINQ to XML) (C#)](./pre-atomization-of-xname-objects-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="cd659-133">If performance is an important issue, see [Pre-Atomization of XName Objects (LINQ to XML) (C#)](./pre-atomization-of-xname-objects-linq-to-xml.md) for more information</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="cd659-134">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="cd659-134">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd659-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd659-135">See also</span></span>

- [<span data-ttu-id="cd659-136">Obory názvů – přehled (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="cd659-136">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
