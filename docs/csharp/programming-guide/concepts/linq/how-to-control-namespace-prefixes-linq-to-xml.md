---
title: 'Postupy: řízení Namespace předpony (C#) (technologie LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: af864139d56bd3ebb22cca6369b82539b9d007da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327750"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a>Postupy: řízení Namespace předpony (C#) (technologie LINQ to XML)
Toto téma popisuje, jak můžete řídit předpony oboru názvů při serializaci strom XML.  
  
 V mnoha situacích není potřeba řídit předpony oboru názvů.  
  
 Ale určitých nástrojích programovací XML vyžadovat konkrétní kontrolu nad předpony oboru názvů. Například je může být manipulace s stylů XSLT nebo XAML dokumentu, který obsahuje vložené XPath výrazy, které odkazují na předpony oboru názvů konkrétní; v takovém případě je důležité, aby dokumentu se Dal serializovat s konkrétní předpon.  
  
 Toto je nejčastější příčinou řízení předpony oboru názvů.  
  
 Řízení předpony oboru názvů jiné obvyklým důvodem je, že chcete uživatelům upravit v dokumentu XML ručně, a chcete vytvořit předpony oboru názvů, které jsou vhodné pro uživatele k zadání. Například můžete generování dokument XSD. Konvence pro schémata naznačují, že používáte buď `xs` nebo `xsd` jako předponu pro obor názvů schématu.  
  
 Chcete-li řídit předpony oboru názvů, vložte atributy, které deklarace oborů názvů. Pokud deklarace oborů názvů s konkrétní předpony [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se pokusí o respektovat předpony oboru názvů při serializaci.  
  
 Pokud chcete vytvořit atribut, který deklaruje předponu oboru názvů, vytvoření atribut, kde je obor názvů název atributu <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, a název atributu je Předpona oboru názvů. Hodnota atributu je identifikátor URI oboru názvů.  
  
## <a name="example"></a>Příklad  
 Tento příklad deklaruje dva obory názvů. Určuje, že `http://www.adventure-works.com` má předponu oboru názvů `aw`a že `www.fourthcoffee.com` má předponu oboru názvů `fc`.  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Viz také  
 [Práce s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
