---
title: 'Postupy: Vyhledání elementů v názvovém prostoru (XPath – LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: c7cb3b77-3424-4b54-9efa-4dc715948e41
ms.openlocfilehash: 3663516e6b6289fe3b1d0599ff3ed4b7dad6a80a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405193"
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="26edc-102">Postupy: hledání elementů v oboru názvů (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26edc-102">How to: Find Elements in a Namespace (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="26edc-103">Výrazy XPath můžou najít uzly v konkrétním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="26edc-103">XPath expressions can find nodes in a particular namespace.</span></span> <span data-ttu-id="26edc-104">Výrazy XPath používají předpony oboru názvů pro zadání oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="26edc-104">XPath expressions use namespace prefixes for specifying namespaces.</span></span> <span data-ttu-id="26edc-105">Chcete-li analyzovat výraz XPath, který obsahuje předpony oboru názvů, je nutné předat objekt metodám XPath, které implementuje <xref:System.Xml.IXmlNamespaceResolver> .</span><span class="sxs-lookup"><span data-stu-id="26edc-105">To parse an XPath expression that contains namespace prefixes, you must pass an object to the XPath methods that implements <xref:System.Xml.IXmlNamespaceResolver>.</span></span> <span data-ttu-id="26edc-106">Tento příklad používá <xref:System.Xml.XmlNamespaceManager> .</span><span class="sxs-lookup"><span data-stu-id="26edc-106">This example uses <xref:System.Xml.XmlNamespaceManager>.</span></span>  
  
 <span data-ttu-id="26edc-107">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="26edc-107">The XPath expression is:</span></span>  
  
 `./aw:*`  
  
## <a name="example"></a><span data-ttu-id="26edc-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="26edc-108">Example</span></span>  
 <span data-ttu-id="26edc-109">Následující příklad přečte strom XML, který obsahuje dva obory názvů.</span><span class="sxs-lookup"><span data-stu-id="26edc-109">The following example reads an XML tree that contains two namespaces.</span></span> <span data-ttu-id="26edc-110">Používá <xref:System.Xml.XmlReader> ke čtení dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="26edc-110">It uses an <xref:System.Xml.XmlReader> to read the XML document.</span></span> <span data-ttu-id="26edc-111">Pak získá <xref:System.Xml.XmlNameTable> z <xref:System.Xml.XmlReader> , a <xref:System.Xml.XmlNamespaceManager> z <xref:System.Xml.XmlNameTable> .</span><span class="sxs-lookup"><span data-stu-id="26edc-111">It then gets an <xref:System.Xml.XmlNameTable> from the <xref:System.Xml.XmlReader>, and an <xref:System.Xml.XmlNamespaceManager> from the <xref:System.Xml.XmlNameTable>.</span></span> <span data-ttu-id="26edc-112">Používá <xref:System.Xml.XmlNamespaceManager> při výběru elementů.</span><span class="sxs-lookup"><span data-stu-id="26edc-112">It uses the <xref:System.Xml.XmlNamespaceManager> when selecting elements.</span></span>  
  
```vb  
Dim reader As XmlReader = _  
        XmlReader.Create("ConsolidatedPurchaseOrders.xml")  
Dim root As XElement = XElement.Load(reader)  
Dim nameTable As XmlNameTable = reader.NameTable  
Dim namespaceManager As XmlNamespaceManager = New XmlNamespaceManager(nameTable)  
namespaceManager.AddNamespace("aw", "http://www.adventure-works.com")  
  
Dim list1 As IEnumerable(Of XElement) = _  
        root.XPathSelectElements("./aw:*", namespaceManager)  
Dim list2 As IEnumerable(Of XElement) = _  
    From el In root.Elements() _  
    Where el.Name.Namespace = "http://www.adventure-works.com" _  
    Select el  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list2  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="26edc-113">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="26edc-113">This example produces the following output:</span></span>  
  
```console
Results are identical  
<aw:PurchaseOrder PONumber="11223" Date="2000-01-15" xmlns:aw="http://www.adventure-works.com">  
    <aw:ShippingAddress>  
      <aw:Name>Chris Preston</aw:Name>  
      <aw:Street>123 Main St.</aw:Street>  
      <aw:City>Seattle</aw:City>  
      <aw:State>WA</aw:State>  
      <aw:Zip>98113</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:ShippingAddress>  
    <aw:BillingAddress>  
      <aw:Name>Chris Preston</aw:Name>  
      <aw:Street>123 Main St.</aw:Street>  
      <aw:City>Seattle</aw:City>  
      <aw:State>WA</aw:State>  
      <aw:Zip>98113</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:BillingAddress>  
    <aw:DeliveryInstructions>Ship only complete order.</aw:DeliveryInstructions>  
    <aw:Item PartNum="LIT-01">  
      <aw:ProductID>Litware Networking Card</aw:ProductID>  
      <aw:Qty>1</aw:Qty>  
      <aw:Price>20.99</aw:Price>  
    </aw:Item>  
    <aw:Item PartNum="LIT-25">  
      <aw:ProductID>Litware 17in LCD Monitor</aw:ProductID>  
      <aw:Qty>1</aw:Qty>  
      <aw:Price>199.99</aw:Price>  
    </aw:Item>  
  </aw:PurchaseOrder>  
```  
  
## <a name="see-also"></a><span data-ttu-id="26edc-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="26edc-114">See also</span></span>

- [<span data-ttu-id="26edc-115">LINQ to XML pro uživatele XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26edc-115">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
