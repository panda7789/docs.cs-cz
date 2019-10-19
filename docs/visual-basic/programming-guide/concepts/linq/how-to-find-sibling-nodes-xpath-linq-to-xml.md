---
title: 'Postupy: Vyhledání uzlů na stejné úrovni (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 73082738-2113-4438-8545-98d5df0927cb
ms.openlocfilehash: 9640c8708082965515d4b90c979519f7efdaa2ba
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582711"
---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="89528-102">Postupy: Vyhledání uzlů na stejné úrovni (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89528-102">How to: Find Sibling Nodes (XPath-LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="89528-103">Možná budete chtít najít všechny uzly na stejné úrovni, které mají konkrétní název.</span><span class="sxs-lookup"><span data-stu-id="89528-103">You might want to find all siblings of a node that have a specific name.</span></span> <span data-ttu-id="89528-104">Výsledná kolekce může zahrnovat kontextový uzel, pokud má uzel kontextu také konkrétní název.</span><span class="sxs-lookup"><span data-stu-id="89528-104">The resulting collection might include the context node if the context node also has the specific name.</span></span>

<span data-ttu-id="89528-105">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="89528-105">The XPath expression is:</span></span>

`../Book`

## <a name="example"></a><span data-ttu-id="89528-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="89528-106">Example</span></span>

<span data-ttu-id="89528-107">Tento příklad nejprve vyhledá prvek `Book` a pak najde všechny prvky na stejné úrovni s názvem `Book`.</span><span class="sxs-lookup"><span data-stu-id="89528-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`.</span></span> <span data-ttu-id="89528-108">Výsledná kolekce obsahuje kontextový uzel.</span><span class="sxs-lookup"><span data-stu-id="89528-108">The resulting collection includes the context node.</span></span>

<span data-ttu-id="89528-109">Tento příklad používá následující dokument XML: [ukázkový soubor XML: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="89528-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>

```vb
Dim books As XDocument = XDocument.Load("Books.xml")
Dim book As XElement = books.Root.<Book>.Skip(1).First()

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = book.Parent.<Book>

' XPath expression
Dim list2 As IEnumerable(Of XElement) = book.XPathSelectElements("../Book")

If list1.Count() = list2.Count() And _
        list1.Intersect(list2).Count() = list1.Count() Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
For Each el As XElement In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="89528-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="89528-110">This example produces the following output:</span></span>

```console
Results are identical
<Book id="bk101">
  <Author>Garghentini, Davide</Author>
  <Title>XML Developer's Guide</Title>
  <Genre>Computer</Genre>
  <Price>44.95</Price>
  <PublishDate>2000-10-01</PublishDate>
  <Description>An in-depth look at creating applications
      with XML.</Description>
</Book>
<Book id="bk102">
  <Author>Garcia, Debra</Author>
  <Title>Midnight Rain</Title>
  <Genre>Fantasy</Genre>
  <Price>5.95</Price>
  <PublishDate>2000-12-16</PublishDate>
  <Description>A former architect battles corporate zombies,
      an evil sorceress, and her own childhood to become queen
      of the world.</Description>
</Book>
```

## <a name="see-also"></a><span data-ttu-id="89528-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89528-111">See also</span></span>

- [<span data-ttu-id="89528-112">LINQ to XML pro uživatele XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89528-112">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
