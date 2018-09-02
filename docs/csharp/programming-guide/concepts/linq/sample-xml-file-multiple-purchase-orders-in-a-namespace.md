---
title: 'Ukázkový soubor XML: Více nákupních objednávek v Namespace2'
ms.date: 07/20/2015
ms.assetid: 595024f2-374a-4615-acb5-64fa1600f377
ms.openlocfilehash: 03ca5cfbf198f576a52e6ceb5eb085195d599d3b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43470009"
---
# <a name="sample-xml-file-multiple-purchase-orders-in-a-namespace"></a>Ukázkový soubor XML: Více nákupních objednávek v Namespace
Následující soubor XML se používá v různých příkladů v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dokumentaci. Tento soubor obsahuje několik nákupních objednávek. XML je v oboru názvů.  
  
## <a name="purchaseordersinnamespacexml"></a>PurchaseOrdersInNamespace.xml  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<aw:PurchaseOrders xmlns:aw="http://www.adventure-works.com">  
  <aw:PurchaseOrder aw:PurchaseOrderNumber="99503" aw:OrderDate="1999-10-20">  
    <aw:Address aw:Type="Shipping">  
      <aw:Name>Ellen Adams</aw:Name>  
      <aw:Street>123 Maple Street</aw:Street>  
      <aw:City>Mill Valley</aw:City>  
      <aw:State>CA</aw:State>  
      <aw:Zip>10999</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:Address>  
    <aw:Address aw:Type="Billing">  
      <aw:Name>Tai Yee</aw:Name>  
      <aw:Street>8 Oak Avenue</aw:Street>  
      <aw:City>Old Town</aw:City>  
      <aw:State>PA</aw:State>  
      <aw:Zip>95819</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:Address>  
    <aw:DeliveryNotes>Please leave packages in shed by driveway.</aw:DeliveryNotes>  
    <aw:Items>  
      <aw:Item aw:PartNumber="872-AA">  
        <aw:ProductName>Lawnmower</aw:ProductName>  
        <aw:Quantity>1</aw:Quantity>  
        <aw:USPrice>148.95</aw:USPrice>  
        <aw:Comment>Confirm this is electric</aw:Comment>  
      </aw:Item>  
      <aw:Item aw:PartNumber="926-AA">  
        <aw:ProductName>Baby Monitor</aw:ProductName>  
        <aw:Quantity>2</aw:Quantity>  
        <aw:USPrice>39.98</aw:USPrice>  
        <aw:ShipDate>1999-05-21</aw:ShipDate>  
      </aw:Item>  
    </aw:Items>  
  </aw:PurchaseOrder>  
  <aw:PurchaseOrder aw:PurchaseOrderNumber="99505" aw:OrderDate="1999-10-22">  
    <aw:Address aw:Type="Shipping">  
      <aw:Name>Cristian Osorio</aw:Name>  
      <aw:Street>456 Main Street</aw:Street>  
      <aw:City>Buffalo</aw:City>  
      <aw:State>NY</aw:State>  
      <aw:Zip>98112</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:Address>  
    <aw:Address aw:Type="Billing">  
      <aw:Name>Cristian Osorio</aw:Name>  
      <aw:Street>456 Main Street</aw:Street>  
      <aw:City>Buffalo</aw:City>  
      <aw:State>NY</aw:State>  
      <aw:Zip>98112</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:Address>  
    <aw:DeliveryNotes>Please notify me before shipping.</aw:DeliveryNotes>  
    <aw:Items>  
      <aw:Item aw:PartNumber="456-NM">  
        <aw:ProductName>Power Supply</aw:ProductName>  
        <aw:Quantity>1</aw:Quantity>  
        <aw:USPrice>45.99</aw:USPrice>  
      </aw:Item>  
    </aw:Items>  
  </aw:PurchaseOrder>  
  <aw:PurchaseOrder aw:PurchaseOrderNumber="99504" aw:OrderDate="1999-10-22">  
    <aw:Address aw:Type="Shipping">  
      <aw:Name>Jessica Arnold</aw:Name>  
      <aw:Street>4055 Madison Ave</aw:Street>  
      <aw:City>Seattle</aw:City>  
      <aw:State>WA</aw:State>  
      <aw:Zip>98112</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:Address>  
    <aw:Address aw:Type="Billing">  
      <aw:Name>Jessica Arnold</aw:Name>  
      <aw:Street>4055 Madison Ave</aw:Street>  
      <aw:City>Buffalo</aw:City>  
      <aw:State>NY</aw:State>  
      <aw:Zip>98112</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:Address>  
    <aw:Items>  
      <aw:Item aw:PartNumber="898-AZ">  
        <aw:ProductName>Computer Keyboard</aw:ProductName>  
        <aw:Quantity>1</aw:Quantity>  
        <aw:USPrice>29.99</aw:USPrice>  
      </aw:Item>  
      <aw:Item aw:PartNumber="898-AM">  
        <aw:ProductName>Wireless Mouse</aw:ProductName>  
        <aw:Quantity>1</aw:Quantity>  
        <aw:USPrice>14.99</aw:USPrice>  
      </aw:Item>  
    </aw:Items>  
  </aw:PurchaseOrder>  
</aw:PurchaseOrders>  
```  
  
## <a name="see-also"></a>Viz také  
 [Ukázkové dokumenty XML (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
