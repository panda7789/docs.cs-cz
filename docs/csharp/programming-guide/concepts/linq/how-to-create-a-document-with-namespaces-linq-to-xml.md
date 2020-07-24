---
title: Postup vytvoření dokumentu s obory názvů (C#) (LINQ to XML)
description: Naučte se, jak vytvořit dokument s oborem názvů v LINQ to XML v jazyce C# pomocí objektu XNamespace pro kombinování oboru názvů s místním názvem.
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 6472baefc73285af1c6dca0bfe7d874003940fc4
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103399"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a><span data-ttu-id="5adfc-103">Postup vytvoření dokumentu s obory názvů (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5adfc-103">How to create a document with namespaces (C#) (LINQ to XML)</span></span>
<span data-ttu-id="5adfc-104">V tomto tématu se dozvíte, jak vytvářet dokumenty s obory názvů.</span><span class="sxs-lookup"><span data-stu-id="5adfc-104">This topic shows how to create documents with namespaces.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5adfc-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="5adfc-105">Example</span></span>  
 <span data-ttu-id="5adfc-106">Chcete-li vytvořit element nebo atribut, který je v oboru názvů, nejprve deklarujete a inicializujete <xref:System.Xml.Linq.XNamespace> objekt.</span><span class="sxs-lookup"><span data-stu-id="5adfc-106">To create an element or an attribute that is in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="5adfc-107">Pak použijte přetížení operátoru sčítání ke kombinování oboru názvů s místním názvem vyjádřeným jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="5adfc-107">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>  
  
 <span data-ttu-id="5adfc-108">Následující příklad vytvoří dokument s jedním oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="5adfc-108">The following example creates a document with one namespace.</span></span> <span data-ttu-id="5adfc-109">Ve výchozím nastavení [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Tento dokument zaserializace s výchozím oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="5adfc-109">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializes this document with a default namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="5adfc-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5adfc-110">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="5adfc-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="5adfc-111">Example</span></span>  
 <span data-ttu-id="5adfc-112">Následující příklad vytvoří dokument s jedním oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="5adfc-112">The following example creates a document with one namespace.</span></span> <span data-ttu-id="5adfc-113">Vytvoří také atribut, který deklaruje obor názvů s předponou oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5adfc-113">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="5adfc-114">Chcete-li vytvořit atribut, který deklaruje obor názvů s předponou, vytvoříte atribut, kde název atributu je předpona oboru názvů a tento název je v <xref:System.Xml.Linq.XNamespace.Xmlns%2A> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5adfc-114">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="5adfc-115">Hodnota tohoto atributu je identifikátor URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5adfc-115">The value of this attribute is the URI of the namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="5adfc-116">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5adfc-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="5adfc-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="5adfc-117">Example</span></span>  
 <span data-ttu-id="5adfc-118">Následující příklad ukazuje vytvoření dokumentu, který obsahuje dva obory názvů.</span><span class="sxs-lookup"><span data-stu-id="5adfc-118">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="5adfc-119">Jedním z nich je výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="5adfc-119">One is the default namespace.</span></span> <span data-ttu-id="5adfc-120">Další je obor názvů s předponou.</span><span class="sxs-lookup"><span data-stu-id="5adfc-120">Another is a namespace with a prefix.</span></span>  
  
 <span data-ttu-id="5adfc-121">Zahrnutím atributů oboru názvů do kořenového elementu jsou obory názvů serializovány, což `http://www.adventure-works.com` je výchozí obor názvů a `www.fourthcoffee.com` je serializován s předponou "FC".</span><span class="sxs-lookup"><span data-stu-id="5adfc-121">By including namespace attributes in the root element, the namespaces are serialized so that `http://www.adventure-works.com` is the default namespace, and `www.fourthcoffee.com` is serialized with a prefix of "fc".</span></span> <span data-ttu-id="5adfc-122">Chcete-li vytvořit atribut, který deklaruje výchozí obor názvů, vytvoříte atribut s názvem "xmlns" bez oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5adfc-122">To create an attribute that declares a default namespace, you create an attribute with the name "xmlns", without a namespace.</span></span> <span data-ttu-id="5adfc-123">Hodnota atributu je výchozí identifikátor URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5adfc-123">The value of the attribute is the default namespace URI.</span></span>  
  
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
  
 <span data-ttu-id="5adfc-124">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5adfc-124">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="5adfc-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="5adfc-125">Example</span></span>  
 <span data-ttu-id="5adfc-126">Následující příklad vytvoří dokument, který obsahuje dva obory názvů, s předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5adfc-126">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>  
  
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
  
 <span data-ttu-id="5adfc-127">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5adfc-127">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="5adfc-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="5adfc-128">Example</span></span>  
 <span data-ttu-id="5adfc-129">Dalším způsobem, jak dosáhnout stejného výsledku, je použít místo deklarace a vytvoření objektu rozšířené názvy <xref:System.Xml.Linq.XNamespace> .</span><span class="sxs-lookup"><span data-stu-id="5adfc-129">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>  
  
 <span data-ttu-id="5adfc-130">Tento přístup má vliv na výkon.</span><span class="sxs-lookup"><span data-stu-id="5adfc-130">This approach has performance implications.</span></span> <span data-ttu-id="5adfc-131">Pokaždé, když předáte řetězec, který obsahuje rozbalený název [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] musí analyzovat název, najít atomické obor názvů a najít název Atom.</span><span class="sxs-lookup"><span data-stu-id="5adfc-131">Each time you pass a string that contains an expanded name to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="5adfc-132">Tento proces trvá čas procesoru.</span><span class="sxs-lookup"><span data-stu-id="5adfc-132">This process takes CPU time.</span></span> <span data-ttu-id="5adfc-133">Pokud je důležitý výkon, možná budete chtít explicitně deklarovat a použít <xref:System.Xml.Linq.XNamespace> objekt.</span><span class="sxs-lookup"><span data-stu-id="5adfc-133">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>  
  
 <span data-ttu-id="5adfc-134">Pokud je výkon důležitý, přečtěte si téma [předběžného vystavování objektů XName (LINQ to XML) (C#)](./pre-atomization-of-xname-objects-linq-to-xml.md) , kde najdete další informace.</span><span class="sxs-lookup"><span data-stu-id="5adfc-134">If performance is an important issue, see [Pre-Atomization of XName Objects (LINQ to XML) (C#)](./pre-atomization-of-xname-objects-linq-to-xml.md) for more information</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="5adfc-135">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5adfc-135">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5adfc-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="5adfc-136">See also</span></span>

- [<span data-ttu-id="5adfc-137">Přehled oborů názvů (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5adfc-137">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
