---
title: Jak najít atribut nadřazeného (XPath-LINQ na XML) (C#)
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: bfe7554a5c767adde5e7170c8e1ea0537155f6df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141172"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="f89b8-102">Jak najít atribut nadřazeného (XPath-LINQ na XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f89b8-102">How to find an attribute of the parent (XPath-LINQ to XML) (C#)</span></span>

<span data-ttu-id="f89b8-103">Toto téma ukazuje, jak přejít na nadřazený prvek a najít jeho atribut.</span><span class="sxs-lookup"><span data-stu-id="f89b8-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>

<span data-ttu-id="f89b8-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="f89b8-104">The XPath expression is:</span></span>

`../@id`

## <a name="example"></a><span data-ttu-id="f89b8-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="f89b8-105">Example</span></span>

<span data-ttu-id="f89b8-106">Tento příklad nejprve `Author` najde prvek.</span><span class="sxs-lookup"><span data-stu-id="f89b8-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="f89b8-107">Potom najde `id` atribut nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="f89b8-107">It then finds the `id` attribute of the parent element.</span></span>

<span data-ttu-id="f89b8-108">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Books (LINQ to XML).](./sample-xml-file-books-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="f89b8-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>

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

<span data-ttu-id="f89b8-109">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f89b8-109">This example produces the following output:</span></span>

```output
Results are identical
id="bk101"
```
