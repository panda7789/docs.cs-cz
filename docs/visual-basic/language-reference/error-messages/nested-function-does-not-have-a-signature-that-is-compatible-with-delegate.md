---
title: Vnořená funkce nemá stejný podpis kompatibilní s delegátem '<delegatename>'.
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 28d07f01c0fd467cb68d73749988273eee95edf4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409423"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a><span data-ttu-id="bde69-102">Vnořená funkce nemá stejný podpis kompatibilní s delegátem '\<delegatename>'.</span><span class="sxs-lookup"><span data-stu-id="bde69-102">Nested function does not have a signature that is compatible with delegate '\<delegatename>'</span></span>

<span data-ttu-id="bde69-103">K delegátovi, který má nekompatibilní signaturu, byl přiřazen výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="bde69-103">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="bde69-104">Například v následujícím kódu `Del` má delegát dva celočíselné parametry.</span><span class="sxs-lookup"><span data-stu-id="bde69-104">For example, in the following code, delegate `Del` has two integer parameters.</span></span>

```vb
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer
```

<span data-ttu-id="bde69-105">Tato chyba je vyvolána, pokud je výraz lambda s jedním argumentem deklarován jako typ `Del` :</span><span class="sxs-lookup"><span data-stu-id="bde69-105">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>

```vb
' Neither of these is valid.
' Dim lambda1 As Del = Function(n As Integer) n + 1
' Dim lambda2 As Del = Function(n) n + 1
```

<span data-ttu-id="bde69-106">**ID chyby:** BC36532</span><span class="sxs-lookup"><span data-stu-id="bde69-106">**Error ID:** BC36532</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="bde69-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="bde69-107">To correct this error</span></span>

<span data-ttu-id="bde69-108">Upravte buď definici delegáta, nebo přiřazený výraz lambda tak, aby signatury byly kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="bde69-108">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>

## <a name="see-also"></a><span data-ttu-id="bde69-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="bde69-109">See also</span></span>

- [<span data-ttu-id="bde69-110">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="bde69-110">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="bde69-111">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="bde69-111">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
