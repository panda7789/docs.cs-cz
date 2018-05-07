---
title: 'Postupy: vyhledávání prvku s konkrétní podřízeným elementem (C#)'
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: e7528784f898f0f9ba84095b080eb82f8458424e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a>Postupy: vyhledávání prvku s konkrétní podřízeným elementem (C#)
Toto téma ukazuje, jak najít konkrétní element, který má podřízený element s konkrétní hodnotou.  
  
## <a name="example"></a>Příklad  
 Vyhledá v příkladu `Test` element, který má `CommandLine` podřízený element s hodnotou "Examp2.EXE".  
  
 Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Konfigurace testu (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 Tento kód vytvoří následující výstup:  
  
```  
0002  
0006  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro formát XML, který je v oboru názvů. Další informace najdete v tématu [práci s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Konfigurace testu v Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace1.md).  
  
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
  
 Tento kód vytvoří následující výstup:  
  
```  
0002  
0006  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [Základní dotazy (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Operace projekce (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
