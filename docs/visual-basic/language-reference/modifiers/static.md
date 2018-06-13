---
title: Static (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 2cbd99a026a5ebf0e215ee5732d62ccf639d3836
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602051"
---
# <a name="static-visual-basic"></a><span data-ttu-id="6ec3e-102">Static (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ec3e-102">Static (Visual Basic)</span></span>
<span data-ttu-id="6ec3e-103">Určuje, že jeden nebo více deklarované lokální proměnné jsou nadále existovat a po ukončení procesu, ve které jsou deklarovány zachovat jejich nejnovější hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ec3e-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ec3e-104">Remarks</span></span>  
 <span data-ttu-id="6ec3e-105">Za normálních okolností místní proměnné v postupu přestane existovat také zastaví proces.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="6ec3e-106">Statické proměnné nadále existovat a jeho nejnovější hodnotu zachová.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-106">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="6ec3e-107">Při příštím kódu volá proceduru, není inicializace proměnné a že dál obsahuje nejpozdější hodnotu, který jste přiřadili k němu.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="6ec3e-108">Statické proměnné i nadále existovat pro životnost třídu nebo modul, který je definován v.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6ec3e-109">Pravidla</span><span class="sxs-lookup"><span data-stu-id="6ec3e-109">Rules</span></span>  
  
-   <span data-ttu-id="6ec3e-110">**Kontext deklarace.**</span><span class="sxs-lookup"><span data-stu-id="6ec3e-110">**Declaration Context.**</span></span> <span data-ttu-id="6ec3e-111">Můžete použít `Static` pouze na místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-111">You can use `Static` only on local variables.</span></span> <span data-ttu-id="6ec3e-112">To znamená kontext deklarace `Static` proměnná musí být procedury nebo blok v postupu, a nelze ji zdrojový soubor, obor názvů, třídy, struktury nebo modul.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="6ec3e-113">Nemůžete použít `Static` uvnitř procedury struktura.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-113">You cannot use `Static` inside a structure procedure.</span></span>  
  
-   <span data-ttu-id="6ec3e-114">Datové typy `Static` místní proměnné nelze odvodit.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-114">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="6ec3e-115">Další informace najdete v tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="6ec3e-115">For more information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
-   <span data-ttu-id="6ec3e-116">**Kombinovaná parametrů.**</span><span class="sxs-lookup"><span data-stu-id="6ec3e-116">**Combined Modifiers.**</span></span> <span data-ttu-id="6ec3e-117">Nelze zadat `Static` společně s `ReadOnly`, `Shadows`, nebo `Shared` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="6ec3e-118">Chování</span><span class="sxs-lookup"><span data-stu-id="6ec3e-118">Behavior</span></span>  
 <span data-ttu-id="6ec3e-119">Když je deklarovat statickou proměnnou v `Shared` postup, pouze jedna kopie statické proměnné je k dispozici pro celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="6ec3e-120">Volání `Shared` název postupu pomocí třídy, ne proměnné, která odkazuje na instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="6ec3e-121">Když je deklarovat statické proměnné v postupu, který není `Shared`, pouze jedna kopie proměnné je k dispozici pro každou instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="6ec3e-122">Volání procedury, nesdílené pomocí proměnné, která odkazuje na konkrétní instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ec3e-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ec3e-123">Example</span></span>  
 <span data-ttu-id="6ec3e-124">Následující příklad ukazuje použití `Static`.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-124">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 <span data-ttu-id="6ec3e-125">`Static` Proměnná `totalSales` je inicializováno 0 pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-125">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="6ec3e-126">Pokaždé, když zadáte `updateSales`, `totalSales` má stále nejnovější hodnotu, kterou jste vypočítali pro něj.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-126">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="6ec3e-127">`Static` Modifikátor můžete v tomto kontextu použít:</span><span class="sxs-lookup"><span data-stu-id="6ec3e-127">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="6ec3e-128">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="6ec3e-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="6ec3e-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ec3e-129">See Also</span></span>  
 [<span data-ttu-id="6ec3e-130">Shadows</span><span class="sxs-lookup"><span data-stu-id="6ec3e-130">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="6ec3e-131">Shared</span><span class="sxs-lookup"><span data-stu-id="6ec3e-131">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="6ec3e-132">Doba platnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6ec3e-132">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="6ec3e-133">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="6ec3e-133">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="6ec3e-134">Struktury</span><span class="sxs-lookup"><span data-stu-id="6ec3e-134">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="6ec3e-135">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="6ec3e-135">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="6ec3e-136">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="6ec3e-136">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
