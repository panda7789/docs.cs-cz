---
title: Jak řídit předpony oboru názvů (C#) (LINQ to XML)
description: Naučte se řídit předpony oboru názvů při serializaci stromu XML v LINQ to XML v jazyce C#. Některé situace vyžadují kontrolu předpon oboru názvů.
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: b0c5cbfa7488f3a7105595830ef6765e6bfb1f12
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105300"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a>Jak řídit předpony oboru názvů (C#) (LINQ to XML)
Toto téma popisuje, jak lze řídit předpony oboru názvů při serializaci stromu XML.  
  
 V mnoha situacích není nutné řídit předpony oboru názvů.  
  
 Nicméně některé programovací nástroje XML vyžadují konkrétní kontrolu předpon oboru názvů. Můžete například manipulovat se šablonou stylů XSLT nebo dokumentem XAML obsahující vložené výrazy XPath, které odkazují na konkrétní předpony oboru názvů. v takovém případě je důležité, aby byl dokument serializován s těmito konkrétními předponami.  
  
 Toto je nejběžnější důvod pro řídící předpony oboru názvů.  
  
 Dalším běžným důvodem pro kontrolní předpony oboru názvů je, že chcete, aby uživatelé upravili dokument XML ručně a chcete vytvořit předpony oboru názvů, které jsou vhodné pro uživatele, aby zadali. Můžete například vygenerovat dokument XSD. Konvence pro schémata naznačují, že použijete `xs` `xsd` předponu pro obor názvů schématu nebo.  
  
 Chcete-li řídit předpony oboru názvů, vložte atributy, které deklaruje obory názvů. Pokud deklarujete obory názvů se specifickými předponami, aplikace [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se pokusí při serializaci při serializaci vyhovět předponám oboru názvů.  
  
 Chcete-li vytvořit atribut, který deklaruje obor názvů s předponou, vytvoříte atribut, kde je obor názvů názvu atributu <xref:System.Xml.Linq.XNamespace.Xmlns%2A> , a název atributu je předpona oboru názvů. Hodnota atributu je identifikátor URI oboru názvů.  
  
## <a name="example"></a>Příklad  
 Tento příklad deklaruje dva obory názvů. Určuje, že `http://www.adventure-works.com` obor názvů má předponu `aw` a že `www.fourthcoffee.com` obor názvů má předponu `fc` .  
  
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

- [Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)
