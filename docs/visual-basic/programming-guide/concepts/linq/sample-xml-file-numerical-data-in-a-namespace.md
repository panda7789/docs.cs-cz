---
title: 'Ukázkový soubor XML: Číselná Data ve Namespace1'
ms.date: 07/20/2015
ms.assetid: f01cc0a1-fb55-4b42-8380-16f4be47d6f4
ms.openlocfilehash: 410e3df37c0e6f38f984e65cf3a9d4cc0a338110
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585234"
---
# <a name="sample-xml-file-numerical-data-in-a-namespace"></a><span data-ttu-id="90ff4-102">Ukázkový soubor XML: Číselná Data ve Namespace</span><span class="sxs-lookup"><span data-stu-id="90ff4-102">Sample XML File: Numerical Data in a Namespace</span></span>
<span data-ttu-id="90ff4-103">Následující soubor XML se používá v různých příkladů v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="90ff4-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="90ff4-104">Tento soubor obsahuje číselná data pro sčítání, agregovat a seskupení.</span><span class="sxs-lookup"><span data-stu-id="90ff4-104">This file contains numerical data for summing, averaging, and grouping.</span></span> <span data-ttu-id="90ff4-105">XML je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="90ff4-105">The XML is in a namespace.</span></span>  
  
## <a name="data"></a><span data-ttu-id="90ff4-106">Data</span><span class="sxs-lookup"><span data-stu-id="90ff4-106">Data</span></span>  
  
```xml  
<Root xmlns='http://www.adatum.com'>  
  <TaxRate>7.25</TaxRate>  
  <Data>  
    <Category>A</Category>  
    <Quantity>3</Quantity>  
    <Price>24.50</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>1</Quantity>  
    <Price>89.99</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>5</Quantity>  
    <Price>4.95</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>3</Quantity>  
    <Price>66.00</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>10</Quantity>  
    <Price>.99</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>15</Quantity>  
    <Price>29.00</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>8</Quantity>  
    <Price>6.99</Price>  
  </Data>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="90ff4-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90ff4-107">See also</span></span>
- [<span data-ttu-id="90ff4-108">Ukázkové dokumenty XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="90ff4-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
