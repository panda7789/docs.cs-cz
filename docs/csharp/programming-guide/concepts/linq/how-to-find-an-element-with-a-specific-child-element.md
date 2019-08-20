---
title: 'Postupy: Vyhledání elementu s konkrétním podřízeným elementem (C#)'
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 80539c7ccd21bc38967479d7b724e6f3361d24ac
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593545"
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
  
```  
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
  
```  
0002  
0006  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Přehled standardních operátorů dotazůC#()](./standard-query-operators-overview.md)
- [Operace projekce (C#)](./projection-operations.md)
