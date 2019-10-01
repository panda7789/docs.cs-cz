---
title: IsNot – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 32e8f9532244679d2994b0e3d98279d75f7e77b4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701041"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="bf64b-102">IsNot – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf64b-102">IsNot Operator (Visual Basic)</span></span>

<span data-ttu-id="bf64b-103">Porovná dvě proměnné odkazu na objekt.</span><span class="sxs-lookup"><span data-stu-id="bf64b-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="bf64b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf64b-104">Syntax</span></span>

```vb
result = object1 IsNot object2
```

## <a name="parts"></a><span data-ttu-id="bf64b-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="bf64b-105">Parts</span></span>
 <span data-ttu-id="bf64b-106">Vyžaduje se `result`.</span><span class="sxs-lookup"><span data-stu-id="bf64b-106">`result` Required.</span></span> <span data-ttu-id="bf64b-107">Hodnota `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="bf64b-107">A `Boolean` value.</span></span>

 <span data-ttu-id="bf64b-108">Vyžaduje se `object1`.</span><span class="sxs-lookup"><span data-stu-id="bf64b-108">`object1` Required.</span></span> <span data-ttu-id="bf64b-109">Jakákoli proměnná nebo výraz `Object`.</span><span class="sxs-lookup"><span data-stu-id="bf64b-109">Any `Object` variable or expression.</span></span>

 <span data-ttu-id="bf64b-110">Vyžaduje se `object2`.</span><span class="sxs-lookup"><span data-stu-id="bf64b-110">`object2` Required.</span></span> <span data-ttu-id="bf64b-111">Jakákoli proměnná nebo výraz `Object`.</span><span class="sxs-lookup"><span data-stu-id="bf64b-111">Any `Object` variable or expression.</span></span>

## <a name="remarks"></a><span data-ttu-id="bf64b-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf64b-112">Remarks</span></span>
 <span data-ttu-id="bf64b-113">Operátor `IsNot` určuje, zda dva odkazy na objekt odkazují na různé objekty.</span><span class="sxs-lookup"><span data-stu-id="bf64b-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="bf64b-114">Ale neprovádí porovnávání hodnot.</span><span class="sxs-lookup"><span data-stu-id="bf64b-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="bf64b-115">Pokud `object1` a `object2` odkazují na přesnou stejnou instanci objektu, `result` je `False`; Pokud ne, `result` je `True`.</span><span class="sxs-lookup"><span data-stu-id="bf64b-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>

 <span data-ttu-id="bf64b-116">`IsNot` je opakem operátoru `Is`.</span><span class="sxs-lookup"><span data-stu-id="bf64b-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="bf64b-117">Výhodou `IsNot` je, že se můžete vyhnout nevhodným syntaxem `Not` a `Is`, což může být obtížné přečíst.</span><span class="sxs-lookup"><span data-stu-id="bf64b-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>

 <span data-ttu-id="bf64b-118">Operátory `Is` a `IsNot` můžete použít k otestování objektů s časnou vazbou i s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="bf64b-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>

## <a name="example"></a><span data-ttu-id="bf64b-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="bf64b-119">Example</span></span>
 <span data-ttu-id="bf64b-120">Následující příklad kódu používá operátor `Is` a operátor `IsNot` k provedení stejného porovnání.</span><span class="sxs-lookup"><span data-stu-id="bf64b-120">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a><span data-ttu-id="bf64b-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf64b-121">See also</span></span>

- [<span data-ttu-id="bf64b-122">Operátor Is</span><span class="sxs-lookup"><span data-stu-id="bf64b-122">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="bf64b-123">Operátor Typeof</span><span class="sxs-lookup"><span data-stu-id="bf64b-123">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="bf64b-124">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bf64b-124">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="bf64b-125">Postupy: Test, zda jsou dva objekty stejné</span><span class="sxs-lookup"><span data-stu-id="bf64b-125">How to: Test Whether Two Objects Are the Same</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
