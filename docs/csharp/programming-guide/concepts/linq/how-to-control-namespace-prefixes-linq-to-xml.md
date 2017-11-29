---
title: "Postupy: řízení Namespace předpony (C#) (technologie LINQ to XML)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fc8d652c54be62fdf38e0aa05fcf6a81af3f719b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a><span data-ttu-id="33ca9-102">Postupy: řízení Namespace předpony (C#) (technologie LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="33ca9-102">How to: Control Namespace Prefixes (C#) (LINQ to XML)</span></span>
<span data-ttu-id="33ca9-103">Toto téma popisuje, jak můžete řídit předpony oboru názvů při serializaci strom XML.</span><span class="sxs-lookup"><span data-stu-id="33ca9-103">This topic describes how you can control namespace prefixes when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="33ca9-104">V mnoha situacích není potřeba řídit předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="33ca9-104">In many situations, it is not necessary to control namespace prefixes.</span></span>  
  
 <span data-ttu-id="33ca9-105">Ale určitých nástrojích programovací XML vyžadovat konkrétní kontrolu nad předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="33ca9-105">However, certain XML programming tools require specific control of namespace prefixes.</span></span> <span data-ttu-id="33ca9-106">Například je může být manipulace s stylů XSLT nebo XAML dokumentu, který obsahuje vložené XPath výrazy, které odkazují na předpony oboru názvů konkrétní; v takovém případě je důležité, aby dokumentu se Dal serializovat s konkrétní předpon.</span><span class="sxs-lookup"><span data-stu-id="33ca9-106">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes; in this case, it is important that the document be serialized with those specific prefixes.</span></span>  
  
 <span data-ttu-id="33ca9-107">Toto je nejčastější příčinou řízení předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="33ca9-107">This is the most common reason for controlling namespace prefixes.</span></span>  
  
 <span data-ttu-id="33ca9-108">Řízení předpony oboru názvů jiné obvyklým důvodem je, že chcete uživatelům upravit v dokumentu XML ručně, a chcete vytvořit předpony oboru názvů, které jsou vhodné pro uživatele k zadání.</span><span class="sxs-lookup"><span data-stu-id="33ca9-108">Another common reason for controlling namespace prefixes is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="33ca9-109">Například můžete generování dokument XSD.</span><span class="sxs-lookup"><span data-stu-id="33ca9-109">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="33ca9-110">Konvence pro schémata naznačují, že používáte buď `xs` nebo `xsd` jako předponu pro obor názvů schématu.</span><span class="sxs-lookup"><span data-stu-id="33ca9-110">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>  
  
 <span data-ttu-id="33ca9-111">Chcete-li řídit předpony oboru názvů, vložte atributy, které deklarace oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="33ca9-111">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="33ca9-112">Pokud deklarace oborů názvů s konkrétní předpony [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se pokusí o respektovat předpony oboru názvů při serializaci.</span><span class="sxs-lookup"><span data-stu-id="33ca9-112">If you declare the namespaces with specific prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will attempt to honor the namespace prefixes when serializing.</span></span>  
  
 <span data-ttu-id="33ca9-113">Pokud chcete vytvořit atribut, který deklaruje předponu oboru názvů, vytvoření atribut, kde je obor názvů název atributu <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, a název atributu je Předpona oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="33ca9-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="33ca9-114">Hodnota atributu je identifikátor URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="33ca9-114">The value of the attribute is the URI of the namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33ca9-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="33ca9-115">Example</span></span>  
 <span data-ttu-id="33ca9-116">Tento příklad deklaruje dva obory názvů.</span><span class="sxs-lookup"><span data-stu-id="33ca9-116">This example declares two namespaces.</span></span> <span data-ttu-id="33ca9-117">Určuje, že `http://www.adventure-works.com` má předponu oboru názvů `aw`a že `www.fourthcoffee.com` má předponu oboru názvů `fc`.</span><span class="sxs-lookup"><span data-stu-id="33ca9-117">It specifies that the `http://www.adventure-works.com` namespace has the prefix of `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="33ca9-118">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="33ca9-118">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="33ca9-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="33ca9-119">See Also</span></span>  
 [<span data-ttu-id="33ca9-120">Práce s obory názvů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="33ca9-120">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
