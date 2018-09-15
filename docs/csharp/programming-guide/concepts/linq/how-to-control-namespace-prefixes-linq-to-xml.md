---
title: 'Postupy: řízení předpon Namespace (C#) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: dd2a91fde868425cadbc395d6db0f913e2be600f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45649702"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a>Postupy: řízení předpon Namespace (C#) (LINQ to XML)
Toto téma popisuje, jak můžete řídit předpony oboru názvů při serializaci stromu XML.  
  
 V mnoha situacích není nutné k řízení předpon názvového prostoru.  
  
 Nicméně některé programovací nástroje XML vyžadují určitý ovládací prvek předpony oboru názvů. Například můžete může být zpracování šablony stylů XSLT nebo dokumentu XAML, který obsahuje vložené výrazy XPath, které odkazují na konkrétní obor názvů předpony; v takovém případě je důležité, že dokument Dal serializovat s příznakem tyto konkrétní předpony.  
  
 Toto je nejběžnějším důvodem pro řízení předpon názvového prostoru.  
  
 Dalším běžným důvodem pro řízení předpon názvového prostoru je, že chcete uživatelům ručně upravit dokument XML, a chcete vytvořit obor názvů předpony, které jsou vhodné pro uživatele, aby. Může být například generování XSD dokumentu. Konvence pro schémata doporučujeme použít buď `xs` nebo `xsd` jako předponu pro obor názvů schématu.  
  
 Chcete-li řízení předpon názvového prostoru, vložte atributy, které deklarace oborů názvů. Pokud deklarujete obory názvů s konkrétní předpony [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se pokusí o případném dalším sdílení dodržovat předpony oboru názvů při serializaci.  
  
 Chcete-li vytvořit atribut, který deklaruje oboru názvů s předponou, vytvořte atribut kde obor názvů název atributu je <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, a název atributu je Předpona oboru názvů. Hodnota atributu je identifikátor URI oboru názvů.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu deklaruje dva obory názvů. Určuje, že `http://www.adventure-works.com` obor názvů má předponu `aw`a že `www.fourthcoffee.com` obor názvů má předponu `fc`.  
  
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

- [Práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
