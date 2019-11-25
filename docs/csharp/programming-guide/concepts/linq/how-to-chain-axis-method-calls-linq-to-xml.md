---
title: Postup řetězení volání metody osy (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: ccfbf516a7fddbef357bfb0072288e250768616b
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141429"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a>Postup řetězení volání metody osy (LINQ to XML) (C#)
Běžným vzorem, který použijete v kódu, je zavolat metodu osy a pak zavolat jednu z OS rozšiřujících metod.  
  
 Existují dvě osy s názvem `Elements`, které vracejí kolekci prvků: metoda <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> a metoda <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>. Tyto dvě osy můžete kombinovat a vyhledat všechny prvky zadaného názvu v dané hloubce stromu.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> a <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> k nalezení všech prvků `Name` ve všech elementech `Address` ve všech `PurchaseOrder` prvcích.  
  
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
  
 Tato funkce funguje, protože jedna z implementací osy `Elements` je jako metoda rozšíření v <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XContainer>. <xref:System.Xml.Linq.XElement> jsou odvozeny z <xref:System.Xml.Linq.XContainer>, takže můžete volat metodu <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> pro výsledky volání metody <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a>Příklad  
 Někdy je vhodné načíst všechny prvky na konkrétní hloubku prvku, pokud může nebo nemusí být zasahovat do nadřazených prvků. Například v následujícím dokumentu můžete chtít načíst všechny `ConfigParameter` prvky, které jsou podřízené prvku `Customer`, ale ne `ConfigParameter`, který je podřízenou položkou `Root` prvku.  
  
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
  
 K tomu můžete použít <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> osu, a to následujícím způsobem:  
  
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
 Následující příklad ukazuje stejnou techniku pro XML, která je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).  
  
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
  
## <a name="see-also"></a>Viz také:

- [LINQ to XML osy (C#)](linq-to-xml-axes-overview.md)
