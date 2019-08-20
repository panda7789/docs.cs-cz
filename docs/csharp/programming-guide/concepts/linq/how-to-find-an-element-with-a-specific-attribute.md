---
title: 'Postupy: Vyhledání elementu s konkrétním atributem (C#)'
ms.date: 07/20/2015
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: da2d1691af6268a97e1f586e92c26bbb26906100
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593601"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-c"></a>Postupy: Vyhledání elementu s konkrétním atributem (C#)
Toto téma ukazuje, jak najít element, který má atribut, který má konkrétní hodnotu.  
  
## <a name="example"></a>Příklad  
 Příklad ukazuje, jak najít `Address` prvek, který `Type` má atribut s hodnotou "vyúčtování".  
  
 V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
XElement root = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> address =  
    from el in root.Elements("Address")  
    where (string)el.Attribute("Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 Tento kód generuje následující výstup:  
  
```xml  
<Address Type="Billing">  
  <Name>Tai Yee</Name>  
  <Street>8 Oak Avenue</Street>  
  <City>Old Town</City>  
  <State>PA</State>  
  <Zip>95819</Zip>  
  <Country>USA</Country>  
</Address>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).  
  
 V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Typická nákupní objednávka v oboru názvů](./sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```csharp  
XElement root = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> address =  
    from el in root.Elements(aw + "Address")  
    where (string)el.Attribute(aw + "Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 Tento kód generuje následující výstup:  
  
```xml  
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">  
  <aw:Name>Tai Yee</aw:Name>  
  <aw:Street>8 Oak Avenue</aw:Street>  
  <aw:City>Old Town</aw:City>  
  <aw:State>PA</aw:State>  
  <aw:Zip>95819</aw:Zip>  
  <aw:Country>USA</aw:Country>  
</aw:Address>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Přehled standardních operátorů dotazůC#()](./standard-query-operators-overview.md)
- [Operace projekce (C#)](./projection-operations.md)
