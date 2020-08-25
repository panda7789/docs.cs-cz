---
title: Is – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 1c2d87ef0a8202332c87af552f488d652c400213
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812260"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="d4284-102">Is – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4284-102">Is operator (Visual Basic)</span></span>

<span data-ttu-id="d4284-103">Porovná dvě proměnné odkazu na objekt.</span><span class="sxs-lookup"><span data-stu-id="d4284-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="d4284-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d4284-104">Syntax</span></span>

```vb
result = object1 Is object2
```

## <a name="parts"></a><span data-ttu-id="d4284-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="d4284-105">Parts</span></span>

 `result`  
 <span data-ttu-id="d4284-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="d4284-106">Required.</span></span> <span data-ttu-id="d4284-107">Libovolná `Boolean` hodnota.</span><span class="sxs-lookup"><span data-stu-id="d4284-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="d4284-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="d4284-108">Required.</span></span> <span data-ttu-id="d4284-109">Libovolný `Object` název.</span><span class="sxs-lookup"><span data-stu-id="d4284-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="d4284-110">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="d4284-110">Required.</span></span> <span data-ttu-id="d4284-111">Libovolný `Object` název.</span><span class="sxs-lookup"><span data-stu-id="d4284-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4284-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4284-112">Remarks</span></span>

<span data-ttu-id="d4284-113">`Is`Operátor určuje, zda dva odkazy na objekt odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="d4284-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="d4284-114">Ale neprovádí porovnávání hodnot.</span><span class="sxs-lookup"><span data-stu-id="d4284-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="d4284-115">Pokud `object1` a `object2` oba odkazují na přesnou stejnou instanci objektu, `result` je `True` ; Pokud ne, `result` je `False` .</span><span class="sxs-lookup"><span data-stu-id="d4284-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>

> [!NOTE]
> <span data-ttu-id="d4284-116">`Is`Klíčové slovo se používá také v rámci [výběru... Příkaz Case](../statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d4284-116">The `Is` keyword is also used in the [Select...Case Statement](../statements/select-case-statement.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="d4284-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="d4284-117">Example</span></span>

<span data-ttu-id="d4284-118">Následující příklad používá `Is` operátor pro porovnání párů odkazů na objekty.</span><span class="sxs-lookup"><span data-stu-id="d4284-118">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="d4284-119">Výsledky jsou přiřazeny k `Boolean` hodnotě, která představuje, zda jsou dva objekty identické.</span><span class="sxs-lookup"><span data-stu-id="d4284-119">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>

[!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]

<span data-ttu-id="d4284-120">Jak ukazuje předchozí příklad, lze použít `Is` operátor k otestování počátečních a pozdních vázaných objektů.</span><span class="sxs-lookup"><span data-stu-id="d4284-120">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>

## <a name="use-typeof-operator-with-is-operator"></a><span data-ttu-id="d4284-121">Použití operátoru TypeOf s operátorem is</span><span class="sxs-lookup"><span data-stu-id="d4284-121">Use TypeOf operator with Is operator</span></span>

<span data-ttu-id="d4284-122">`Is` operátor lze také použít s `TypeOf` klíčovým slovem pro vytvoření `TypeOf` výrazu... `Is` , který testuje, zda je objektová proměnná kompatibilní s datovým typem.</span><span class="sxs-lookup"><span data-stu-id="d4284-122">`Is` operator can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span> <span data-ttu-id="d4284-123">Příklad:</span><span class="sxs-lookup"><span data-stu-id="d4284-123">For example:</span></span>

```vb
If TypeOf sender Is Button Then
```

## <a name="see-also"></a><span data-ttu-id="d4284-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4284-124">See also</span></span>

- [<span data-ttu-id="d4284-125">TypeOf – operátor</span><span class="sxs-lookup"><span data-stu-id="d4284-125">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="d4284-126">IsNot – operátor</span><span class="sxs-lookup"><span data-stu-id="d4284-126">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="d4284-127">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d4284-127">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="d4284-128">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d4284-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="d4284-129">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="d4284-129">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="d4284-130">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="d4284-130">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
