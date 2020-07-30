---
title: Jak najít odvozené elementy (XPath-LINQ to XML) (C#)
description: Naučte se najít následníky s konkrétním názvem pomocí výrazu XPath. Zkontrolujte příklad kódu, který používá ukázkový soubor XML.
ms.date: 07/20/2015
ms.assetid: b318da39-bb8b-4c56-a019-e13b12b01831
ms.openlocfilehash: c5a998a05f866203f3b684b8847a4a5647c12e5b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303267"
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-c"></a>Jak najít odvozené elementy (XPath-LINQ to XML) (C#)
Toto téma ukazuje, jak získat odvozené prvky s určitým názvem.  
  
 Výraz XPath je `//Name` .  
  
## <a name="example"></a>Příklad  
 Tento příklad vyhledá všechny následníky s názvem `Name` .  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = po.Root.Descendants("Name");  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements("//Name");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```output  
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
