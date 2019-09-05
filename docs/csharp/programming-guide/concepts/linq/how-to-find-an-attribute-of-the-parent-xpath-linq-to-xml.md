---
title: 'Postupy: Najít atribut nadřazené položky (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: aa602f6876b014c48a73dea9b2ff42eb953e5c4c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253776"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="462f6-102">Postupy: Najít atribut nadřazené položky (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="462f6-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (C#)</span></span>

<span data-ttu-id="462f6-103">Toto téma ukazuje, jak přejít na nadřazený prvek a najít atribut.</span><span class="sxs-lookup"><span data-stu-id="462f6-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>

<span data-ttu-id="462f6-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="462f6-104">The XPath expression is:</span></span>

`../@id`

## <a name="example"></a><span data-ttu-id="462f6-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="462f6-105">Example</span></span>

<span data-ttu-id="462f6-106">Tento příklad nejprve vyhledá `Author` prvek.</span><span class="sxs-lookup"><span data-stu-id="462f6-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="462f6-107">Pak najde `id` atribut nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="462f6-107">It then finds the `id` attribute of the parent element.</span></span>

<span data-ttu-id="462f6-108">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Books (LINQ to XML](./sample-xml-file-books-linq-to-xml.md)).</span><span class="sxs-lookup"><span data-stu-id="462f6-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>

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

<span data-ttu-id="462f6-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="462f6-109">This example produces the following output:</span></span>

```output
Results are identical
id="bk101"
```
