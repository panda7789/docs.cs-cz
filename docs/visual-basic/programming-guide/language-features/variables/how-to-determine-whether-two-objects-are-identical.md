---
title: 'Postupy: Určení, zda dva objekty jsou identické.'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 67c3af8b7bdac3ad1c7e4908f1ac2684df7a87aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410474"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="a64b9-102">Postupy: Určení, zda dva objekty jsou identické (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a64b9-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="a64b9-103">V Visual Basic jsou dva odkazy na proměnné považovány za identické, pokud jsou ukazatele stejné, to znamená, pokud obě proměnné odkazují na stejnou instanci třídy v paměti.</span><span class="sxs-lookup"><span data-stu-id="a64b9-103">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="a64b9-104">Například v aplikaci model Windows Forms můžete chtít porovnat, aby bylo možné určit, zda aktuální instance ( `Me` ) je stejná jako konkrétní instance, například `Form2` .</span><span class="sxs-lookup"><span data-stu-id="a64b9-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 <span data-ttu-id="a64b9-105">Visual Basic poskytuje dva operátory pro porovnání ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="a64b9-105">Visual Basic provides two operators to compare pointers.</span></span> <span data-ttu-id="a64b9-106">[Operátor is](../../../language-reference/operators/is-operator.md) vrátí `True` , pokud jsou objekty shodné, a [operátor IsNot](../../../language-reference/operators/isnot-operator.md) vrátí, `True` Pokud nejsou.</span><span class="sxs-lookup"><span data-stu-id="a64b9-106">The [Is Operator](../../../language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="a64b9-107">Určení, zda jsou dva objekty identické</span><span class="sxs-lookup"><span data-stu-id="a64b9-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="a64b9-108">Určení, zda jsou dva objekty identické</span><span class="sxs-lookup"><span data-stu-id="a64b9-108">To determine if two objects are identical</span></span>  
  
1. <span data-ttu-id="a64b9-109">Nastavte `Boolean` výraz pro otestování těchto dvou objektů.</span><span class="sxs-lookup"><span data-stu-id="a64b9-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="a64b9-110">Ve výrazu testování použijte `Is` operátor se dvěma objekty jako operandy.</span><span class="sxs-lookup"><span data-stu-id="a64b9-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="a64b9-111">`Is`Vrátí `True` , zda objekty odkazují na stejnou instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="a64b9-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="a64b9-112">Určení, zda dva objekty nejsou identické</span><span class="sxs-lookup"><span data-stu-id="a64b9-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="a64b9-113">V některých případech je třeba provést akci, pokud tyto dva objekty nejsou totožné a může být nevhodným způsobem kombinovat `Not` a například `Is` `If Not obj1 Is obj2` .</span><span class="sxs-lookup"><span data-stu-id="a64b9-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="a64b9-114">V takovém případě můžete použít `IsNot` operátor.</span><span class="sxs-lookup"><span data-stu-id="a64b9-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="a64b9-115">Určení, zda dva objekty nejsou identické</span><span class="sxs-lookup"><span data-stu-id="a64b9-115">To determine if two objects are not identical</span></span>  
  
1. <span data-ttu-id="a64b9-116">Nastavte `Boolean` výraz pro otestování těchto dvou objektů.</span><span class="sxs-lookup"><span data-stu-id="a64b9-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="a64b9-117">Ve výrazu testování použijte `IsNot` operátor se dvěma objekty jako operandy.</span><span class="sxs-lookup"><span data-stu-id="a64b9-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="a64b9-118">`IsNot`Vrátí, `True` zda objekty neodkazují na stejnou instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="a64b9-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a64b9-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="a64b9-119">Example</span></span>  
 <span data-ttu-id="a64b9-120">Následující příklad testuje páry proměnných, `Object` aby bylo možné zjistit, zda odkazují na stejnou instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="a64b9-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 <span data-ttu-id="a64b9-121">V předchozím příkladu se zobrazí následující výstup.</span><span class="sxs-lookup"><span data-stu-id="a64b9-121">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="a64b9-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="a64b9-122">See also</span></span>

- [<span data-ttu-id="a64b9-123">Datový typ objektu</span><span class="sxs-lookup"><span data-stu-id="a64b9-123">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="a64b9-124">Proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="a64b9-124">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="a64b9-125">Hodnoty proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="a64b9-125">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="a64b9-126">Is – operátor</span><span class="sxs-lookup"><span data-stu-id="a64b9-126">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="a64b9-127">IsNot – operátor</span><span class="sxs-lookup"><span data-stu-id="a64b9-127">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="a64b9-128">Postupy: Určení, zda dva objekty souvisejí.</span><span class="sxs-lookup"><span data-stu-id="a64b9-128">How to: Determine Whether Two Objects Are Related</span></span>](how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="a64b9-129">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="a64b9-129">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
