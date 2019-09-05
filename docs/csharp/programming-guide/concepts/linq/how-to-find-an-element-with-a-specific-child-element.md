---
title: 'Postupy: Vyhledání elementu s konkrétním podřízeným elementem (C#)'
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: f007bddcbecc1cb938d05c7d444d29b6047749e8
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253745"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a>Postupy: Vyhledání elementu s konkrétním podřízeným elementem (C#)
Toto téma ukazuje, jak najít konkrétní prvek, který má podřízený element s konkrétní hodnotou.  
  
## <a name="example"></a>Příklad  
 Příklad vyhledá `Test` prvek, který `CommandLine` má podřízený element s hodnotou "Examp2. exe".  
  
 V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Konfigurace testu (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 Tento kód generuje následující výstup:  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).  
  
 V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Konfigurace testu v oboru názvů](./sample-xml-file-test-configuration-in-a-namespace1.md).  
  
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
  
 Tento kód generuje následující výstup:  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Přehled standardních operátorů dotazůC#()](./standard-query-operators-overview.md)
- [Operace projekce (C#)](./projection-operations.md)
