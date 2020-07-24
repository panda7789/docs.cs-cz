---
title: Jak řídit předpony oboru názvů (C#) (LINQ to XML)
description: Naučte se řídit předpony oboru názvů při serializaci stromu XML v LINQ to XML v jazyce C#. Některé situace vyžadují kontrolu předpon oboru názvů.
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: b0c5cbfa7488f3a7105595830ef6765e6bfb1f12
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105300"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a><span data-ttu-id="3a622-104">Jak řídit předpony oboru názvů (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="3a622-104">How to control namespace prefixes (C#) (LINQ to XML)</span></span>
<span data-ttu-id="3a622-105">Toto téma popisuje, jak lze řídit předpony oboru názvů při serializaci stromu XML.</span><span class="sxs-lookup"><span data-stu-id="3a622-105">This topic describes how you can control namespace prefixes when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="3a622-106">V mnoha situacích není nutné řídit předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3a622-106">In many situations, it is not necessary to control namespace prefixes.</span></span>  
  
 <span data-ttu-id="3a622-107">Nicméně některé programovací nástroje XML vyžadují konkrétní kontrolu předpon oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3a622-107">However, certain XML programming tools require specific control of namespace prefixes.</span></span> <span data-ttu-id="3a622-108">Můžete například manipulovat se šablonou stylů XSLT nebo dokumentem XAML obsahující vložené výrazy XPath, které odkazují na konkrétní předpony oboru názvů. v takovém případě je důležité, aby byl dokument serializován s těmito konkrétními předponami.</span><span class="sxs-lookup"><span data-stu-id="3a622-108">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes; in this case, it is important that the document be serialized with those specific prefixes.</span></span>  
  
 <span data-ttu-id="3a622-109">Toto je nejběžnější důvod pro řídící předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3a622-109">This is the most common reason for controlling namespace prefixes.</span></span>  
  
 <span data-ttu-id="3a622-110">Dalším běžným důvodem pro kontrolní předpony oboru názvů je, že chcete, aby uživatelé upravili dokument XML ručně a chcete vytvořit předpony oboru názvů, které jsou vhodné pro uživatele, aby zadali.</span><span class="sxs-lookup"><span data-stu-id="3a622-110">Another common reason for controlling namespace prefixes is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="3a622-111">Můžete například vygenerovat dokument XSD.</span><span class="sxs-lookup"><span data-stu-id="3a622-111">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="3a622-112">Konvence pro schémata naznačují, že použijete `xs` `xsd` předponu pro obor názvů schématu nebo.</span><span class="sxs-lookup"><span data-stu-id="3a622-112">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>  
  
 <span data-ttu-id="3a622-113">Chcete-li řídit předpony oboru názvů, vložte atributy, které deklaruje obory názvů.</span><span class="sxs-lookup"><span data-stu-id="3a622-113">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="3a622-114">Pokud deklarujete obory názvů se specifickými předponami, aplikace [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se pokusí při serializaci při serializaci vyhovět předponám oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3a622-114">If you declare the namespaces with specific prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will attempt to honor the namespace prefixes when serializing.</span></span>  
  
 <span data-ttu-id="3a622-115">Chcete-li vytvořit atribut, který deklaruje obor názvů s předponou, vytvoříte atribut, kde je obor názvů názvu atributu <xref:System.Xml.Linq.XNamespace.Xmlns%2A> , a název atributu je předpona oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3a622-115">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="3a622-116">Hodnota atributu je identifikátor URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3a622-116">The value of the attribute is the URI of the namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a622-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="3a622-117">Example</span></span>  
 <span data-ttu-id="3a622-118">Tento příklad deklaruje dva obory názvů.</span><span class="sxs-lookup"><span data-stu-id="3a622-118">This example declares two namespaces.</span></span> <span data-ttu-id="3a622-119">Určuje, že `http://www.adventure-works.com` obor názvů má předponu `aw` a že `www.fourthcoffee.com` obor názvů má předponu `fc` .</span><span class="sxs-lookup"><span data-stu-id="3a622-119">It specifies that the `http://www.adventure-works.com` namespace has the prefix of `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
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
  
 <span data-ttu-id="3a622-120">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3a622-120">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a622-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a622-121">See also</span></span>

- [<span data-ttu-id="3a622-122">Přehled oborů názvů (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="3a622-122">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
