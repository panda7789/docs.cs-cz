---
title: Jak řídit předpony oboru názvů (C#) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 9f43c0804d8c830fa75f1e1390cb578c5f5d5106
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141377"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a>Jak řídit předpony oboru názvů (C#) (LINQ to XML)
Toto téma popisuje, jak můžete řídit předpony oboru názvů při serializaci stromu XML.  
  
 V mnoha situacích není nutné řídit předpony oboru názvů.  
  
 Některé programovací nástroje XML však vyžadují zvláštní řízení předpon oboru názvů. Můžete například manipulovat se šablonou stylů XSLT nebo dokumentem XAML, který obsahuje vložené výrazy XPath, které odkazují na konkrétní předpony oboru názvů; v tomto případě je důležité, aby byl dokument serializován s těmito specifickými předčíslími.  
  
 Toto je nejčastější důvod pro řízení předpon oboru názvů.  
  
 Dalším běžným důvodem pro řízení předpon oboru názvů je, že chcete, aby uživatelé ručně upravovali dokument XML, a chcete vytvořit předpony oboru názvů, které jsou vhodné pro uživatele k zadání. Například můžete generovat dokument XSD. Konvence pro schémata naznačují, že `xs` používáte buď nebo `xsd` jako předponu pro obor názvů schématu.  
  
 Chcete-li řídit předpony oboru názvů, vložte atributy, které deklarují obory názvů. Pokud deklarujete obory [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] názvů s určitými předčíslími, pokusíte se respektovat předpony oboru názvů při serializaci.  
  
 Chcete-li vytvořit atribut, který deklaruje obor názvů s předponou, vytvořte <xref:System.Xml.Linq.XNamespace.Xmlns%2A>atribut, ve kterém je obor názvů názvu atributu a název atributu je předpona oboru názvů. Hodnota atributu je identifikátor URI oboru názvů.  
  
## <a name="example"></a>Příklad  
 Tento příklad deklaruje dva obory názvů. Určuje, že `http://www.adventure-works.com` obor názvů má předponu `aw`a `www.fourthcoffee.com` že obor názvů `fc`má předponu .  
  
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
  
 Tento příklad vytváří následující výstup:  
  
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

- [Obory názvů – přehled (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)
