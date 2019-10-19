---
title: Název proměnné rozsahu lze odvodit jen z jednoduchého nebo kvalifikovaného názvu bez argumentů.
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: ca50ddd86cfbba8db0148ed315645714acabc18d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582426"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="907d3-102">Název proměnné rozsahu lze odvodit jen z jednoduchého nebo kvalifikovaného názvu bez argumentů.</span><span class="sxs-lookup"><span data-stu-id="907d3-102">Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>

<span data-ttu-id="907d3-103">Programovací prvek, který používá jeden nebo více argumentů, je obsažen v dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="907d3-103">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="907d3-104">Kompilátor nemůže odvodit proměnnou rozsahu z tohoto programovacího prvku.</span><span class="sxs-lookup"><span data-stu-id="907d3-104">The compiler is unable to infer a range variable from that programming element.</span></span>

<span data-ttu-id="907d3-105">**ID chyby:** BC36599</span><span class="sxs-lookup"><span data-stu-id="907d3-105">**Error ID:** BC36599</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="907d3-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="907d3-106">To correct this error</span></span>

<span data-ttu-id="907d3-107">Zadejte explicitní název proměnné pro programový element, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="907d3-107">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>

```vb
Dim query = From var1 In collection1
            Select VariableAlias= SampleFunction(var1), var1
```

## <a name="see-also"></a><span data-ttu-id="907d3-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="907d3-108">See also</span></span>

- [<span data-ttu-id="907d3-109">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="907d3-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="907d3-110">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="907d3-110">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
