---
title: 'Postupy: Ovládací prvek Namespace předpony (C#) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 4664be2661e54782598345886029835108934955
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702188"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a><span data-ttu-id="28f3c-102">Postupy: Ovládací prvek Namespace předpony (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="28f3c-102">How to: Control Namespace Prefixes (C#) (LINQ to XML)</span></span>
<span data-ttu-id="28f3c-103">Toto téma popisuje, jak můžete řídit předpony oboru názvů při serializaci stromu XML.</span><span class="sxs-lookup"><span data-stu-id="28f3c-103">This topic describes how you can control namespace prefixes when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="28f3c-104">V mnoha situacích není nutné k řízení předpon názvového prostoru.</span><span class="sxs-lookup"><span data-stu-id="28f3c-104">In many situations, it is not necessary to control namespace prefixes.</span></span>  
  
 <span data-ttu-id="28f3c-105">Nicméně některé programovací nástroje XML vyžadují určitý ovládací prvek předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="28f3c-105">However, certain XML programming tools require specific control of namespace prefixes.</span></span> <span data-ttu-id="28f3c-106">Například můžete může být zpracování šablony stylů XSLT nebo dokumentu XAML, který obsahuje vložené výrazy XPath, které odkazují na konkrétní obor názvů předpony; v takovém případě je důležité, že dokument Dal serializovat s příznakem tyto konkrétní předpony.</span><span class="sxs-lookup"><span data-stu-id="28f3c-106">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes; in this case, it is important that the document be serialized with those specific prefixes.</span></span>  
  
 <span data-ttu-id="28f3c-107">Toto je nejběžnějším důvodem pro řízení předpon názvového prostoru.</span><span class="sxs-lookup"><span data-stu-id="28f3c-107">This is the most common reason for controlling namespace prefixes.</span></span>  
  
 <span data-ttu-id="28f3c-108">Dalším běžným důvodem pro řízení předpon názvového prostoru je, že chcete uživatelům ručně upravit dokument XML, a chcete vytvořit obor názvů předpony, které jsou vhodné pro uživatele, aby.</span><span class="sxs-lookup"><span data-stu-id="28f3c-108">Another common reason for controlling namespace prefixes is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="28f3c-109">Může být například generování XSD dokumentu.</span><span class="sxs-lookup"><span data-stu-id="28f3c-109">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="28f3c-110">Konvence pro schémata doporučujeme použít buď `xs` nebo `xsd` jako předponu pro obor názvů schématu.</span><span class="sxs-lookup"><span data-stu-id="28f3c-110">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>  
  
 <span data-ttu-id="28f3c-111">Chcete-li řízení předpon názvového prostoru, vložte atributy, které deklarace oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="28f3c-111">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="28f3c-112">Pokud deklarujete obory názvů s konkrétní předpony [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se pokusí o případném dalším sdílení dodržovat předpony oboru názvů při serializaci.</span><span class="sxs-lookup"><span data-stu-id="28f3c-112">If you declare the namespaces with specific prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will attempt to honor the namespace prefixes when serializing.</span></span>  
  
 <span data-ttu-id="28f3c-113">Chcete-li vytvořit atribut, který deklaruje oboru názvů s předponou, vytvořte atribut kde obor názvů název atributu je <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, a název atributu je Předpona oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="28f3c-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="28f3c-114">Hodnota atributu je identifikátor URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="28f3c-114">The value of the attribute is the URI of the namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28f3c-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="28f3c-115">Example</span></span>  
 <span data-ttu-id="28f3c-116">V tomto příkladu deklaruje dva obory názvů.</span><span class="sxs-lookup"><span data-stu-id="28f3c-116">This example declares two namespaces.</span></span> <span data-ttu-id="28f3c-117">Určuje, že `http://www.adventure-works.com` obor názvů má předponu `aw`a že `www.fourthcoffee.com` obor názvů má předponu `fc`.</span><span class="sxs-lookup"><span data-stu-id="28f3c-117">It specifies that the `http://www.adventure-works.com` namespace has the prefix of `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
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
  
 <span data-ttu-id="28f3c-118">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="28f3c-118">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="28f3c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28f3c-119">See also</span></span>

- [<span data-ttu-id="28f3c-120">Práce s názvovými prostory XML (C#)</span><span class="sxs-lookup"><span data-stu-id="28f3c-120">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
