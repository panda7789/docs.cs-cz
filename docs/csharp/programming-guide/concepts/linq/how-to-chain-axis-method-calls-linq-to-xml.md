---
title: Jak zřetězit volání metod osy (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 56fa5c9e8358883d838b68e99664240aa97f347f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169464"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a>Jak zřetězit volání metod osy (LINQ to XML) (C#)
Běžný vzor, který budete používat v kódu je volání metody osy, pak volání jedné z os metody rozšíření.  
  
 Existují dvě osy s `Elements` názvem, které vrátí <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> kolekci <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> prvků: metoda a metoda. Tyto dvě osy můžete zkombinovat a najít všechny prvky zadaného názvu v dané hloubce ve stromu.  
  
## <a name="example"></a>Příklad  
 Tento příklad <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> používá a `Name` najít `Address` všechny prvky ve všech prvků ve všech `PurchaseOrder` prvků.  
  
 Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML).](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 To funguje, protože jedna z `Elements` implementací osy je jako metoda rozšíření na <xref:System.Collections.Generic.IEnumerable%601> . <xref:System.Xml.Linq.XContainer> <xref:System.Xml.Linq.XElement>odvozuje <xref:System.Xml.Linq.XContainer>z , takže <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> můžete volat metodu na <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> výsledky volání metody.  
  
## <a name="example"></a>Příklad  
 Někdy chcete načíst všechny prvky v určité hloubce prvku, když může nebo nemusí být zasahující předkové. Například v následujícím dokumentu můžete chtít načíst `ConfigParameter` všechny prvky, `Customer` které jsou `ConfigParameter` podřízené prvku, `Root` ale ne, který je podřízený prvku.  
  
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
  
 Chcete-li to provést, <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> můžete použít osu takto:  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejnou techniku pro XML, která je v oboru názvů. Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Více nákupních objednávek v oboru názvů](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a>Viz také

- [LINQ na osy XML (C#)](linq-to-xml-axes-overview.md)
