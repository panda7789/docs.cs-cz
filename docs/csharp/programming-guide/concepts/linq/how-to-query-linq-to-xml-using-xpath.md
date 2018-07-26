---
title: 'Postupy: dotazování na LINQ to XML pomocí jazyka XPath (C#)'
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: a02149719afa19350a9baf15c41bd3548daa1344
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37959852"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a>Postupy: dotazování na LINQ to XML pomocí jazyka XPath (C#)
Toto téma představuje rozšiřující metody, které vám umožní dotazovat stromu XML pomocí XPath. Podrobné informace o použití těchto metod rozšíření najdete v tématu <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
 Pokud nemáte velmi konkrétní důvod pro dotazování pomocí XPath, jako je například příliš často používá starší verzi kódu s LINQ to XML pomocí jazyka XPath se nedoporučuje. Nebude provádět dotazy XPath a jednak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří malý stromu XML a používá <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> vybrat sadu elementů.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child1", 2),  
    new XElement("Child1", 3),  
    new XElement("Child2", 4),  
    new XElement("Child2", 5),  
    new XElement("Child2", 6)  
);  
IEnumerable<XElement> list = root.XPathSelectElements("./Child2");  
foreach (XElement el in list)  
    Console.WriteLine(el);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a>Viz také  
 [Pokročilé techniky dotazování (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
