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
ms.openlocfilehash: 3cc0ae5f04358fbe6b2aabc50498f39ca7225164
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370801"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="ff0cd-102">Is – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff0cd-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="ff0cd-103">Porovná dvě proměnné odkazu na objekt.</span><span class="sxs-lookup"><span data-stu-id="ff0cd-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff0cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff0cd-104">Syntax</span></span>  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="ff0cd-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="ff0cd-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="ff0cd-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ff0cd-106">Required.</span></span> <span data-ttu-id="ff0cd-107">Libovolná `Boolean` hodnota.</span><span class="sxs-lookup"><span data-stu-id="ff0cd-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="ff0cd-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ff0cd-108">Required.</span></span> <span data-ttu-id="ff0cd-109">Libovolný `Object` název.</span><span class="sxs-lookup"><span data-stu-id="ff0cd-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="ff0cd-110">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ff0cd-110">Required.</span></span> <span data-ttu-id="ff0cd-111">Libovolný `Object` název.</span><span class="sxs-lookup"><span data-stu-id="ff0cd-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff0cd-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff0cd-112">Remarks</span></span>  
 <span data-ttu-id="ff0cd-113">`Is`Operátor určuje, zda dva odkazy na objekt odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="ff0cd-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="ff0cd-114">Ale neprovádí porovnávání hodnot.</span><span class="sxs-lookup"><span data-stu-id="ff0cd-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="ff0cd-115">Pokud `object1` a `object2` oba odkazují na přesnou stejnou instanci objektu, `result` je `True` ; Pokud ne, `result` je `False` .</span><span class="sxs-lookup"><span data-stu-id="ff0cd-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="ff0cd-116">`Is`lze také použít s `TypeOf` klíčovým slovem pro vytvoření `TypeOf` výrazu... `Is` , který testuje, zda je objektová proměnná kompatibilní s datovým typem.</span><span class="sxs-lookup"><span data-stu-id="ff0cd-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff0cd-117">`Is`Klíčové slovo se používá také v rámci [výběru... Příkaz Case](../statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ff0cd-117">The `Is` keyword is also used in the [Select...Case Statement](../statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff0cd-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff0cd-118">Example</span></span>  
 <span data-ttu-id="ff0cd-119">Následující příklad používá `Is` operátor pro porovnání párů odkazů na objekty.</span><span class="sxs-lookup"><span data-stu-id="ff0cd-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="ff0cd-120">Výsledky jsou přiřazeny k `Boolean` hodnotě, která představuje, zda jsou dva objekty identické.</span><span class="sxs-lookup"><span data-stu-id="ff0cd-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 <span data-ttu-id="ff0cd-121">Jak ukazuje předchozí příklad, lze použít `Is` operátor k otestování počátečních a pozdních vázaných objektů.</span><span class="sxs-lookup"><span data-stu-id="ff0cd-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff0cd-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff0cd-122">See also</span></span>

- [<span data-ttu-id="ff0cd-123">TypeOf – operátor</span><span class="sxs-lookup"><span data-stu-id="ff0cd-123">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="ff0cd-124">IsNot – operátor</span><span class="sxs-lookup"><span data-stu-id="ff0cd-124">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="ff0cd-125">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ff0cd-125">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="ff0cd-126">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ff0cd-126">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="ff0cd-127">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="ff0cd-127">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="ff0cd-128">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="ff0cd-128">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
