---
title: 'Postupy: Předpony oboru názvů ovládacíhoC#prvku () (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 5b836be46001b660547532311b1b507ff234975f
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710161"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a>Postupy: Předpony oboru názvů ovládacíhoC#prvku () (LINQ to XML)
Toto téma popisuje, jak lze řídit předpony oboru názvů při serializaci stromu XML.  
  
 V mnoha situacích není nutné řídit předpony oboru názvů.  
  
 Nicméně některé programovací nástroje XML vyžadují konkrétní kontrolu předpon oboru názvů. Můžete například manipulovat se šablonou stylů XSLT nebo dokumentem XAML obsahující vložené výrazy XPath, které odkazují na konkrétní předpony oboru názvů. v takovém případě je důležité, aby byl dokument serializován s těmito konkrétními předponami.  
  
 Toto je nejběžnější důvod pro řídící předpony oboru názvů.  
  
 Dalším běžným důvodem pro kontrolní předpony oboru názvů je, že chcete, aby uživatelé upravili dokument XML ručně a chcete vytvořit předpony oboru názvů, které jsou vhodné pro uživatele, aby zadali. Můžete například vygenerovat dokument XSD. Konvence pro schémata naznačují, že `xs` použijete `xsd` předponu pro obor názvů schématu nebo.  
  
 Chcete-li řídit předpony oboru názvů, vložte atributy, které deklaruje obory názvů. Pokud deklarujete obory názvů se specifickými předponami, aplikace [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se pokusí při serializaci při serializaci vyhovět předponám oboru názvů.  
  
 Chcete-li vytvořit atribut, který deklaruje obor názvů s předponou, vytvoříte atribut, kde je <xref:System.Xml.Linq.XNamespace.Xmlns%2A>obor názvů názvu atributu, a název atributu je předpona oboru názvů. Hodnota atributu je identifikátor URI oboru názvů.  
  
## <a name="example"></a>Příklad  
 Tento příklad deklaruje dva obory názvů. Určuje, že `http://www.adventure-works.com` obor názvů má `aw`předponu a že `www.fourthcoffee.com` obor názvů má předponu `fc`.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Přehled oborů názvů (LINQ to XML)C#()](namespaces-overview-linq-to-xml.md)
