---
title: Jak najít atribut nadřazené položky (XPath-LINQ to XML) (C#)
description: Přečtěte si, jak najít atribut nadřazeného elementu. Podívejte se na příklad kódu, který používá ukázkový dokument XML.
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: 03344bb66f617970d9598c91366eb7d69514397a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303293"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a>Jak najít atribut nadřazené položky (XPath-LINQ to XML) (C#)

Toto téma ukazuje, jak přejít na nadřazený prvek a najít atribut.

Výraz XPath je:

`../@id`

## <a name="example"></a>Příklad

Tento příklad nejprve vyhledá `Author` prvek. Pak najde `id` atribut nadřazeného elementu.

Tento příklad používá následující dokument XML: [ukázkový soubor XML: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).

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

```output
Results are identical
id="bk101"
```
