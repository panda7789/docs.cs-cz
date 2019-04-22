---
title: ReDim – příkaz (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 8f5f3172eaa6b43d9b07aefa0036708b26087777
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824114"
---
# <a name="redim-statement-visual-basic"></a><span data-ttu-id="dff89-102">ReDim – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dff89-102">ReDim Statement (Visual Basic)</span></span>
<span data-ttu-id="dff89-103">Znovu alokuje prostor úložiště pro proměnné pole.</span><span class="sxs-lookup"><span data-stu-id="dff89-103">Reallocates storage space for an array variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dff89-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dff89-104">Syntax</span></span>  
  
```  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="dff89-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="dff89-105">Parts</span></span>  
  
|<span data-ttu-id="dff89-106">Termín</span><span class="sxs-lookup"><span data-stu-id="dff89-106">Term</span></span>|<span data-ttu-id="dff89-107">Definice</span><span class="sxs-lookup"><span data-stu-id="dff89-107">Definition</span></span>|  
|----------|----------------|  
|`Preserve`|<span data-ttu-id="dff89-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="dff89-108">Optional.</span></span> <span data-ttu-id="dff89-109">Modifikátor se používá k zachování dat v existujícím poli, když změníte velikost jenom poslední dimenze.</span><span class="sxs-lookup"><span data-stu-id="dff89-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span></span>|  
|`name`|<span data-ttu-id="dff89-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="dff89-110">Required.</span></span> <span data-ttu-id="dff89-111">Název proměnné pole.</span><span class="sxs-lookup"><span data-stu-id="dff89-111">Name of the array variable.</span></span> <span data-ttu-id="dff89-112">Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="dff89-112">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`boundlist`|<span data-ttu-id="dff89-113">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="dff89-113">Required.</span></span> <span data-ttu-id="dff89-114">Seznam mezí jednotlivých rozměrů pole Předefinovaná.</span><span class="sxs-lookup"><span data-stu-id="dff89-114">List of bounds of each dimension of the redefined array.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dff89-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dff89-115">Remarks</span></span>  
 <span data-ttu-id="dff89-116">Můžete použít `ReDim` příkaz ke změně velikosti jednu nebo více dimenzí pole, které je už deklarovaný.</span><span class="sxs-lookup"><span data-stu-id="dff89-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span></span> <span data-ttu-id="dff89-117">Pokud máte velké pole a které už nepotřebujete, některé z jeho prvků `ReDim` může uvolnit paměť snížením velikosti pole.</span><span class="sxs-lookup"><span data-stu-id="dff89-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span></span> <span data-ttu-id="dff89-118">Na druhou stranu, pokud další prvky, musí vaše pole `ReDim` můžete je přidat.</span><span class="sxs-lookup"><span data-stu-id="dff89-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span></span>  
  
 <span data-ttu-id="dff89-119">`ReDim` Příkaz je určena pouze pro pole.</span><span class="sxs-lookup"><span data-stu-id="dff89-119">The `ReDim` statement is intended only for arrays.</span></span> <span data-ttu-id="dff89-120">Není platný v skaláry (proměnné, které obsahují jenom jedna hodnota), kolekce nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="dff89-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span></span> <span data-ttu-id="dff89-121">Všimněte si, že pokud deklarujete proměnnou typu `Array`, `ReDim` příkaz nemá dostatek informací o typu k vytvoření nové pole.</span><span class="sxs-lookup"><span data-stu-id="dff89-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span></span>  
  
 <span data-ttu-id="dff89-122">Můžete použít `ReDim` pouze na úrovni postup.</span><span class="sxs-lookup"><span data-stu-id="dff89-122">You can use `ReDim` only at procedure level.</span></span> <span data-ttu-id="dff89-123">Místní deklarace proměnné proto musí být postup; ho nemůže být zdrojový soubor, obor názvů, rozhraní, třídy, struktury, modul nebo blok.</span><span class="sxs-lookup"><span data-stu-id="dff89-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span></span> <span data-ttu-id="dff89-124">Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="dff89-124">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="dff89-125">pravidla</span><span class="sxs-lookup"><span data-stu-id="dff89-125">Rules</span></span>  
  
-   <span data-ttu-id="dff89-126">**Více proměnných.**</span><span class="sxs-lookup"><span data-stu-id="dff89-126">**Multiple Variables.**</span></span> <span data-ttu-id="dff89-127">Můžete změnit velikost několik proměnných ve stejném příkazu deklarace a určit, `name` a `boundlist` částí pro každou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="dff89-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span></span> <span data-ttu-id="dff89-128">Více proměnných jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="dff89-128">Multiple variables are separated by commas.</span></span>  
  
-   <span data-ttu-id="dff89-129">**Array Bounds.**</span><span class="sxs-lookup"><span data-stu-id="dff89-129">**Array Bounds.**</span></span> <span data-ttu-id="dff89-130">Každá položka v `boundlist` můžete zadat, dolní a horní hranice této dimenze.</span><span class="sxs-lookup"><span data-stu-id="dff89-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span></span> <span data-ttu-id="dff89-131">Dolní mez je vždy 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="dff89-131">The lower bound is always 0 (zero).</span></span> <span data-ttu-id="dff89-132">Horní mez je nejvyšší hodnota možný index pro tuto dimenzi, nikoli velikost rozměru (což je horní mez plus jedna).</span><span class="sxs-lookup"><span data-stu-id="dff89-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span></span> <span data-ttu-id="dff89-133">Index každé dimenze se může lišit od 0 do jeho hodnotu horní mez.</span><span class="sxs-lookup"><span data-stu-id="dff89-133">The index for each dimension can vary from 0 through its upper bound value.</span></span>  
  
     <span data-ttu-id="dff89-134">Počet dimenzí v `boundlist` musí odpovídat původní počet rozměrů (pořadí) pole.</span><span class="sxs-lookup"><span data-stu-id="dff89-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span></span>  
  
-   <span data-ttu-id="dff89-135">**Datové typy.**</span><span class="sxs-lookup"><span data-stu-id="dff89-135">**Data Types.**</span></span> <span data-ttu-id="dff89-136">`ReDim` Příkaz nelze změnit datový typ proměnné pole nebo jeho elementů.</span><span class="sxs-lookup"><span data-stu-id="dff89-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span></span>  
  
-   <span data-ttu-id="dff89-137">**Inicializace.**</span><span class="sxs-lookup"><span data-stu-id="dff89-137">**Initialization.**</span></span> <span data-ttu-id="dff89-138">`ReDim` Příkaz nelze zadat nové inicializace hodnoty pro prvky pole.</span><span class="sxs-lookup"><span data-stu-id="dff89-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span></span>  
  
-   <span data-ttu-id="dff89-139">**Pořadí.**</span><span class="sxs-lookup"><span data-stu-id="dff89-139">**Rank.**</span></span> <span data-ttu-id="dff89-140">`ReDim` Příkaz nelze změnit pořadí (počet rozměrů) v poli.</span><span class="sxs-lookup"><span data-stu-id="dff89-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span></span>  
  
-   <span data-ttu-id="dff89-141">**Změna velikosti se zachová.**</span><span class="sxs-lookup"><span data-stu-id="dff89-141">**Resizing with Preserve.**</span></span> <span data-ttu-id="dff89-142">Pokud používáte `Preserve`, změníte velikost jenom poslední dimenze pole.</span><span class="sxs-lookup"><span data-stu-id="dff89-142">If you use `Preserve`, you can resize only the last dimension of the array.</span></span> <span data-ttu-id="dff89-143">Pro každou dimenzi je nutné zadat mez existujícího pole.</span><span class="sxs-lookup"><span data-stu-id="dff89-143">For every other dimension, you must specify the bound of the existing array.</span></span>  
  
     <span data-ttu-id="dff89-144">Například pokud vaše pole má pouze jednu dimenzi, můžete změnit velikost daná dimenze a zároveň zachovat veškerý obsah pole, protože se mění poslední a pouze dimenze.</span><span class="sxs-lookup"><span data-stu-id="dff89-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span></span> <span data-ttu-id="dff89-145">Nicméně pokud vaše pole má dvě nebo více dimenzí, můžete změnit velikost jenom poslední dimenze používáte `Preserve`.</span><span class="sxs-lookup"><span data-stu-id="dff89-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span></span>  
  
-   <span data-ttu-id="dff89-146">**Vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="dff89-146">**Properties.**</span></span> <span data-ttu-id="dff89-147">Můžete použít `ReDim` na vlastnost, která obsahuje pole hodnot.</span><span class="sxs-lookup"><span data-stu-id="dff89-147">You can use `ReDim` on a property that holds an array of values.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="dff89-148">Chování</span><span class="sxs-lookup"><span data-stu-id="dff89-148">Behavior</span></span>  
  
-   <span data-ttu-id="dff89-149">**Nahrazení pole.**</span><span class="sxs-lookup"><span data-stu-id="dff89-149">**Array Replacement.**</span></span> <span data-ttu-id="dff89-150">`ReDim` uvolní existujícího pole a vytvoří nové pole obsahující stejné pořadí.</span><span class="sxs-lookup"><span data-stu-id="dff89-150">`ReDim` releases the existing array and creates a new array with the same rank.</span></span> <span data-ttu-id="dff89-151">Nové pole nahradí vydané pole v proměnné pole.</span><span class="sxs-lookup"><span data-stu-id="dff89-151">The new array replaces the released array in the array variable.</span></span>  
  
-   <span data-ttu-id="dff89-152">**Inicializace bez zachování.**</span><span class="sxs-lookup"><span data-stu-id="dff89-152">**Initialization without Preserve.**</span></span> <span data-ttu-id="dff89-153">Pokud nezadáte `Preserve`, `ReDim` inicializuje elementy nové pole pomocí výchozí hodnota pro jejich datové typy.</span><span class="sxs-lookup"><span data-stu-id="dff89-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span></span>  
  
-   <span data-ttu-id="dff89-154">**Inicializace pomocí zachovat.**</span><span class="sxs-lookup"><span data-stu-id="dff89-154">**Initialization with Preserve.**</span></span> <span data-ttu-id="dff89-155">Pokud zadáte `Preserve`, Visual Basic zkopíruje prvky z existujícího pole do nového pole.</span><span class="sxs-lookup"><span data-stu-id="dff89-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dff89-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="dff89-156">Example</span></span>  
 <span data-ttu-id="dff89-157">Následující příklad zvyšuje velikost poslední dimenze dynamické pole bez ztráty všechna existující data v poli a pak snižuje velikost ztráty částečná data.</span><span class="sxs-lookup"><span data-stu-id="dff89-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span></span> <span data-ttu-id="dff89-158">Nakonec se zmenší velikost zpět na původní hodnotu a znovu inicializuje všechny prvky pole.</span><span class="sxs-lookup"><span data-stu-id="dff89-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span></span>  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 <span data-ttu-id="dff89-159">`Dim` Příkaz vytvoří nové pole s tři dimenze.</span><span class="sxs-lookup"><span data-stu-id="dff89-159">The `Dim` statement creates a new array with three dimensions.</span></span> <span data-ttu-id="dff89-160">Každé dimenze je deklarován s hranicí 10, takže index pole pro jednotlivé rozměry v rozsahu 0 až 10.</span><span class="sxs-lookup"><span data-stu-id="dff89-160">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span></span> <span data-ttu-id="dff89-161">V následující diskuse tři dimenze jsou označovány jako vrstva, řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="dff89-161">In the following discussion, the three dimensions are referred to as layer, row, and column.</span></span>  
  
 <span data-ttu-id="dff89-162">První `ReDim` vytvoří nové pole, která nahradí stávající pole v proměnné `intArray`.</span><span class="sxs-lookup"><span data-stu-id="dff89-162">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span></span> <span data-ttu-id="dff89-163">`ReDim` zkopíruje všechny prvky z existujícího pole do nového pole.</span><span class="sxs-lookup"><span data-stu-id="dff89-163">`ReDim` copies all the elements from the existing array into the new array.</span></span> <span data-ttu-id="dff89-164">Také přidá 10 další sloupce na konci každého řádku v každé vrstvě a inicializuje prvky v těchto nových sloupců na hodnotu 0 (výchozí hodnota `Integer`, což je typ prvku pole).</span><span class="sxs-lookup"><span data-stu-id="dff89-164">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span></span>  
  
 <span data-ttu-id="dff89-165">Druhá `ReDim` vytvoří další nové pole a zkopíruje všechny prvky, které vyhovují.</span><span class="sxs-lookup"><span data-stu-id="dff89-165">The second `ReDim` creates another new array and copies all the elements that fit.</span></span> <span data-ttu-id="dff89-166">Pět sloupců se ale ztratí z konci každého řádku v každé vrstvě.</span><span class="sxs-lookup"><span data-stu-id="dff89-166">However, five columns are lost from the end of every row in every layer.</span></span> <span data-ttu-id="dff89-167">To není problém, pokud jste dokončili pomocí těchto sloupců.</span><span class="sxs-lookup"><span data-stu-id="dff89-167">This is not a problem if you have finished using these columns.</span></span> <span data-ttu-id="dff89-168">Zmenšit velké pole můžete uvolnit paměť, která už nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="dff89-168">Reducing the size of a large array can free up memory that you no longer need.</span></span>  
  
 <span data-ttu-id="dff89-169">Třetí `ReDim` vytvoří další nové pole a odebere jiného pět sloupců z konci každého řádku v každé vrstvě.</span><span class="sxs-lookup"><span data-stu-id="dff89-169">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span></span> <span data-ttu-id="dff89-170">Tentokrát nekopíruje jakýchkoli prvků.</span><span class="sxs-lookup"><span data-stu-id="dff89-170">This time it does not copy any existing elements.</span></span> <span data-ttu-id="dff89-171">Tento příkaz vrátí pole původní velikost.</span><span class="sxs-lookup"><span data-stu-id="dff89-171">This statement reverts the array to its original size.</span></span> <span data-ttu-id="dff89-172">Protože neobsahuje příkaz `Preserve` modifikátor, nastaví všechny prvky pole na původní výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="dff89-172">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span></span>  
  
 <span data-ttu-id="dff89-173">Další příklady najdete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="dff89-173">For additional examples, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dff89-174">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dff89-174">See also</span></span>

- <xref:System.IndexOutOfRangeException>
- [<span data-ttu-id="dff89-175">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="dff89-175">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="dff89-176">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="dff89-176">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="dff89-177">Příkaz Erase</span><span class="sxs-lookup"><span data-stu-id="dff89-177">Erase Statement</span></span>](../../../visual-basic/language-reference/statements/erase-statement.md)
- [<span data-ttu-id="dff89-178">Nothing</span><span class="sxs-lookup"><span data-stu-id="dff89-178">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="dff89-179">Pole</span><span class="sxs-lookup"><span data-stu-id="dff89-179">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
