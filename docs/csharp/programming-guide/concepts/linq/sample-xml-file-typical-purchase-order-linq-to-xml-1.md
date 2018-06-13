---
title: 'Ukázkový soubor XML: Typické nákupní objednávka (technologie LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: dcbfb859-24fc-4758-b01c-51d1b6f644e6
ms.openlocfilehash: 0a5ea4dad9d86182d4bc3def0e8a59d1dcd892af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339420"
---
# <a name="sample-xml-file-typical-purchase-order-linq-to-xml"></a><span data-ttu-id="1459d-102">Ukázkový soubor XML: Typické nákupní objednávka (technologie LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="1459d-102">Sample XML File: Typical Purchase Order (LINQ to XML)</span></span>
<span data-ttu-id="1459d-103">Následující soubor XML se používá v různých příklady v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="1459d-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="1459d-104">Tento soubor je typické nákupní objednávka.</span><span class="sxs-lookup"><span data-stu-id="1459d-104">This file is a typical purchase order.</span></span>  
  
## <a name="purchaseorderxml"></a><span data-ttu-id="1459d-105">PurchaseOrder.xml</span><span class="sxs-lookup"><span data-stu-id="1459d-105">PurchaseOrder.xml</span></span>  
  
```xml  
<?xml version="1.0"?>  
<PurchaseOrder PurchaseOrderNumber="99503" OrderDate="1999-10-20">  
  <Address Type="Shipping">  
    <Name>Ellen Adams</Name>  
    <Street>123 Maple Street</Street>  
    <City>Mill Valley</City>  
    <State>CA</State>  
    <Zip>10999</Zip>  
    <Country>USA</Country>  
  </Address>  
  <Address Type="Billing">  
    <Name>Tai Yee</Name>  
    <Street>8 Oak Avenue</Street>  
    <City>Old Town</City>  
    <State>PA</State>  
    <Zip>95819</Zip>  
    <Country>USA</Country>  
  </Address>  
  <DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
  <Items>  
    <Item PartNumber="872-AA">  
      <ProductName>Lawnmower</ProductName>  
      <Quantity>1</Quantity>  
      <USPrice>148.95</USPrice>  
      <Comment>Confirm this is electric</Comment>  
    </Item>  
    <Item PartNumber="926-AA">  
      <ProductName>Baby Monitor</ProductName>  
      <Quantity>2</Quantity>  
      <USPrice>39.98</USPrice>  
      <ShipDate>1999-05-21</ShipDate>  
    </Item>  
  </Items>  
</PurchaseOrder>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1459d-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="1459d-106">See Also</span></span>  
 [<span data-ttu-id="1459d-107">Ukázkové dokumenty XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="1459d-107">Sample XML Documents (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
