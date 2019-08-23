---
title: IsNot – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 0a83b48e5e415bd6ca0c777cef6d34f7127691b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966925"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="96b0b-102">IsNot – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96b0b-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="96b0b-103">Porovná dvě proměnné odkazu na objekt.</span><span class="sxs-lookup"><span data-stu-id="96b0b-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96b0b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96b0b-104">Syntax</span></span>  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a><span data-ttu-id="96b0b-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="96b0b-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="96b0b-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="96b0b-106">Required.</span></span> <span data-ttu-id="96b0b-107">`Boolean` Hodnota.</span><span class="sxs-lookup"><span data-stu-id="96b0b-107">A `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="96b0b-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="96b0b-108">Required.</span></span> <span data-ttu-id="96b0b-109">Jakákoli `Object` proměnná nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="96b0b-109">Any `Object` variable or expression.</span></span>  
  
 `object2`  
 <span data-ttu-id="96b0b-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="96b0b-110">Required.</span></span> <span data-ttu-id="96b0b-111">Jakákoli `Object` proměnná nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="96b0b-111">Any `Object` variable or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96b0b-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96b0b-112">Remarks</span></span>  
 <span data-ttu-id="96b0b-113">`IsNot` Operátor určuje, zda dva odkazy na objekt odkazují na různé objekty.</span><span class="sxs-lookup"><span data-stu-id="96b0b-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="96b0b-114">Ale neprovádí porovnávání hodnot.</span><span class="sxs-lookup"><span data-stu-id="96b0b-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="96b0b-115">Pokud `object1` a `False` `result` `result` `True`oba odkazují na přesnou stejnou instanci objektu, je; Pokud ne, je. `object2`</span><span class="sxs-lookup"><span data-stu-id="96b0b-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>  
  
 <span data-ttu-id="96b0b-116">`IsNot`je opakem `Is` operátoru.</span><span class="sxs-lookup"><span data-stu-id="96b0b-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="96b0b-117">Výhodou `IsNot` je, že se můžete vyhnout nevhodným `Not` syntaxem s a `Is`, což může být obtížné ho přečíst.</span><span class="sxs-lookup"><span data-stu-id="96b0b-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>  
  
 <span data-ttu-id="96b0b-118">Operátory `Is` a`IsNot` můžete použít k otestování objektů s časnou vazbou i s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="96b0b-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96b0b-119">Operátor nelze použít pro porovnání výrazů vrácených `TypeOf` z operátoru. `IsNot`</span><span class="sxs-lookup"><span data-stu-id="96b0b-119">The `IsNot` operator cannot be used to compare expressions returned from the `TypeOf` operator.</span></span> <span data-ttu-id="96b0b-120">Místo toho je nutné použít `Not` operátory a. `Is`</span><span class="sxs-lookup"><span data-stu-id="96b0b-120">Instead, you must use the `Not` and `Is` operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96b0b-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="96b0b-121">Example</span></span>  
 <span data-ttu-id="96b0b-122">Následující příklad kódu používá `Is` operátor `IsNot` i operátor k provedení stejného porovnání.</span><span class="sxs-lookup"><span data-stu-id="96b0b-122">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>  
  
 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]  
  
## <a name="see-also"></a><span data-ttu-id="96b0b-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96b0b-123">See also</span></span>

- [<span data-ttu-id="96b0b-124">Operátor Is</span><span class="sxs-lookup"><span data-stu-id="96b0b-124">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="96b0b-125">Operátor Typeof</span><span class="sxs-lookup"><span data-stu-id="96b0b-125">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="96b0b-126">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="96b0b-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="96b0b-127">Postupy: Testovat, zda jsou dva objekty stejné</span><span class="sxs-lookup"><span data-stu-id="96b0b-127">How to: Test Whether Two Objects Are the Same</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
