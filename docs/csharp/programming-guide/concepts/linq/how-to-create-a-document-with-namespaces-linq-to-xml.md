---
title: Jak vytvořit dokument s obory názvů (C#) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 429b0b0b41f2201b983f931e469b25ff406b91ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141335"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a>Jak vytvořit dokument s obory názvů (C#) (LINQ to XML)
Toto téma ukazuje, jak vytvořit dokumenty pomocí oborů názvů.  
  
## <a name="example"></a>Příklad  
 Chcete-li vytvořit prvek nebo atribut, který je v oboru názvů, nejprve deklarovat a inicializovat <xref:System.Xml.Linq.XNamespace> objekt. Potom použít přetížení operátoru sčítání kombinovat obor názvů s místním názvem, vyjádřené jako řetězec.  
  
 Následující příklad vytvoří dokument s jedním oborem názvů. Ve výchozím [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nastavení serializuje tento dokument s výchozím oborem názvů.  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dokument s jedním oborem názvů. Vytvoří také atribut, který deklaruje obor názvů s předponou oboru názvů. Chcete-li vytvořit atribut, který deklaruje obor názvů s předponou, vytvořte atribut, kde název <xref:System.Xml.Linq.XNamespace.Xmlns%2A> atributu je předpona oboru názvů a tento název je v oboru názvů. Hodnota tohoto atributu je identifikátor URI oboru názvů.  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje vytvoření dokumentu, který obsahuje dva obory názvů. Jedním z nich je výchozí obor názvů. Dalším je obor názvů s předponou.  
  
 Zahrnutím atributů oboru názvů do kořenového prvku jsou `http://www.adventure-works.com` obory názvů serializovány tak, aby se výchozí obor názvů uplatňovaly, a `www.fourthcoffee.com` jsou serializovány s předponou "fc". Chcete-li vytvořit atribut, který deklaruje výchozí obor názvů, vytvořte atribut s názvem xmlns bez oboru názvů. Hodnota atributu je výchozí identifikátor URI oboru názvů.  
  
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
  
 Tento příklad vytváří následující výstup:  
  
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
 Následující příklad vytvoří dokument, který obsahuje dva obory názvů, a to jak s předčíslím oboru názvů.  
  
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
  
## <a name="example"></a>Příklad  
 Dalším způsobem, jak dosáhnout stejného výsledku, je použít <xref:System.Xml.Linq.XNamespace> rozšířené názvy namísto deklarování a vytváření objektu.  
  
 Tento přístup má vliv na výkon. Pokaždé, když předáte řetězec, který [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obsahuje rozšířený název , musí analyzovat název, najít atomizovaný obor názvů a najít atomizovaný název. Tento proces trvá čas procesoru. Pokud je výkon důležitý, můžete explicitně <xref:System.Xml.Linq.XNamespace> deklarovat a používat objekt.  
  
 Pokud je výkon důležitý, další informace naleznete [v tématu Pre-Atomization of XName Objects (LINQ to XML) (C#)](./pre-atomization-of-xname-objects-linq-to-xml.md)  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Viz také

- [Obory názvů – přehled (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)
