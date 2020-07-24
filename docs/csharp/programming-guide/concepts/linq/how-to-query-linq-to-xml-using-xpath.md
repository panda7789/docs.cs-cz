---
title: Postup dotazování LINQ to XML pomocí XPath (C#)
description: Můžete použít rozšiřující metody v jazyce C# k dotazování stromu XML pomocí XPath. Obecně nedoporučujeme používat XPath s LINQ to XML.
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: fff45a93380b5af85aa640fc690783cc95e6298b
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104346"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a>Postup dotazování LINQ to XML pomocí XPath (C#)
Toto téma představuje rozšiřující metody, které umožňují dotazování stromu XML pomocí XPath. Podrobné informace o použití těchto rozšiřujících metod naleznete v tématu <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType> .  
  
 Pokud nemáte konkrétní důvod pro dotazování pomocí XPath, jako je například rozsáhlé použití starší verze kódu, použití XPath s LINQ to XML se nedoporučuje. Dotazy XPath nebudou provádět ani [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří malý strom XML a používá <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> se k výběru sady prvků.  
  
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
  