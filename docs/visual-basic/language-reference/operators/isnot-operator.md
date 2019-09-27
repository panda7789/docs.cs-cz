---
title: IsNot – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 7e1ac1004e671f592c03bd44ee7ec2e8cc572933
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71331621"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="93c6f-102">IsNot – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93c6f-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="93c6f-103">Porovná dvě proměnné odkazu na objekt.</span><span class="sxs-lookup"><span data-stu-id="93c6f-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="93c6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93c6f-104">Syntax</span></span>

```vb
result = object1 IsNot object2
```

## <a name="parts"></a><span data-ttu-id="93c6f-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="93c6f-105">Parts</span></span>
 <span data-ttu-id="93c6f-106">Vyžaduje se `result`.</span><span class="sxs-lookup"><span data-stu-id="93c6f-106">`result` Required.</span></span> <span data-ttu-id="93c6f-107">Hodnota `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="93c6f-107">A `Boolean` value.</span></span>

 <span data-ttu-id="93c6f-108">Vyžaduje se `object1`.</span><span class="sxs-lookup"><span data-stu-id="93c6f-108">`object1` Required.</span></span> <span data-ttu-id="93c6f-109">Jakákoli proměnná nebo výraz `Object`.</span><span class="sxs-lookup"><span data-stu-id="93c6f-109">Any `Object` variable or expression.</span></span>

 <span data-ttu-id="93c6f-110">Vyžaduje se `object2`.</span><span class="sxs-lookup"><span data-stu-id="93c6f-110">`object2` Required.</span></span> <span data-ttu-id="93c6f-111">Jakákoli proměnná nebo výraz `Object`.</span><span class="sxs-lookup"><span data-stu-id="93c6f-111">Any `Object` variable or expression.</span></span>

## <a name="remarks"></a><span data-ttu-id="93c6f-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93c6f-112">Remarks</span></span>
 <span data-ttu-id="93c6f-113">Operátor `IsNot` určuje, zda dva odkazy na objekt odkazují na různé objekty.</span><span class="sxs-lookup"><span data-stu-id="93c6f-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="93c6f-114">Ale neprovádí porovnávání hodnot.</span><span class="sxs-lookup"><span data-stu-id="93c6f-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="93c6f-115">Pokud `object1` a `object2` odkazují na přesnou stejnou instanci objektu, `result` je `False`; Pokud ne, `result` je `True`.</span><span class="sxs-lookup"><span data-stu-id="93c6f-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>

 <span data-ttu-id="93c6f-116">`IsNot` je opakem operátoru `Is`.</span><span class="sxs-lookup"><span data-stu-id="93c6f-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="93c6f-117">Výhodou `IsNot` je, že se můžete vyhnout nevhodným syntaxem `Not` a `Is`, což může být obtížné přečíst.</span><span class="sxs-lookup"><span data-stu-id="93c6f-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>

 <span data-ttu-id="93c6f-118">Operátory `Is` a `IsNot` můžete použít k otestování objektů s časnou vazbou i s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="93c6f-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>

## <a name="example"></a><span data-ttu-id="93c6f-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="93c6f-119">Example</span></span>
 <span data-ttu-id="93c6f-120">Následující příklad kódu používá operátor `Is` a operátor `IsNot` k provedení stejného porovnání.</span><span class="sxs-lookup"><span data-stu-id="93c6f-120">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a><span data-ttu-id="93c6f-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93c6f-121">See also</span></span>

- [<span data-ttu-id="93c6f-122">Operátor Is</span><span class="sxs-lookup"><span data-stu-id="93c6f-122">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="93c6f-123">Operátor Typeof</span><span class="sxs-lookup"><span data-stu-id="93c6f-123">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="93c6f-124">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="93c6f-124">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- <span data-ttu-id="93c6f-125">[Postupy: Otestuje, zda jsou dva objekty stejné @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="93c6f-125">[How to: Test Whether Two Objects Are the Same](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)</span></span>
