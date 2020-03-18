---
title: Jak najít prvek s určitým podřízeným prvkem (C#)
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 0536b1b92d4d7fc18b5d406bbcd24aefc6a840c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141146"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a>Jak najít prvek s určitým podřízeným prvkem (C#)
Toto téma ukazuje, jak najít konkrétní prvek, který má podřízený prvek s určitou hodnotou.  
  
## <a name="example"></a>Příklad  
 Příklad vyhledá `Test` prvek, který `CommandLine` má podřízený prvek s hodnotou "Examp2.EXE".  
  
 Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Test Configuration (LINQ to XML).](./sample-xml-file-test-configuration-linq-to-xml.md)  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro jazyk XML, který je v oboru názvů. Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Testovat konfiguraci v oboru názvů](./sample-xml-file-test-configuration-in-a-namespace1.md).  
  
```csharp  
XElement root = XElement.Load("TestConfigInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<XElement> tests =  
    from el in root.Elements(ad + "Test")  
    where (string)el.Element(ad + "CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Standardní operátory dotazů – přehled (C#)](./standard-query-operators-overview.md)
- [Projekční operace (C#)](./projection-operations.md)
