---
title: Static
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: f020756466888f51298abb423997906ddc7caff7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350763"
---
# <a name="static-visual-basic"></a><span data-ttu-id="2c011-102">Static (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c011-102">Static (Visual Basic)</span></span>
<span data-ttu-id="2c011-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span><span class="sxs-lookup"><span data-stu-id="2c011-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c011-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c011-104">Remarks</span></span>  
 <span data-ttu-id="2c011-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span><span class="sxs-lookup"><span data-stu-id="2c011-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="2c011-106">A static variable continues to exist and retains its most recent value.</span><span class="sxs-lookup"><span data-stu-id="2c011-106">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="2c011-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span><span class="sxs-lookup"><span data-stu-id="2c011-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="2c011-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span><span class="sxs-lookup"><span data-stu-id="2c011-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="2c011-109">Rules</span><span class="sxs-lookup"><span data-stu-id="2c011-109">Rules</span></span>  
  
- <span data-ttu-id="2c011-110">**Declaration Context.**</span><span class="sxs-lookup"><span data-stu-id="2c011-110">**Declaration Context.**</span></span> <span data-ttu-id="2c011-111">You can use `Static` only on local variables.</span><span class="sxs-lookup"><span data-stu-id="2c011-111">You can use `Static` only on local variables.</span></span> <span data-ttu-id="2c011-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span><span class="sxs-lookup"><span data-stu-id="2c011-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="2c011-113">You cannot use `Static` inside a structure procedure.</span><span class="sxs-lookup"><span data-stu-id="2c011-113">You cannot use `Static` inside a structure procedure.</span></span>  
  
- <span data-ttu-id="2c011-114">The data types of `Static` local variables cannot be inferred.</span><span class="sxs-lookup"><span data-stu-id="2c011-114">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="2c011-115">For more information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="2c011-115">For more information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
- <span data-ttu-id="2c011-116">**Combined Modifiers.**</span><span class="sxs-lookup"><span data-stu-id="2c011-116">**Combined Modifiers.**</span></span> <span data-ttu-id="2c011-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span><span class="sxs-lookup"><span data-stu-id="2c011-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="2c011-118">Behavior</span><span class="sxs-lookup"><span data-stu-id="2c011-118">Behavior</span></span>  
 <span data-ttu-id="2c011-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span><span class="sxs-lookup"><span data-stu-id="2c011-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="2c011-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span><span class="sxs-lookup"><span data-stu-id="2c011-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="2c011-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span><span class="sxs-lookup"><span data-stu-id="2c011-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="2c011-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span><span class="sxs-lookup"><span data-stu-id="2c011-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c011-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c011-123">Example</span></span>  
 <span data-ttu-id="2c011-124">The following example demonstrates the use of `Static`.</span><span class="sxs-lookup"><span data-stu-id="2c011-124">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 <span data-ttu-id="2c011-125">The `Static` variable `totalSales` is initialized to 0 only one time.</span><span class="sxs-lookup"><span data-stu-id="2c011-125">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="2c011-126">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span><span class="sxs-lookup"><span data-stu-id="2c011-126">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="2c011-127">The `Static` modifier can be used in this context:</span><span class="sxs-lookup"><span data-stu-id="2c011-127">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="2c011-128">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="2c011-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2c011-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c011-129">See also</span></span>

- [<span data-ttu-id="2c011-130">Shadows</span><span class="sxs-lookup"><span data-stu-id="2c011-130">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="2c011-131">Shared</span><span class="sxs-lookup"><span data-stu-id="2c011-131">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="2c011-132">Lifetime in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2c011-132">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="2c011-133">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="2c011-133">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="2c011-134">Struktury</span><span class="sxs-lookup"><span data-stu-id="2c011-134">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="2c011-135">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="2c011-135">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="2c011-136">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="2c011-136">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
