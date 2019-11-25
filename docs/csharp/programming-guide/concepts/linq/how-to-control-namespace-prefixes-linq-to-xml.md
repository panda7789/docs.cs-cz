---
title: Jak řídit předpony oboru názvů (C#) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 9f43c0804d8c830fa75f1e1390cb578c5f5d5106
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141377"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a>Jak řídit předpony oboru názvů (C#) (LINQ to XML)
Toto téma popisuje, jak lze řídit předpony oboru názvů při serializaci stromu XML.  
  
 V mnoha situacích není nutné řídit předpony oboru názvů.  
  
 Nicméně některé programovací nástroje XML vyžadují konkrétní kontrolu předpon oboru názvů. Můžete například manipulovat se šablonou stylů XSLT nebo dokumentem XAML obsahující vložené výrazy XPath, které odkazují na konkrétní předpony oboru názvů. v takovém případě je důležité, aby byl dokument serializován s těmito konkrétními předponami.  
  
 Toto je nejběžnější důvod pro řídící předpony oboru názvů.  
  
 Dalším běžným důvodem pro kontrolní předpony oboru názvů je, že chcete, aby uživatelé upravili dokument XML ručně a chcete vytvořit předpony oboru názvů, které jsou vhodné pro uživatele, aby zadali. Můžete například vygenerovat dokument XSD. Konvence pro schémata naznačují, že jako předponu pro obor názvů schématu používáte buď `xs`, nebo `xsd`.  
  
 Chcete-li řídit předpony oboru názvů, vložte atributy, které deklaruje obory názvů. Pokud deklarujete obory názvů se specifickými předponami, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se pokusí při serializaci akceptovat předpony oboru názvů.  
  
 Chcete-li vytvořit atribut, který deklaruje obor názvů s předponou, vytvoříte atribut, kde je obor názvů názvu atributu <xref:System.Xml.Linq.XNamespace.Xmlns%2A>a název atributu je předpona oboru názvů. Hodnota atributu je identifikátor URI oboru názvů.  
  
## <a name="example"></a>Příklad  
 Tento příklad deklaruje dva obory názvů. Určuje, že obor názvů `http://www.adventure-works.com` má předponu `aw`a že obor názvů `www.fourthcoffee.com` má předponu `fc`.  
  
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
