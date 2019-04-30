---
title: Název proměnné rozsahu lze odvodit jen z jednoduchého nebo kvalifikovaného názvu bez argumentů.
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: a0b5633bb0efb3c67f73810552ef9a14ac3d0c70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934274"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="1af65-102">Název proměnné rozsahu lze odvodit jen z jednoduchého nebo kvalifikovaného názvu bez argumentů.</span><span class="sxs-lookup"><span data-stu-id="1af65-102">Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="1af65-103">Programový element, který přijímá jeden nebo více argumentů je zahrnutý v dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="1af65-103">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="1af65-104">Kompilátor nedokáže odvodit proměnnou rozsahu z této programovací element.</span><span class="sxs-lookup"><span data-stu-id="1af65-104">The compiler is unable to infer a range variable from that programming element.</span></span>  
  
 <span data-ttu-id="1af65-105">**ID chyby:** BC36599</span><span class="sxs-lookup"><span data-stu-id="1af65-105">**Error ID:** BC36599</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1af65-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="1af65-106">To correct this error</span></span>  
  
1. <span data-ttu-id="1af65-107">Zadejte explicitní název proměnné pro programový element, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="1af65-107">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a><span data-ttu-id="1af65-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1af65-108">See also</span></span>

- [<span data-ttu-id="1af65-109">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1af65-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="1af65-110">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="1af65-110">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
