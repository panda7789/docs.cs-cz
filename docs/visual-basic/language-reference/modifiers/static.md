---
title: Statické
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
# <a name="static-visual-basic"></a><span data-ttu-id="acb12-102">Static (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acb12-102">Static (Visual Basic)</span></span>
<span data-ttu-id="acb12-103">Určuje, že nejmíň jedna z deklarovaných lokálních proměnných bude i po ukončení postupu, ve kterém jsou deklarované, dál existovat a uchovávat jejich nejnovější hodnoty.</span><span class="sxs-lookup"><span data-stu-id="acb12-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acb12-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="acb12-104">Remarks</span></span>  
 <span data-ttu-id="acb12-105">V normálním případě místní proměnná v proceduře přestane existovat, jakmile se procedura zastaví.</span><span class="sxs-lookup"><span data-stu-id="acb12-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="acb12-106">Statická proměnná stále existuje a uchovává její nejnovější hodnotu.</span><span class="sxs-lookup"><span data-stu-id="acb12-106">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="acb12-107">Při příštím volání procedury kód, proměnná není znovu inicializována a stále obsahuje nejnovější hodnotu, kterou jste přiřadili.</span><span class="sxs-lookup"><span data-stu-id="acb12-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="acb12-108">Statická proměnná bude nadále existovat po dobu života třídy nebo modulu, ve kterém je definována.</span><span class="sxs-lookup"><span data-stu-id="acb12-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="acb12-109">Pravidla</span><span class="sxs-lookup"><span data-stu-id="acb12-109">Rules</span></span>  
  
- <span data-ttu-id="acb12-110">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="acb12-110">**Declaration Context.**</span></span> <span data-ttu-id="acb12-111">`Static` můžete použít pouze pro místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="acb12-111">You can use `Static` only on local variables.</span></span> <span data-ttu-id="acb12-112">To znamená, že kontext deklarace pro proměnnou `Static` musí být procedura nebo blok v proceduře a nemůže se jednat o zdrojový soubor, obor názvů, třídu, strukturu nebo modul.</span><span class="sxs-lookup"><span data-stu-id="acb12-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="acb12-113">V proceduře struktury nelze použít `Static`.</span><span class="sxs-lookup"><span data-stu-id="acb12-113">You cannot use `Static` inside a structure procedure.</span></span>  
  
- <span data-ttu-id="acb12-114">Datové typy `Static` místních proměnných nelze odvodit.</span><span class="sxs-lookup"><span data-stu-id="acb12-114">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="acb12-115">Další informace naleznete v tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="acb12-115">For more information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
- <span data-ttu-id="acb12-116">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="acb12-116">**Combined Modifiers.**</span></span> <span data-ttu-id="acb12-117">V rámci stejné deklarace nelze zadat `Static` společně s `ReadOnly`, `Shadows`nebo `Shared`.</span><span class="sxs-lookup"><span data-stu-id="acb12-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="acb12-118">Chování</span><span class="sxs-lookup"><span data-stu-id="acb12-118">Behavior</span></span>  
 <span data-ttu-id="acb12-119">Pokud deklarujete statickou proměnnou v `Shared` proceduře, je k dispozici pouze jedna kopie statické proměnné pro celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="acb12-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="acb12-120">Proceduru `Shared` zavoláte pomocí názvu třídy, nikoli proměnné, která odkazuje na instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="acb12-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="acb12-121">Pokud deklarujete statickou proměnnou v proceduře, která není `Shared`, je k dispozici pouze jedna kopie proměnné pro každou instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="acb12-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="acb12-122">Nesdílenou proceduru zavoláte pomocí proměnné, která odkazuje na konkrétní instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="acb12-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acb12-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="acb12-123">Example</span></span>  
 <span data-ttu-id="acb12-124">Následující příklad ukazuje použití `Static`.</span><span class="sxs-lookup"><span data-stu-id="acb12-124">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 <span data-ttu-id="acb12-125">Proměnná `Static` `totalSales` byla inicializována na hodnotu 0 pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="acb12-125">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="acb12-126">Pokaždé, když zadáte `updateSales`, má `totalSales` stále nejnovější hodnotu, kterou jste pro ni vypočítali.</span><span class="sxs-lookup"><span data-stu-id="acb12-126">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="acb12-127">V tomto kontextu lze použít modifikátor `Static`:</span><span class="sxs-lookup"><span data-stu-id="acb12-127">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="acb12-128">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="acb12-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="acb12-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="acb12-129">See also</span></span>

- [<span data-ttu-id="acb12-130">Shadows</span><span class="sxs-lookup"><span data-stu-id="acb12-130">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="acb12-131">Shared</span><span class="sxs-lookup"><span data-stu-id="acb12-131">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="acb12-132">Doba života v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="acb12-132">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="acb12-133">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="acb12-133">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="acb12-134">Struktury</span><span class="sxs-lookup"><span data-stu-id="acb12-134">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="acb12-135">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="acb12-135">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="acb12-136">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="acb12-136">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
