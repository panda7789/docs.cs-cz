---
title: ReDim – příkaz
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
ms.openlocfilehash: fabfd9a45d47cc1b881b3743181a03e89158f939
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346742"
---
# <a name="redim-statement-visual-basic"></a><span data-ttu-id="3fc0f-102">ReDim – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fc0f-102">ReDim Statement (Visual Basic)</span></span>
<span data-ttu-id="3fc0f-103">Znovu přidělí prostor úložiště pro proměnnou pole.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-103">Reallocates storage space for an array variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fc0f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fc0f-104">Syntax</span></span>  
  
```vb  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="3fc0f-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="3fc0f-105">Parts</span></span>  
  
|<span data-ttu-id="3fc0f-106">Termín</span><span class="sxs-lookup"><span data-stu-id="3fc0f-106">Term</span></span>|<span data-ttu-id="3fc0f-107">Definice</span><span class="sxs-lookup"><span data-stu-id="3fc0f-107">Definition</span></span>|  
|----------|----------------|  
|`Preserve`|<span data-ttu-id="3fc0f-108">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-108">Optional.</span></span> <span data-ttu-id="3fc0f-109">Modifikátor používaný k zachování dat v existujícím poli při změně velikosti pouze poslední dimenze.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span></span>|  
|`name`|<span data-ttu-id="3fc0f-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-110">Required.</span></span> <span data-ttu-id="3fc0f-111">Název proměnné pole</span><span class="sxs-lookup"><span data-stu-id="3fc0f-111">Name of the array variable.</span></span> <span data-ttu-id="3fc0f-112">Viz [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="3fc0f-112">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`boundlist`|<span data-ttu-id="3fc0f-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-113">Required.</span></span> <span data-ttu-id="3fc0f-114">Seznam hranic jednotlivých dimenzí předefinovaného pole</span><span class="sxs-lookup"><span data-stu-id="3fc0f-114">List of bounds of each dimension of the redefined array.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fc0f-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3fc0f-115">Remarks</span></span>  
 <span data-ttu-id="3fc0f-116">Pomocí příkazu `ReDim` můžete změnit velikost jedné nebo více dimenzí pole, které již bylo deklarováno.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span></span> <span data-ttu-id="3fc0f-117">Pokud máte velké pole a již nepotřebujete některé z jeho prvků, `ReDim` může uvolnit paměť zmenšením velikosti pole.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span></span> <span data-ttu-id="3fc0f-118">Na druhé straně, pokud vaše pole potřebuje více prvků, `ReDim` je může přidat.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span></span>  
  
 <span data-ttu-id="3fc0f-119">Příkaz `ReDim` je určen pouze pro pole.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-119">The `ReDim` statement is intended only for arrays.</span></span> <span data-ttu-id="3fc0f-120">Není platná pro skalární hodnoty (proměnné, které obsahují pouze jednu hodnotu), kolekce nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span></span> <span data-ttu-id="3fc0f-121">Všimněte si, že pokud deklarujete proměnnou, která má být typu `Array`, příkaz `ReDim` neobsahuje dostatečné informace o typu pro vytvoření nového pole.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span></span>  
  
 <span data-ttu-id="3fc0f-122">`ReDim` můžete použít jenom na úrovni procedury.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-122">You can use `ReDim` only at procedure level.</span></span> <span data-ttu-id="3fc0f-123">Proto kontext deklarace pro proměnnou musí být procedura; nemůže to být zdrojový soubor, obor názvů, rozhraní, třída, struktura, modul nebo blok.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span></span> <span data-ttu-id="3fc0f-124">Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3fc0f-124">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3fc0f-125">Pravidla</span><span class="sxs-lookup"><span data-stu-id="3fc0f-125">Rules</span></span>  
  
- <span data-ttu-id="3fc0f-126">**Několik proměnných.**</span><span class="sxs-lookup"><span data-stu-id="3fc0f-126">**Multiple Variables.**</span></span> <span data-ttu-id="3fc0f-127">Můžete změnit velikost několika proměnných pole v rámci jednoho příkazu deklarace a určit `name` a `boundlist` části pro každou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span></span> <span data-ttu-id="3fc0f-128">Více proměnných je odděleno čárkami.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-128">Multiple variables are separated by commas.</span></span>  
  
- <span data-ttu-id="3fc0f-129">**Meze pole.**</span><span class="sxs-lookup"><span data-stu-id="3fc0f-129">**Array Bounds.**</span></span> <span data-ttu-id="3fc0f-130">Každá položka v `boundlist` může určit dolní a horní hranici dané dimenze.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span></span> <span data-ttu-id="3fc0f-131">Dolní mez je vždycky 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="3fc0f-131">The lower bound is always 0 (zero).</span></span> <span data-ttu-id="3fc0f-132">Horní mez představuje nejvyšší možnou hodnotu indexu pro tuto dimenzi, nikoli délku dimenze (což je horní mez plus jedna).</span><span class="sxs-lookup"><span data-stu-id="3fc0f-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span></span> <span data-ttu-id="3fc0f-133">Index pro každou dimenzi se může od nuly lišit hodnotou horní meze.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-133">The index for each dimension can vary from 0 through its upper bound value.</span></span>  
  
     <span data-ttu-id="3fc0f-134">Počet rozměrů v `boundlist` musí odpovídat původnímu počtu rozměrů pole (Rank).</span><span class="sxs-lookup"><span data-stu-id="3fc0f-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span></span>  
  
- <span data-ttu-id="3fc0f-135">**Datové typy.**</span><span class="sxs-lookup"><span data-stu-id="3fc0f-135">**Data Types.**</span></span> <span data-ttu-id="3fc0f-136">Příkaz `ReDim` nemůže změnit datový typ proměnné pole nebo jejích elementů.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span></span>  
  
- <span data-ttu-id="3fc0f-137">**Operace.**</span><span class="sxs-lookup"><span data-stu-id="3fc0f-137">**Initialization.**</span></span> <span data-ttu-id="3fc0f-138">Příkaz `ReDim` nemůže poskytnout nové inicializační hodnoty pro prvky pole.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span></span>  
  
- <span data-ttu-id="3fc0f-139">**Pořadí.**</span><span class="sxs-lookup"><span data-stu-id="3fc0f-139">**Rank.**</span></span> <span data-ttu-id="3fc0f-140">Příkaz `ReDim` nemůže změnit pořadí (počet rozměrů) pole.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span></span>  
  
- <span data-ttu-id="3fc0f-141">**Změna velikosti se zachováním zachovat.**</span><span class="sxs-lookup"><span data-stu-id="3fc0f-141">**Resizing with Preserve.**</span></span> <span data-ttu-id="3fc0f-142">Pokud používáte `Preserve`, můžete změnit velikost pouze poslední dimenze pole.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-142">If you use `Preserve`, you can resize only the last dimension of the array.</span></span> <span data-ttu-id="3fc0f-143">Pro všechny ostatní dimenze je nutné zadat hranici existujícího pole.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-143">For every other dimension, you must specify the bound of the existing array.</span></span>  
  
     <span data-ttu-id="3fc0f-144">Například pokud má vaše pole pouze jednu dimenzi, můžete změnit velikost této dimenze a zachovat obsah pole, protože měníte poslední a pouze dimenzi.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span></span> <span data-ttu-id="3fc0f-145">Pokud má ale vaše pole dvě nebo více dimenzí, můžete změnit velikost jenom poslední dimenze, pokud používáte `Preserve`.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span></span>  
  
- <span data-ttu-id="3fc0f-146">**Vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="3fc0f-146">**Properties.**</span></span> <span data-ttu-id="3fc0f-147">Můžete použít `ReDim` u vlastnosti, která obsahuje pole hodnot.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-147">You can use `ReDim` on a property that holds an array of values.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="3fc0f-148">Chování</span><span class="sxs-lookup"><span data-stu-id="3fc0f-148">Behavior</span></span>  
  
- <span data-ttu-id="3fc0f-149">**Nahrazení pole**</span><span class="sxs-lookup"><span data-stu-id="3fc0f-149">**Array Replacement.**</span></span> <span data-ttu-id="3fc0f-150">`ReDim` uvolní existující pole a vytvoří nové pole se stejným pořadím.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-150">`ReDim` releases the existing array and creates a new array with the same rank.</span></span> <span data-ttu-id="3fc0f-151">Nové pole nahradí uvolněné pole v proměnné pole.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-151">The new array replaces the released array in the array variable.</span></span>  
  
- <span data-ttu-id="3fc0f-152">**Inicializace bez zachování.**</span><span class="sxs-lookup"><span data-stu-id="3fc0f-152">**Initialization without Preserve.**</span></span> <span data-ttu-id="3fc0f-153">Pokud nezadáte `Preserve`, `ReDim` inicializuje prvky nového pole pomocí výchozí hodnoty pro svůj datový typ.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span></span>  
  
- <span data-ttu-id="3fc0f-154">**Inicializace s zachovat.**</span><span class="sxs-lookup"><span data-stu-id="3fc0f-154">**Initialization with Preserve.**</span></span> <span data-ttu-id="3fc0f-155">Pokud zadáte `Preserve`, Visual Basic zkopíruje prvky z existujícího pole do nového pole.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fc0f-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="3fc0f-156">Example</span></span>  
 <span data-ttu-id="3fc0f-157">Následující příklad zvětší velikost poslední dimenze dynamického pole, aniž by ztratila všechna existující data v poli, a pak zmenší velikost s částečnou ztrátou dat.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span></span> <span data-ttu-id="3fc0f-158">Nakonec zmenší velikost zpátky na původní hodnotu a znovu inicializuje všechny prvky pole.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span></span>  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 <span data-ttu-id="3fc0f-159">Příkaz `Dim` vytvoří nové pole se třemi dimenzemi.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-159">The `Dim` statement creates a new array with three dimensions.</span></span> <span data-ttu-id="3fc0f-160">Každá dimenze je deklarována s hranicí 10, takže index pole pro každou dimenzi může být v rozsahu od 0 do 10.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-160">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span></span> <span data-ttu-id="3fc0f-161">V následující diskuzi se tři dimenze označují jako vrstvy, řádky a sloupce.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-161">In the following discussion, the three dimensions are referred to as layer, row, and column.</span></span>  
  
 <span data-ttu-id="3fc0f-162">První `ReDim` vytvoří nové pole, které nahradí existující pole v proměnné `intArray`.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-162">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span></span> <span data-ttu-id="3fc0f-163">`ReDim` zkopíruje všechny prvky z existujícího pole do nového pole.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-163">`ReDim` copies all the elements from the existing array into the new array.</span></span> <span data-ttu-id="3fc0f-164">Přidává také 10 dalších sloupců na konec každého řádku v každé vrstvě a inicializuje prvky v těchto nových sloupcích na 0 (výchozí hodnota `Integer`, což je typ prvku pole).</span><span class="sxs-lookup"><span data-stu-id="3fc0f-164">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span></span>  
  
 <span data-ttu-id="3fc0f-165">Druhý `ReDim` vytvoří další nové pole a zkopíruje všechny prvky, které odpovídají.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-165">The second `ReDim` creates another new array and copies all the elements that fit.</span></span> <span data-ttu-id="3fc0f-166">Nicméně pět sloupců se na konci každého řádku v každé vrstvě ztratí.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-166">However, five columns are lost from the end of every row in every layer.</span></span> <span data-ttu-id="3fc0f-167">Nejedná se o problém, pokud jste s použitím těchto sloupců dokončili.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-167">This is not a problem if you have finished using these columns.</span></span> <span data-ttu-id="3fc0f-168">Zmenšení velikosti velkého pole může uvolnit paměť, kterou už nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-168">Reducing the size of a large array can free up memory that you no longer need.</span></span>  
  
 <span data-ttu-id="3fc0f-169">Třetí `ReDim` vytvoří další nové pole a z konce každého řádku v každé vrstvě odebere další pět sloupců.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-169">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span></span> <span data-ttu-id="3fc0f-170">Tentokrát nekopíruje žádné existující prvky.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-170">This time it does not copy any existing elements.</span></span> <span data-ttu-id="3fc0f-171">Tento příkaz vrátí pole do původní velikosti.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-171">This statement reverts the array to its original size.</span></span> <span data-ttu-id="3fc0f-172">Vzhledem k tomu, že příkaz neobsahuje modifikátor `Preserve`, nastaví všechny prvky pole na původní výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-172">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span></span>  
  
 <span data-ttu-id="3fc0f-173">Další příklady naleznete v tématu [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="3fc0f-173">For additional examples, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fc0f-174">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3fc0f-174">See also</span></span>

- <xref:System.IndexOutOfRangeException>
- [<span data-ttu-id="3fc0f-175">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="3fc0f-175">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="3fc0f-176">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="3fc0f-176">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="3fc0f-177">Příkaz Erase</span><span class="sxs-lookup"><span data-stu-id="3fc0f-177">Erase Statement</span></span>](../../../visual-basic/language-reference/statements/erase-statement.md)
- [<span data-ttu-id="3fc0f-178">Nothing</span><span class="sxs-lookup"><span data-stu-id="3fc0f-178">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="3fc0f-179">Pole</span><span class="sxs-lookup"><span data-stu-id="3fc0f-179">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
