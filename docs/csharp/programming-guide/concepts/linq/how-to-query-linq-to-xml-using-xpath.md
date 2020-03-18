---
title: Jak dotaz LINQ na XML pomocí XPath (C#)
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: 61878febd9b4880872b7bc58e4de04b37cff96f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344808"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a>Jak dotaz LINQ na XML pomocí XPath (C#)
Toto téma představuje metody rozšíření, které umožňují dotaz na strom XML pomocí XPath. Podrobné informace o použití těchto <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>metod rozšíření naleznete v tématu .  
  
 Pokud nemáte velmi specifický důvod pro dotazování pomocí XPath, jako je například rozsáhlé použití staršího kódu, nedoporučujeme používat XPath s LINQ na XML. Dotazy XPath nebudou fungovat tak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dobře jako dotazy.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří malý strom <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> XML a použije se k výběru sady prvků.  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  