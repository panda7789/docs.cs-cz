---
title: Hledání prvků v oboru názvů (XPath-LINQ to XML) (C#)
description: Naučte se najít prvky v oboru názvů pomocí výrazu XPath. Podívejte se na příklad, který čte strom XML, který obsahuje dva obory názvů.
ms.date: 07/20/2015
ms.assetid: cae1c4ac-6cd5-46cf-9b1c-bd85bc9b7ea9
ms.openlocfilehash: 3bf15c4183e3ca339fa7090c21baff83526e37d3
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303228"
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-c"></a>Hledání prvků v oboru názvů (XPath-LINQ to XML) (C#)

Výrazy XPath můžou najít uzly v konkrétním oboru názvů. Výrazy XPath používají předpony oboru názvů pro zadání oborů názvů. Chcete-li analyzovat výraz XPath, který obsahuje předpony oboru názvů, je nutné předat objekt metodám XPath, které implementuje <xref:System.Xml.IXmlNamespaceResolver> . Tento příklad používá <xref:System.Xml.XmlNamespaceManager> .

Výraz XPath je:

`./aw:*`

## <a name="example"></a>Příklad

Následující příklad přečte strom XML, který obsahuje dva obory názvů. Používá <xref:System.Xml.XmlReader> ke čtení dokumentu XML. Pak získá <xref:System.Xml.XmlNameTable> z <xref:System.Xml.XmlReader> , a <xref:System.Xml.XmlNamespaceManager> z <xref:System.Xml.XmlNameTable> . Používá <xref:System.Xml.XmlNamespaceManager> při výběru elementů.

```csharp
XmlReader reader = XmlReader.Create("ConsolidatedPurchaseOrders.xml");
XElement root = XElement.Load(reader);
XmlNameTable nameTable = reader.NameTable;
XmlNamespaceManager namespaceManager = new XmlNamespaceManager(nameTable);
namespaceManager.AddNamespace("aw", "http://www.adventure-works.com");
IEnumerable<XElement> list1 = root.XPathSelectElements("./aw:*", namespaceManager);
IEnumerable<XElement> list2 =
    from el in root.Elements()
    where el.Name.Namespace == "http://www.adventure-works.com"
    select el;
if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list2)
    Console.WriteLine(el);
```

Tento příklad vytvoří následující výstup:

```output
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
