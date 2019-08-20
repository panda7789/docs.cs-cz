---
title: 'Postupy: Najít atribut nadřazené položky (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: 2e6c124d2653fb4426b3abb693f0b58daa5413c2
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593611"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a>Postupy: Najít atribut nadřazené položky (XPath-LINQ to XML) (C#)

Toto téma ukazuje, jak přejít na nadřazený prvek a najít atribut.

Výraz XPath je:

`../@id`

## <a name="example"></a>Příklad

Tento příklad nejprve vyhledá `Author` prvek. Pak najde `id` atribut nadřazeného elementu.

V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Books (LINQ to XML](./sample-xml-file-books-linq-to-xml.md)).

```csharp
XDocument books = XDocument.Load("Books.xml");

XElement author =
    books
    .Root
    .Element("Book")
    .Element("Author");

// LINQ to XML query
XAttribute att1 =
    author
    .Parent
    .Attribute("id");

// XPath expression
XAttribute att2 = ((IEnumerable)author.XPathEvaluate("../@id")).Cast<XAttribute>().First();

if (att1 == att2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(att1);
```

Tento příklad vytvoří následující výstup:

```
Results are identical
id="bk101"
```
