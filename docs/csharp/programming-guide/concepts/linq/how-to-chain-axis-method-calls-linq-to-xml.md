---
title: Postup řetězení volání metody osy (LINQ to XML) (C#)
description: Tyto LINQ to XML Příklady v jazyce C# ukazují volání dvou OS, aby bylo možné najít všechny prvky zadaného názvu v dané hloubkě stromu.
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: f26efd2ca918fd36916eb4f01462af70066219a0
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105390"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a>Postup řetězení volání metody osy (LINQ to XML) (C#)
Běžným vzorem, který použijete v kódu, je zavolat metodu osy a pak zavolat jednu z OS rozšiřujících metod.  
  
 Existují dvě osy s názvem `Elements` , který vrací kolekci prvků: <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> Metoda a <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metoda. Tyto dvě osy můžete kombinovat a vyhledat všechny prvky zadaného názvu v dané hloubce stromu.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> a <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> k nalezení všech prvků všech prvků ve `Name` `Address` všech `PurchaseOrder` prvcích.  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```csharp  
XElement purchaseOrders = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements("PurchaseOrder")  
        .Elements("Address")  
        .Elements("Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 To funguje, protože jedna z implementací `Elements` osy je jako metoda rozšíření na <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XContainer> . <xref:System.Xml.Linq.XElement>je odvozen z <xref:System.Xml.Linq.XContainer> , takže můžete volat <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metodu pro výsledky volání <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> metody.  
  
## <a name="example"></a>Příklad  
 Někdy je vhodné načíst všechny prvky na konkrétní hloubku prvku, pokud může nebo nemusí být zasahovat do nadřazených prvků. Například v následujícím dokumentu můžete chtít načíst všechny `ConfigParameter` prvky, které jsou podřízené `Customer` prvku, ale nikoli `ConfigParameter` podřízený `Root` prvek elementu.  
  
```xml  
<Root>  
  <ConfigParameter>RootConfigParameter</ConfigParameter>  
  <Customer>  
    <Name>Frank</Name>  
    <Config>  
      <ConfigParameter>FirstConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
  <Customer>  
    <Name>Bob</Name>  
    <!--This customer doesn't have a Config element-->  
  </Customer>  
  <Customer>  
    <Name>Bill</Name>  
    <Config>  
      <ConfigParameter>SecondConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
</Root>  
```  
  
 K tomu můžete použít <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> osu následujícím způsobem:  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejnou techniku pro XML, která je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek v oboru názvů](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement purchaseOrders = XElement.Load("PurchaseOrdersInNamespace.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements(aw + "PurchaseOrder")  
        .Elements(aw + "Address")  
        .Elements(aw + "Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a>Viz také

- [LINQ to XML osy (C#)](linq-to-xml-axes-overview.md)
