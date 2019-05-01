---
title: Objektová proměnná nebo proměnná bloku With nebyla nastavena.
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 766b95163f164ec76135b964115069b6855ceebf
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807876"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="14ba1-102">Objektová proměnná nebo proměnná bloku With nebyla nastavena.</span><span class="sxs-lookup"><span data-stu-id="14ba1-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="14ba1-103">Odkazují na neplatný objekt proměnnou.</span><span class="sxs-lookup"><span data-stu-id="14ba1-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="14ba1-104">Této chybě může dojít z několika důvodů:</span><span class="sxs-lookup"><span data-stu-id="14ba1-104">This error can occur for several reasons:</span></span>

- <span data-ttu-id="14ba1-105">Proměnná byla deklarovaná bez zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="14ba1-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="14ba1-106">Pokud je proměnná deklarována bez určení typu, použije se výchozí typ `Object`.</span><span class="sxs-lookup"><span data-stu-id="14ba1-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>

    <span data-ttu-id="14ba1-107">Například proměnná deklarovaná pomocí `Dim x` budou mít typ `Object;` proměnná deklarovaná pomocí `Dim x As String` budou mít typ `String`.</span><span class="sxs-lookup"><span data-stu-id="14ba1-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>

    > [!TIP]
    >  <span data-ttu-id="14ba1-108">`Option Strict` Příkaz zakáže implicitního zápisu, která vede `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="14ba1-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="14ba1-109">Vynecháte-li typ, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="14ba1-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="14ba1-110">Zobrazit [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="14ba1-110">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>

- <span data-ttu-id="14ba1-111">Pokoušíte se odkazovat na objekt, který je nastavená na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="14ba1-111">You are attempting to reference an object that has been set to `Nothing`.</span></span>

- <span data-ttu-id="14ba1-112">Pokoušíte se o přístup k prvku, který nebyl správně deklarované proměnné pole.</span><span class="sxs-lookup"><span data-stu-id="14ba1-112">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>

    <span data-ttu-id="14ba1-113">Například pole deklarované jako `products() As String` chyba se aktivuje, pokud se pokusíte odkazovat na prvek pole `products(3) = "Widget"`.</span><span class="sxs-lookup"><span data-stu-id="14ba1-113">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="14ba1-114">Pole neobsahuje žádné prvky a je považován za objekt.</span><span class="sxs-lookup"><span data-stu-id="14ba1-114">The array has no elements and is treated as an object.</span></span>

- <span data-ttu-id="14ba1-115">Pokoušíte se přístupový kód v rámci `With...End With` blokovat před inicializací bloku.</span><span class="sxs-lookup"><span data-stu-id="14ba1-115">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="14ba1-116">A `With...End With` bloku se musí inicializovat pomocí provádí `With` příkaz vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="14ba1-116">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>

> [!NOTE]
> <span data-ttu-id="14ba1-117">V dřívějších verzích jazyka Visual Basic nebo VBA k této chybě také aktivovaly přiřazení hodnoty proměnné bez použití `Set` – klíčové slovo (`x = "name"` místo `Set x = "name"`).</span><span class="sxs-lookup"><span data-stu-id="14ba1-117">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="14ba1-118">`Set` – Klíčové slovo již není platný v jazyce Visual Basic .net.</span><span class="sxs-lookup"><span data-stu-id="14ba1-118">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="14ba1-119">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="14ba1-119">To correct this error</span></span>

1. <span data-ttu-id="14ba1-120">Nastavte `Option Strict` k `On` na začátek souboru přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="14ba1-120">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>

    ```vb
    Option Strict On
    ```

    <span data-ttu-id="14ba1-121">Při spuštění projektu se objevit Chyba kompilátoru **seznam chyb** jakékoli proměnné, který byl zadán bez typu.</span><span class="sxs-lookup"><span data-stu-id="14ba1-121">When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.</span></span>

2. <span data-ttu-id="14ba1-122">Pokud nechcete povolit `Option Strict`, vyhledávání v kódu pro všechny proměnné, které byly zadány bez typu (`Dim x` místo `Dim x As String`) a přidejte odpovídající typu k deklaraci.</span><span class="sxs-lookup"><span data-stu-id="14ba1-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>

3. <span data-ttu-id="14ba1-123">Ujistěte se, že nejsou odkazující na proměnné objektu, která byla nastavena na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="14ba1-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="14ba1-124">Vyhledávání v kódu pro klíčové slovo `Nothing`a upravte kód tak, aby objekt není nastaven na `Nothing` až poté, co mají odkazovat.</span><span class="sxs-lookup"><span data-stu-id="14ba1-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>

4. <span data-ttu-id="14ba1-125">Ujistěte se, že jsou všechny proměnné pole dimenzovanými předtím, než k nim přístup.</span><span class="sxs-lookup"><span data-stu-id="14ba1-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="14ba1-126">Dimenze můžete přiřadit při prvním vytvoření pole (`Dim x(5) As String` místo `Dim x() As String`), nebo použijte `ReDim` – klíčové slovo k nastavení rozměrů pole před první přístup.</span><span class="sxs-lookup"><span data-stu-id="14ba1-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>

5. <span data-ttu-id="14ba1-127">Ujistěte se, že vaše `With` bloku je inicializován pomocí provádí `With` příkaz vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="14ba1-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="14ba1-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14ba1-128">See also</span></span>

- [<span data-ttu-id="14ba1-129">Deklarace objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="14ba1-129">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="14ba1-130">Příkaz ReDim</span><span class="sxs-lookup"><span data-stu-id="14ba1-130">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="14ba1-131">Příkaz With...End With</span><span class="sxs-lookup"><span data-stu-id="14ba1-131">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
