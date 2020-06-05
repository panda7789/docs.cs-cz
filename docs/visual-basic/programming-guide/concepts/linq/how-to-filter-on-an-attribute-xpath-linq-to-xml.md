---
title: 'Postupy: Filtrování atributu (XPath – LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: ffefb9d6-45ec-4677-a396-dd9c2b36298f
ms.openlocfilehash: 5bc0a621f0d3bb8e22701440383cdac54c7be51b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394502"
---
# <a name="how-to-filter-on-an-attribute-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="475f7-102">Postupy: filtrování atributu (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="475f7-102">How to: Filter on an Attribute (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="475f7-103">Toto téma ukazuje, jak získat odvozené prvky se zadaným názvem a s atributem se zadanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="475f7-103">This topic shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="475f7-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="475f7-104">The XPath expression is:</span></span>  
  
 `.//Address[@Type='Shipping']`  
  
## <a name="example"></a><span data-ttu-id="475f7-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="475f7-105">Example</span></span>  
 <span data-ttu-id="475f7-106">Tento příklad vyhledá všechny prvky následníků s názvem `Address` a s `Type` atributem s hodnotou "expedice".</span><span class="sxs-lookup"><span data-stu-id="475f7-106">This example finds all descendants elements with the name of `Address`, and with a `Type` attribute with a value of "Shipping".</span></span>  
  
 <span data-ttu-id="475f7-107">Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="475f7-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    From el In po...<Address> _  
    Where el.@Type = "Shipping" _  
    Select el  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = _  
    po.XPathSelectElements(".//Address[@Type='Shipping']")  
  
If (list1.Count = list2.Count And _  
        list1.Intersect(list2).Count() = list1.Count()) Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="475f7-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="475f7-108">This example produces the following output:</span></span>  
  
```console
Results are identical  
<Address Type="Shipping">  
  <Name>Ellen Adams</Name>  
  <Street>123 Maple Street</Street>  
  <City>Mill Valley</City>  
  <State>CA</State>  
  <Zip>10999</Zip>  
  <Country>USA</Country>  
</Address>  
<Address Type="Shipping">  
  <Name>Cristian Osorio</Name>  
  <Street>456 Main Street</Street>  
  <City>Buffalo</City>  
  <State>NY</State>  
  <Zip>98112</Zip>  
  <Country>USA</Country>  
</Address>  
<Address Type="Shipping">  
  <Name>Jessica Arnold</Name>  
  <Street>4055 Madison Ave</Street>  
  <City>Seattle</City>  
  <State>WA</State>  
  <Zip>98112</Zip>  
  <Country>USA</Country>  
</Address>  
```  
  
## <a name="see-also"></a><span data-ttu-id="475f7-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="475f7-109">See also</span></span>

- [<span data-ttu-id="475f7-110">LINQ to XML pro uživatele XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="475f7-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
