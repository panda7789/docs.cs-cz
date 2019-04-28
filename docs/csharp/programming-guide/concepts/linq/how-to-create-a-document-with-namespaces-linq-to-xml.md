---
title: 'Postupy: Vytvoření dokumentu s obory názvů (C#) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 9277253e885ac27ccb7d98221366d404ce0902e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668156"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a>Postupy: Vytvoření dokumentu s obory názvů (C#) (LINQ to XML)
Toto téma ukazuje, jak vytvářet dokumenty s obory názvů.  
  
## <a name="example"></a>Příklad  
 Chcete-li vytvořit element nebo atribut, který je v oboru názvů, nejprve deklarujete a inicializujete <xref:System.Xml.Linq.XNamespace> objektu. Potom použijte přetížení operátoru sčítání kombinovat obor názvů s místním názvem vyjádřená jako řetězec.  
  
 Následující příklad vytvoří dokument s jeden obor názvů. Ve výchozím nastavení [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializuje tento dokument s výchozí obor názvů.  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dokument s jeden obor názvů. Vytvoří také atribut, který deklaruje předponu oboru názvů z oboru názvů. Chcete-li vytvořit atribut, který deklaruje oboru názvů s předponou, vytvořte atribut kde název atributu je Předpona oboru názvů, a tento název se <xref:System.Xml.Linq.XNamespace.Xmlns%2A> oboru názvů. Hodnota tohoto atributu je identifikátor URI oboru názvů.  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje vytvoření dokumentu, který obsahuje dva obory názvů. Jeden je výchozí obor názvů. Další je obor názvů s předponou.  
  
 Zahrnutím atributy oboru názvů v kořenovém prvku serializují obory názvů tak, aby `http://www.adventure-works.com` je výchozí obor názvů a `www.fourthcoffee.com` serializovat s předponou "fc". Chcete-li vytvořit atribut, který deklaruje výchozí obor názvů, vytvořte atribut se názvu "xmlns", bez oboru názvů. Hodnota atributu je výchozí obor názvů identifikátoru URI.  
  
```csharp  
// The http://www.adventure-works.com namespace is forced to be the default namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute("xmlns", "http://www.adventure-works.com"),  
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
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dokument, který obsahuje dva obory názvů, jak u předpony oboru názvů.  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", aw.NamespaceName),  
    new XAttribute(XNamespace.Xmlns + "fc", fc.NamespaceName),  
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
  
## <a name="example"></a>Příklad  
 Jiný způsob k dosažení stejného výsledku je použít rozšířené názvy namísto deklarování a vytváření <xref:System.Xml.Linq.XNamespace> objektu.  
  
 Tento přístup má vliv na výkon. Pokaždé, když předáte řetězec, který obsahuje rozbalený název má [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] musíte analyzovat název, najít atomizované objekty obor názvů a vyhledání názvu atomizované objekty. Tento proces trvá čas procesoru. Pokud je důležitý výkon, může být vhodné k deklarování a použití <xref:System.Xml.Linq.XNamespace> objekt explicitně.  
  
 Pokud výkon je důležitý problém, přečtěte si téma [předběžná atomizace XName objektů (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) Další informace  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Viz také:

- [Práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
