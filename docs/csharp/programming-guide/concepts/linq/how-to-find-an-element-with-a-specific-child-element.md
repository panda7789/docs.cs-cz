---
title: Jak najít element s konkrétním podřízeným elementem (C#)
description: Naučte se najít element, který má konkrétní podřízený element. Podívejte se na příklady kódu a další zdroje informací.
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 1d02f3d3af0a3711a5361941727e2e0b6c8bbdc9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301707"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a>Jak najít element s konkrétním podřízeným elementem (C#)
Toto téma ukazuje, jak najít konkrétní prvek, který má podřízený element s konkrétní hodnotou.  
  
## <a name="example"></a>Příklad  
 Příklad vyhledá `Test` prvek, který má `CommandLine` podřízený element s hodnotou "Examp2.EXE".  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: testovací konfigurace (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).  
  
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
 Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: konfigurace testu v oboru názvů](./sample-xml-file-test-configuration-in-a-namespace1.md).  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Přehled standardních operátorů dotazů (C#)](./standard-query-operators-overview.md)
- [Operace projekce (C#)](./projection-operations.md)
