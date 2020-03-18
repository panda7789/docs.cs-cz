---
title: Jak řídit předpony oboru názvů (C#) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 9f43c0804d8c830fa75f1e1390cb578c5f5d5106
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141377"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a><span data-ttu-id="6cb3e-102">Jak řídit předpony oboru názvů (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="6cb3e-102">How to control namespace prefixes (C#) (LINQ to XML)</span></span>
<span data-ttu-id="6cb3e-103">Toto téma popisuje, jak můžete řídit předpony oboru názvů při serializaci stromu XML.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-103">This topic describes how you can control namespace prefixes when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="6cb3e-104">V mnoha situacích není nutné řídit předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-104">In many situations, it is not necessary to control namespace prefixes.</span></span>  
  
 <span data-ttu-id="6cb3e-105">Některé programovací nástroje XML však vyžadují zvláštní řízení předpon oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-105">However, certain XML programming tools require specific control of namespace prefixes.</span></span> <span data-ttu-id="6cb3e-106">Můžete například manipulovat se šablonou stylů XSLT nebo dokumentem XAML, který obsahuje vložené výrazy XPath, které odkazují na konkrétní předpony oboru názvů; v tomto případě je důležité, aby byl dokument serializován s těmito specifickými předčíslími.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-106">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes; in this case, it is important that the document be serialized with those specific prefixes.</span></span>  
  
 <span data-ttu-id="6cb3e-107">Toto je nejčastější důvod pro řízení předpon oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-107">This is the most common reason for controlling namespace prefixes.</span></span>  
  
 <span data-ttu-id="6cb3e-108">Dalším běžným důvodem pro řízení předpon oboru názvů je, že chcete, aby uživatelé ručně upravovali dokument XML, a chcete vytvořit předpony oboru názvů, které jsou vhodné pro uživatele k zadání.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-108">Another common reason for controlling namespace prefixes is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="6cb3e-109">Například můžete generovat dokument XSD.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-109">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="6cb3e-110">Konvence pro schémata naznačují, že `xs` používáte buď nebo `xsd` jako předponu pro obor názvů schématu.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-110">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>  
  
 <span data-ttu-id="6cb3e-111">Chcete-li řídit předpony oboru názvů, vložte atributy, které deklarují obory názvů.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-111">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="6cb3e-112">Pokud deklarujete obory [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] názvů s určitými předčíslími, pokusíte se respektovat předpony oboru názvů při serializaci.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-112">If you declare the namespaces with specific prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will attempt to honor the namespace prefixes when serializing.</span></span>  
  
 <span data-ttu-id="6cb3e-113">Chcete-li vytvořit atribut, který deklaruje obor názvů s předponou, vytvořte <xref:System.Xml.Linq.XNamespace.Xmlns%2A>atribut, ve kterém je obor názvů názvu atributu a název atributu je předpona oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="6cb3e-114">Hodnota atributu je identifikátor URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-114">The value of the attribute is the URI of the namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cb3e-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="6cb3e-115">Example</span></span>  
 <span data-ttu-id="6cb3e-116">Tento příklad deklaruje dva obory názvů.</span><span class="sxs-lookup"><span data-stu-id="6cb3e-116">This example declares two namespaces.</span></span> <span data-ttu-id="6cb3e-117">Určuje, že `http://www.adventure-works.com` obor názvů má předponu `aw`a `www.fourthcoffee.com` že obor názvů `fc`má předponu .</span><span class="sxs-lookup"><span data-stu-id="6cb3e-117">It specifies that the `http://www.adventure-works.com` namespace has the prefix of `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
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
  
 <span data-ttu-id="6cb3e-118">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6cb3e-118">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6cb3e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="6cb3e-119">See also</span></span>

- [<span data-ttu-id="6cb3e-120">Obory názvů – přehled (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6cb3e-120">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
