---
title: "ReDim – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ReDim
- vb.Preserve
helpviewer_keywords:
- fixed-length strings [Visual Basic], declaring
- ReDim statement [Visual Basic], syntax
- dynamic arrays [Visual Basic], ReDim statement
- arrays [Visual Basic], reallocating
- arrays [Visual Basic], reinitializing
- arrays [Visual Basic], dimensions
- scalars, and arrays
- scalars
- declarations [Visual Basic], dynamic arrays
- variables [Visual Basic], scalar
- ReDim statement [Visual Basic]
- data types [Visual Basic], assigning
- As keyword [Visual Basic], in ReDim statement
- To keyword [Visual Basic], ReDim statement
- arrays [Visual Basic], declaring
- Preserve keyword [Visual Basic], ReDim statement
- storage [Visual Basic], allocating
- arrays [Visual Basic], and scalars
- declaration statements [Visual Basic]
- scalar variables [Visual Basic]
ms.assetid: ad1c5e07-dcd7-4ae1-a79e-ad3f2dcc2083
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cec66ee33bfd82b3abd623a0130f5635aa3d1d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="redim-statement-visual-basic"></a><span data-ttu-id="36eb7-102">ReDim – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36eb7-102">ReDim Statement (Visual Basic)</span></span>
<span data-ttu-id="36eb7-103">Přidělí prostor úložiště pro proměnné pole.</span><span class="sxs-lookup"><span data-stu-id="36eb7-103">Reallocates storage space for an array variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36eb7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36eb7-104">Syntax</span></span>  
  
```  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="36eb7-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="36eb7-105">Parts</span></span>  
  
|<span data-ttu-id="36eb7-106">Termín</span><span class="sxs-lookup"><span data-stu-id="36eb7-106">Term</span></span>|<span data-ttu-id="36eb7-107">Definice</span><span class="sxs-lookup"><span data-stu-id="36eb7-107">Definition</span></span>|  
|----------|----------------|  
|`Preserve`|<span data-ttu-id="36eb7-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="36eb7-108">Optional.</span></span> <span data-ttu-id="36eb7-109">Modifikátor umožňuje zachovat data v existující pole, když změníte velikost pouze poslední dimenze.</span><span class="sxs-lookup"><span data-stu-id="36eb7-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span></span>|  
|`name`|<span data-ttu-id="36eb7-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="36eb7-110">Required.</span></span> <span data-ttu-id="36eb7-111">Název proměnné pole.</span><span class="sxs-lookup"><span data-stu-id="36eb7-111">Name of the array variable.</span></span> <span data-ttu-id="36eb7-112">V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="36eb7-112">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`boundlist`|<span data-ttu-id="36eb7-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="36eb7-113">Required.</span></span> <span data-ttu-id="36eb7-114">Seznam mezí Každá dimenze Předefinovaná pole.</span><span class="sxs-lookup"><span data-stu-id="36eb7-114">List of bounds of each dimension of the redefined array.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36eb7-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36eb7-115">Remarks</span></span>  
 <span data-ttu-id="36eb7-116">Můžete použít `ReDim` příkaz ke změně velikosti jeden nebo více rozměry pole, které již byl deklarován.</span><span class="sxs-lookup"><span data-stu-id="36eb7-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span></span> <span data-ttu-id="36eb7-117">Pokud máte velké pole a některé jeho elementy již nepotřebujete `ReDim` můžete uvolnit paměť snížením velikost pole.</span><span class="sxs-lookup"><span data-stu-id="36eb7-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span></span> <span data-ttu-id="36eb7-118">Na druhé straně, pokud další prvky, musí vaše pole `ReDim` je přidat.</span><span class="sxs-lookup"><span data-stu-id="36eb7-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span></span>  
  
 <span data-ttu-id="36eb7-119">`ReDim` Příkaz je určena pouze pro pole.</span><span class="sxs-lookup"><span data-stu-id="36eb7-119">The `ReDim` statement is intended only for arrays.</span></span> <span data-ttu-id="36eb7-120">Není platný na skalárních hodnot (proměnné, které obsahují pouze jednu hodnotu), kolekce nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="36eb7-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span></span> <span data-ttu-id="36eb7-121">Všimněte si, že pokud deklarovat proměnnou být typu `Array`, `ReDim` příkaz nemá dostatek informací o typu vytvořte nové pole.</span><span class="sxs-lookup"><span data-stu-id="36eb7-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span></span>  
  
 <span data-ttu-id="36eb7-122">Můžete použít `ReDim` jenom na úrovni postupu.</span><span class="sxs-lookup"><span data-stu-id="36eb7-122">You can use `ReDim` only at procedure level.</span></span> <span data-ttu-id="36eb7-123">Kontext deklarace proměnné proto musí být procedury; nemůže být zdrojový soubor, obor názvů, rozhraní, třídy, struktury, modul nebo blok.</span><span class="sxs-lookup"><span data-stu-id="36eb7-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span></span> <span data-ttu-id="36eb7-124">Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="36eb7-124">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="36eb7-125">Pravidla</span><span class="sxs-lookup"><span data-stu-id="36eb7-125">Rules</span></span>  
  
-   <span data-ttu-id="36eb7-126">**Více proměnných.**</span><span class="sxs-lookup"><span data-stu-id="36eb7-126">**Multiple Variables.**</span></span> <span data-ttu-id="36eb7-127">Můžete změnit velikost několik proměnné pole v jednom příkazu deklarace a určit, `name` a `boundlist` částí pro každou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="36eb7-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span></span> <span data-ttu-id="36eb7-128">Více proměnných jsou oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="36eb7-128">Multiple variables are separated by commas.</span></span>  
  
-   <span data-ttu-id="36eb7-129">**Meze pole.**</span><span class="sxs-lookup"><span data-stu-id="36eb7-129">**Array Bounds.**</span></span> <span data-ttu-id="36eb7-130">Každá položka v `boundlist` můžete určit, dolní a horní meze této dimenze.</span><span class="sxs-lookup"><span data-stu-id="36eb7-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span></span> <span data-ttu-id="36eb7-131">Dolní hranice je vždy 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="36eb7-131">The lower bound is always 0 (zero).</span></span> <span data-ttu-id="36eb7-132">Horní mez je hodnota nejvyšší možné indexu pro daná dimenze, není délka dimenze (což je horní mez plus jedna).</span><span class="sxs-lookup"><span data-stu-id="36eb7-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span></span> <span data-ttu-id="36eb7-133">Index pro Každá dimenze se může lišit od 0 do jeho horní mez hodnoty.</span><span class="sxs-lookup"><span data-stu-id="36eb7-133">The index for each dimension can vary from 0 through its upper bound value.</span></span>  
  
     <span data-ttu-id="36eb7-134">Počet dimenzí v `boundlist` původní počet rozměrů (pořadí) pole se musí shodovat.</span><span class="sxs-lookup"><span data-stu-id="36eb7-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span></span>  
  
-   <span data-ttu-id="36eb7-135">**Datové typy.**</span><span class="sxs-lookup"><span data-stu-id="36eb7-135">**Data Types.**</span></span> <span data-ttu-id="36eb7-136">`ReDim` Příkaz nelze změnit datový typ proměnné pole nebo jeho prvky.</span><span class="sxs-lookup"><span data-stu-id="36eb7-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span></span>  
  
-   <span data-ttu-id="36eb7-137">**Inicializace.**</span><span class="sxs-lookup"><span data-stu-id="36eb7-137">**Initialization.**</span></span> <span data-ttu-id="36eb7-138">`ReDim` Příkaz nelze zadat nové inicializace hodnoty pro elementy pole.</span><span class="sxs-lookup"><span data-stu-id="36eb7-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span></span>  
  
-   <span data-ttu-id="36eb7-139">**Pořadí.**</span><span class="sxs-lookup"><span data-stu-id="36eb7-139">**Rank.**</span></span> <span data-ttu-id="36eb7-140">`ReDim` Příkaz nelze změnit pořadí pole (počet dimenzí).</span><span class="sxs-lookup"><span data-stu-id="36eb7-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span></span>  
  
-   <span data-ttu-id="36eb7-141">**Změna velikosti s zachovat.**</span><span class="sxs-lookup"><span data-stu-id="36eb7-141">**Resizing with Preserve.**</span></span> <span data-ttu-id="36eb7-142">Pokud používáte `Preserve`, můžete změnit velikost pouze poslední dimenze pole.</span><span class="sxs-lookup"><span data-stu-id="36eb7-142">If you use `Preserve`, you can resize only the last dimension of the array.</span></span> <span data-ttu-id="36eb7-143">Pro každý další dimenze je nutné zadat mez existující pole.</span><span class="sxs-lookup"><span data-stu-id="36eb7-143">For every other dimension, you must specify the bound of the existing array.</span></span>  
  
     <span data-ttu-id="36eb7-144">Například pokud vaše pole má jenom jednu dimenzi, můžete změnit velikost daná dimenze a současně zachovat veškerý obsah pole, protože měníte jenom dimenze a poslední.</span><span class="sxs-lookup"><span data-stu-id="36eb7-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span></span> <span data-ttu-id="36eb7-145">Ale pokud vaše pole má dvě nebo více dimenzí, je možné změnit velikost pouze poslední dimenze používáte `Preserve`.</span><span class="sxs-lookup"><span data-stu-id="36eb7-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span></span>  
  
-   <span data-ttu-id="36eb7-146">**Vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="36eb7-146">**Properties.**</span></span> <span data-ttu-id="36eb7-147">Můžete použít `ReDim` u vlastnosti, která obsahuje pole hodnot.</span><span class="sxs-lookup"><span data-stu-id="36eb7-147">You can use `ReDim` on a property that holds an array of values.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="36eb7-148">Chování</span><span class="sxs-lookup"><span data-stu-id="36eb7-148">Behavior</span></span>  
  
-   <span data-ttu-id="36eb7-149">**Pole nahrazení.**</span><span class="sxs-lookup"><span data-stu-id="36eb7-149">**Array Replacement.**</span></span> <span data-ttu-id="36eb7-150">`ReDim`uvolní existující pole a vytvoří nové pole s stejné pořadí.</span><span class="sxs-lookup"><span data-stu-id="36eb7-150">`ReDim` releases the existing array and creates a new array with the same rank.</span></span> <span data-ttu-id="36eb7-151">Nové pole nahrazuje pole vydaných v proměnné pole.</span><span class="sxs-lookup"><span data-stu-id="36eb7-151">The new array replaces the released array in the array variable.</span></span>  
  
-   <span data-ttu-id="36eb7-152">**Inicializace bez zachovat.**</span><span class="sxs-lookup"><span data-stu-id="36eb7-152">**Initialization without Preserve.**</span></span> <span data-ttu-id="36eb7-153">Pokud nezadáte `Preserve`, `ReDim` inicializuje prvky nové pole pomocí výchozí hodnota pro datového typu.</span><span class="sxs-lookup"><span data-stu-id="36eb7-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span></span>  
  
-   <span data-ttu-id="36eb7-154">**Inicializace se zachovat.**</span><span class="sxs-lookup"><span data-stu-id="36eb7-154">**Initialization with Preserve.**</span></span> <span data-ttu-id="36eb7-155">Pokud zadáte `Preserve`, Visual Basic zkopíruje elementy ze stávající pole do nové pole.</span><span class="sxs-lookup"><span data-stu-id="36eb7-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36eb7-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="36eb7-156">Example</span></span>  
 <span data-ttu-id="36eb7-157">Následující příklad zvyšuje velikost poslední dimenze dynamické pole bez ztráty jakákoli stávající data v poli a potom snižuje velikost ztráty částečná data.</span><span class="sxs-lookup"><span data-stu-id="36eb7-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span></span> <span data-ttu-id="36eb7-158">Nakonec snižuje velikost zpět na původní hodnotu a znovu inicializuje všechny elementy pole.</span><span class="sxs-lookup"><span data-stu-id="36eb7-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span></span>  
  
 [!code-vb[VbVbalrStatements#52](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/redim-statement_1.vb)]  
  
 <span data-ttu-id="36eb7-159">`Dim` Příkaz vytvoří nové pole s tři dimenze.</span><span class="sxs-lookup"><span data-stu-id="36eb7-159">The `Dim` statement creates a new array with three dimensions.</span></span> <span data-ttu-id="36eb7-160">Každá dimenze je deklarovaný s mez 10, takže index pole pro každý dimenze může být v rozsahu od 0 až 10.</span><span class="sxs-lookup"><span data-stu-id="36eb7-160">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span></span> <span data-ttu-id="36eb7-161">V následující diskusi tři dimenze jsou označovány jako vrstvy, řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="36eb7-161">In the following discussion, the three dimensions are referred to as layer, row, and column.</span></span>  
  
 <span data-ttu-id="36eb7-162">První `ReDim` vytvoří nové pole, které nahradí stávající pole v proměnné `intArray`.</span><span class="sxs-lookup"><span data-stu-id="36eb7-162">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span></span> <span data-ttu-id="36eb7-163">`ReDim`zkopíruje všechny elementy z existující pole do nové pole.</span><span class="sxs-lookup"><span data-stu-id="36eb7-163">`ReDim` copies all the elements from the existing array into the new array.</span></span> <span data-ttu-id="36eb7-164">Také přidá na konec každý řádek v každé vrstvě 10 více sloupců a inicializuje elementů v tyto nové sloupce na hodnotu 0 (výchozí hodnota `Integer`, což je typ elementu pole).</span><span class="sxs-lookup"><span data-stu-id="36eb7-164">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span></span>  
  
 <span data-ttu-id="36eb7-165">Druhý `ReDim` vytvoří jiné nové pole a zkopíruje všechny prvky, které vyhovují.</span><span class="sxs-lookup"><span data-stu-id="36eb7-165">The second `ReDim` creates another new array and copies all the elements that fit.</span></span> <span data-ttu-id="36eb7-166">Pět sloupce jsou však ztraceny od konce každý řádek v každé vrstvě.</span><span class="sxs-lookup"><span data-stu-id="36eb7-166">However, five columns are lost from the end of every row in every layer.</span></span> <span data-ttu-id="36eb7-167">To není problém, pokud dokončíte používání těchto sloupců.</span><span class="sxs-lookup"><span data-stu-id="36eb7-167">This is not a problem if you have finished using these columns.</span></span> <span data-ttu-id="36eb7-168">Zmenšení velikosti velké pole můžete uvolnit paměť, která již nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="36eb7-168">Reducing the size of a large array can free up memory that you no longer need.</span></span>  
  
 <span data-ttu-id="36eb7-169">Třetí `ReDim` vytvoří jiné nové pole a odebere jiné pět sloupců z konce každý řádek v každé vrstvě.</span><span class="sxs-lookup"><span data-stu-id="36eb7-169">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span></span> <span data-ttu-id="36eb7-170">Tentokrát ho nekopíruje existující prvky.</span><span class="sxs-lookup"><span data-stu-id="36eb7-170">This time it does not copy any existing elements.</span></span> <span data-ttu-id="36eb7-171">Tento příkaz vrátí pole pro její původní velikost.</span><span class="sxs-lookup"><span data-stu-id="36eb7-171">This statement reverts the array to its original size.</span></span> <span data-ttu-id="36eb7-172">Vzhledem k tomu, že neobsahuje příkaz `Preserve` modifikátor, nastaví všechny elementy pole na původní výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="36eb7-172">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span></span>  
  
 <span data-ttu-id="36eb7-173">Další příklady najdete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="36eb7-173">For additional examples, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36eb7-174">Viz také</span><span class="sxs-lookup"><span data-stu-id="36eb7-174">See Also</span></span>  
 <xref:System.IndexOutOfRangeException>  
 [<span data-ttu-id="36eb7-175">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="36eb7-175">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="36eb7-176">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="36eb7-176">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="36eb7-177">Erase – příkaz</span><span class="sxs-lookup"><span data-stu-id="36eb7-177">Erase Statement</span></span>](../../../visual-basic/language-reference/statements/erase-statement.md)  
 [<span data-ttu-id="36eb7-178">Nic</span><span class="sxs-lookup"><span data-stu-id="36eb7-178">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="36eb7-179">Pole</span><span class="sxs-lookup"><span data-stu-id="36eb7-179">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
