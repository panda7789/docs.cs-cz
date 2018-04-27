---
title: 'Postupy: Určení, zda dva objekty jsou identické (Visual Basic).'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 266e878e7f5fa8deb1c8cd91795af8d63ded0177
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="f0a00-102">Postupy: Určení, zda dva objekty jsou identické (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="f0a00-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="f0a00-103">V jazyce Visual Basic dva odkazy na proměnné jsou považovány za shodné, pokud jejich ukazatele jsou stejné, to znamená, pokud obě proměnné bodu na stejnou instanci třídy v paměti.</span><span class="sxs-lookup"><span data-stu-id="f0a00-103">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="f0a00-104">Například v aplikaci Windows Forms, můžete chtít provést porovnání Chcete-li určit, zda aktuální instance (`Me`) je stejný jako konkrétní instanci, například `Form2`.</span><span class="sxs-lookup"><span data-stu-id="f0a00-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 <span data-ttu-id="f0a00-105">Visual Basic poskytuje dva operátory k porovnání ukazatele.</span><span class="sxs-lookup"><span data-stu-id="f0a00-105">Visual Basic provides two operators to compare pointers.</span></span> <span data-ttu-id="f0a00-106">[Je operátor](../../../../visual-basic/language-reference/operators/is-operator.md) vrátí `True` případě objekty jsou identické a [IsNot – operátor](../../../../visual-basic/language-reference/operators/isnot-operator.md) vrátí `True` Pokud tomu tak není.</span><span class="sxs-lookup"><span data-stu-id="f0a00-106">The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="f0a00-107">Určení, zda dva objekty jsou identické</span><span class="sxs-lookup"><span data-stu-id="f0a00-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="f0a00-108">Chcete-li zjistit, zda dva objekty jsou identické</span><span class="sxs-lookup"><span data-stu-id="f0a00-108">To determine if two objects are identical</span></span>  
  
1.  <span data-ttu-id="f0a00-109">Nastavení `Boolean` výraz k testování dva objekty.</span><span class="sxs-lookup"><span data-stu-id="f0a00-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="f0a00-110">Do výrazu testování pomocí `Is` operátor s dva objekty jako operandy.</span><span class="sxs-lookup"><span data-stu-id="f0a00-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="f0a00-111">`Is` Vrátí `True` Pokud objekty bodu na stejnou instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="f0a00-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="f0a00-112">Určení, pokud dva objekty nejsou identické</span><span class="sxs-lookup"><span data-stu-id="f0a00-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="f0a00-113">Občas můžete chtít k provedení akce, pokud dva objekty nejsou identické, a může být nevhodných kombinovat `Not` a `Is`, například `If Not obj1 Is obj2`.</span><span class="sxs-lookup"><span data-stu-id="f0a00-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="f0a00-114">V takovém případě můžete použít `IsNot` operátor.</span><span class="sxs-lookup"><span data-stu-id="f0a00-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="f0a00-115">Chcete-li zjistit, pokud dva objekty nejsou identické</span><span class="sxs-lookup"><span data-stu-id="f0a00-115">To determine if two objects are not identical</span></span>  
  
1.  <span data-ttu-id="f0a00-116">Nastavení `Boolean` výraz k testování dva objekty.</span><span class="sxs-lookup"><span data-stu-id="f0a00-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="f0a00-117">Do výrazu testování pomocí `IsNot` operátor s dva objekty jako operandy.</span><span class="sxs-lookup"><span data-stu-id="f0a00-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="f0a00-118">`IsNot` Vrátí `True` Pokud objekty neodkazují na stejnou instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="f0a00-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0a00-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0a00-119">Example</span></span>  
 <span data-ttu-id="f0a00-120">Následující příklad testy dvojici `Object` proměnné, které chcete zobrazit, pokud se bod na stejnou instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="f0a00-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]  
  
 <span data-ttu-id="f0a00-121">V předchozím příkladu zobrazí následující výstup.</span><span class="sxs-lookup"><span data-stu-id="f0a00-121">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="f0a00-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0a00-122">See Also</span></span>  
 [<span data-ttu-id="f0a00-123">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="f0a00-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="f0a00-124">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="f0a00-124">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="f0a00-125">Hodnoty objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="f0a00-125">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="f0a00-126">Operátor Is</span><span class="sxs-lookup"><span data-stu-id="f0a00-126">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="f0a00-127">Operátor IsNot</span><span class="sxs-lookup"><span data-stu-id="f0a00-127">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="f0a00-128">Postupy: Určení, zda dva objekty spolu souvisí</span><span class="sxs-lookup"><span data-stu-id="f0a00-128">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [<span data-ttu-id="f0a00-129">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="f0a00-129">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
