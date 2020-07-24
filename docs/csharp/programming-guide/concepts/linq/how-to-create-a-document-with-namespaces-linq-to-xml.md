---
title: Postup vytvoření dokumentu s obory názvů (C#) (LINQ to XML)
description: Naučte se, jak vytvořit dokument s oborem názvů v LINQ to XML v jazyce C# pomocí objektu XNamespace pro kombinování oboru názvů s místním názvem.
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 6472baefc73285af1c6dca0bfe7d874003940fc4
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103399"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a>Postup vytvoření dokumentu s obory názvů (C#) (LINQ to XML)
V tomto tématu se dozvíte, jak vytvářet dokumenty s obory názvů.  
  
## <a name="example"></a>Příklad  
 Chcete-li vytvořit element nebo atribut, který je v oboru názvů, nejprve deklarujete a inicializujete <xref:System.Xml.Linq.XNamespace> objekt. Pak použijte přetížení operátoru sčítání ke kombinování oboru názvů s místním názvem vyjádřeným jako řetězec.  
  
 Následující příklad vytvoří dokument s jedním oborem názvů. Ve výchozím nastavení [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Tento dokument zaserializace s výchozím oborem názvů.  
  
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
 Následující příklad vytvoří dokument s jedním oborem názvů. Vytvoří také atribut, který deklaruje obor názvů s předponou oboru názvů. Chcete-li vytvořit atribut, který deklaruje obor názvů s předponou, vytvoříte atribut, kde název atributu je předpona oboru názvů a tento název je v <xref:System.Xml.Linq.XNamespace.Xmlns%2A> oboru názvů. Hodnota tohoto atributu je identifikátor URI oboru názvů.  
  
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
 Následující příklad ukazuje vytvoření dokumentu, který obsahuje dva obory názvů. Jedním z nich je výchozí obor názvů. Další je obor názvů s předponou.  
  
 Zahrnutím atributů oboru názvů do kořenového elementu jsou obory názvů serializovány, což `http://www.adventure-works.com` je výchozí obor názvů a `www.fourthcoffee.com` je serializován s předponou "FC". Chcete-li vytvořit atribut, který deklaruje výchozí obor názvů, vytvoříte atribut s názvem "xmlns" bez oboru názvů. Hodnota atributu je výchozí identifikátor URI oboru názvů.  
  
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
 Následující příklad vytvoří dokument, který obsahuje dva obory názvů, s předpony oboru názvů.  
  
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
 Dalším způsobem, jak dosáhnout stejného výsledku, je použít místo deklarace a vytvoření objektu rozšířené názvy <xref:System.Xml.Linq.XNamespace> .  
  
 Tento přístup má vliv na výkon. Pokaždé, když předáte řetězec, který obsahuje rozbalený název [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] musí analyzovat název, najít atomické obor názvů a najít název Atom. Tento proces trvá čas procesoru. Pokud je důležitý výkon, možná budete chtít explicitně deklarovat a použít <xref:System.Xml.Linq.XNamespace> objekt.  
  
 Pokud je výkon důležitý, přečtěte si téma [předběžného vystavování objektů XName (LINQ to XML) (C#)](./pre-atomization-of-xname-objects-linq-to-xml.md) , kde najdete další informace.  
  
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
  
## <a name="see-also"></a>Viz také

- [Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)
