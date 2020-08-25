---
title: IsNot – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- comparison operators [Visual Basic]
- TypeOf...IsNot expression
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ea978f8874cee20fb3a005189fd846f7564da777
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811038"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="407db-102">IsNot – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="407db-102">IsNot Operator (Visual Basic)</span></span>

<span data-ttu-id="407db-103">Porovná dvě proměnné odkazu na objekt.</span><span class="sxs-lookup"><span data-stu-id="407db-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="407db-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="407db-104">Syntax</span></span>

```vb
result = object1 IsNot object2
```

## <a name="parts"></a><span data-ttu-id="407db-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="407db-105">Parts</span></span>

- `result`

  <span data-ttu-id="407db-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="407db-106">Required.</span></span> <span data-ttu-id="407db-107">`Boolean`Hodnota.</span><span class="sxs-lookup"><span data-stu-id="407db-107">A `Boolean` value.</span></span>

- `object1`

  <span data-ttu-id="407db-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="407db-108">Required.</span></span> <span data-ttu-id="407db-109">Jakákoli `Object` proměnná nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="407db-109">Any `Object` variable or expression.</span></span>

- `object2`

  <span data-ttu-id="407db-110">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="407db-110">Required.</span></span> <span data-ttu-id="407db-111">Jakákoli `Object` proměnná nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="407db-111">Any `Object` variable or expression.</span></span>

## <a name="remarks"></a><span data-ttu-id="407db-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="407db-112">Remarks</span></span>

<span data-ttu-id="407db-113">`IsNot`Operátor určuje, zda dva odkazy na objekt odkazují na různé objekty.</span><span class="sxs-lookup"><span data-stu-id="407db-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="407db-114">Ale neprovádí porovnávání hodnot.</span><span class="sxs-lookup"><span data-stu-id="407db-114">However, it doesn't perform value comparisons.</span></span> <span data-ttu-id="407db-115">Pokud `object1` a `object2` obě odkazují na přesnou stejnou instanci objektu, `result` je `False` . Pokud ne, `result` je `True` .</span><span class="sxs-lookup"><span data-stu-id="407db-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they don't, `result` is `True`.</span></span>

<span data-ttu-id="407db-116">`IsNot` je opakem `Is` operátoru.</span><span class="sxs-lookup"><span data-stu-id="407db-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="407db-117">Výhodou `IsNot` je, že se můžete vyhnout nevhodným syntaxem s `Not` a `Is` , což může být obtížné ho přečíst.</span><span class="sxs-lookup"><span data-stu-id="407db-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>

 <span data-ttu-id="407db-118">Operátory a můžete použít `Is` `IsNot` k otestování objektů s časnou vazbou i s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="407db-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>

## <a name="example"></a><span data-ttu-id="407db-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="407db-119">Example</span></span>

<span data-ttu-id="407db-120">Následující příklad kódu používá `Is` operátor i `IsNot` operátor k provedení stejného porovnání.</span><span class="sxs-lookup"><span data-stu-id="407db-120">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>

[!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="use-typeof-operator-with-isnot-operator"></a><span data-ttu-id="407db-121">Použití operátoru TypeOf s operátorem IsNot</span><span class="sxs-lookup"><span data-stu-id="407db-121">Use TypeOf operator with IsNot operator</span></span>

<span data-ttu-id="407db-122">Počínaje Visual Basic 14 můžete `TypeOf` operátor s `IsNot` operátorem použít k otestování, zda objekt není kompatibilní s datovým typem. *not*</span><span class="sxs-lookup"><span data-stu-id="407db-122">Starting with Visual Basic 14, you can use the `TypeOf` operator with the `IsNot` operator to test whether an object is *not* compatible with a data type.</span></span> <span data-ttu-id="407db-123">Příklad:</span><span class="sxs-lookup"><span data-stu-id="407db-123">For example:</span></span>

```vb
If TypeOf sender IsNot Button Then
```

## <a name="see-also"></a><span data-ttu-id="407db-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="407db-124">See also</span></span>

- [<span data-ttu-id="407db-125">Is – operátor</span><span class="sxs-lookup"><span data-stu-id="407db-125">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="407db-126">TypeOf – operátor</span><span class="sxs-lookup"><span data-stu-id="407db-126">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="407db-127">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="407db-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="407db-128">Postupy: Test, zda jsou dva objekty stejné.</span><span class="sxs-lookup"><span data-stu-id="407db-128">How to: Test Whether Two Objects Are the Same</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
