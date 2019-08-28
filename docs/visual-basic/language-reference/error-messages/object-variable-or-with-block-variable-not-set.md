---
title: Objektová proměnná nebo proměnná bloku With nebyla nastavena.
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 07c215d373e4ac1cbadf82a48b8cb3d90efdbdb4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040556"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="ab81b-102">Objektová proměnná nebo proměnná bloku With nebyla nastavena.</span><span class="sxs-lookup"><span data-stu-id="ab81b-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="ab81b-103">Je odkazováno na neplatnou proměnnou objektu.</span><span class="sxs-lookup"><span data-stu-id="ab81b-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="ab81b-104">K této chybě může dojít z několika důvodů:</span><span class="sxs-lookup"><span data-stu-id="ab81b-104">This error can occur for several reasons:</span></span>

- <span data-ttu-id="ab81b-105">Proměnná byla deklarována bez určení typu.</span><span class="sxs-lookup"><span data-stu-id="ab81b-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="ab81b-106">Je-li proměnná deklarována bez určení typu, je použita výchozí hodnota `Object`typu.</span><span class="sxs-lookup"><span data-stu-id="ab81b-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>

    <span data-ttu-id="ab81b-107">`Dim x` Například Proměnná deklarovaná s by měla být typu `Object;` proměnná s `Dim x As String` deklarací by byla typu `String`.</span><span class="sxs-lookup"><span data-stu-id="ab81b-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>

    > [!TIP]
    > <span data-ttu-id="ab81b-108">Příkaz nepovoluje implicitní zadání, které má `Object` za následek typ. `Option Strict`</span><span class="sxs-lookup"><span data-stu-id="ab81b-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="ab81b-109">Pokud vynecháte typ, dojde k chybě při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="ab81b-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="ab81b-110">Viz [příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ab81b-110">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>

- <span data-ttu-id="ab81b-111">Pokoušíte se vytvořit odkaz na objekt, který byl nastaven na `Nothing`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ab81b-111">You are attempting to reference an object that has been set to `Nothing`.</span></span>

- <span data-ttu-id="ab81b-112">Pokoušíte se o přístup k prvku proměnné pole, která nebyla správně deklarována.</span><span class="sxs-lookup"><span data-stu-id="ab81b-112">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>

    <span data-ttu-id="ab81b-113">Například pole deklarované jako `products() As String` aktivuje chybu, pokud se pokusíte odkazovat na prvek pole. `products(3) = "Widget"`</span><span class="sxs-lookup"><span data-stu-id="ab81b-113">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="ab81b-114">Pole nemá žádné elementy a je považováno za objekt.</span><span class="sxs-lookup"><span data-stu-id="ab81b-114">The array has no elements and is treated as an object.</span></span>

- <span data-ttu-id="ab81b-115">Pokoušíte se o přístup k kódu v rámci `With...End With` bloku před inicializací bloku.</span><span class="sxs-lookup"><span data-stu-id="ab81b-115">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="ab81b-116">Blok musí být inicializován `With` spuštěním vstupního bodu příkazu. `With...End With`</span><span class="sxs-lookup"><span data-stu-id="ab81b-116">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>

> [!NOTE]
> <span data-ttu-id="ab81b-117">V dřívějších verzích Visual Basic nebo v jazyce VBA se tato chyba aktivovala také přiřazením hodnoty proměnné bez použití `Set` klíčového slova (`x = "name"` místo `Set x = "name"`).</span><span class="sxs-lookup"><span data-stu-id="ab81b-117">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="ab81b-118">`Set` Klíčové slovo již není platné v Visual Basic .NET.</span><span class="sxs-lookup"><span data-stu-id="ab81b-118">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ab81b-119">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ab81b-119">To correct this error</span></span>

1. <span data-ttu-id="ab81b-120">Nastavte `Option Strict` na`On` začátek souboru přidáním následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="ab81b-120">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>

    ```vb
    Option Strict On
    ```

    <span data-ttu-id="ab81b-121">Při spuštění projektu se zobrazí chyba kompilátoru v **Seznam chyb** pro jakoukoliv proměnnou, která byla zadána bez typu.</span><span class="sxs-lookup"><span data-stu-id="ab81b-121">When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.</span></span>

2. <span data-ttu-id="ab81b-122">Pokud nechcete povolit `Option Strict`, vyhledejte v kódu proměnné, které byly zadány bez typu (`Dim x` namísto `Dim x As String`) a přidejte do deklarace zamýšlený typ.</span><span class="sxs-lookup"><span data-stu-id="ab81b-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>

3. <span data-ttu-id="ab81b-123">Ujistěte se, že neodkazujete na proměnnou objektu, která je nastavená na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ab81b-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="ab81b-124">Vyhledejte kód klíčového slova `Nothing`a upravte kód tak, aby objekt nebyl nastaven na `Nothing` hodnotu až po jeho odkazování.</span><span class="sxs-lookup"><span data-stu-id="ab81b-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>

4. <span data-ttu-id="ab81b-125">Ujistěte se, že všechny proměnné pole jsou dimenze, než k nim přistupujete.</span><span class="sxs-lookup"><span data-stu-id="ab81b-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="ab81b-126">Dimenzi můžete přiřadit buď při prvním vytvoření pole (`Dim x(5) As String` `Dim x() As String`místo `ReDim` ), nebo pomocí klíčového slova pro nastavení rozměrů pole před prvním přístupem.</span><span class="sxs-lookup"><span data-stu-id="ab81b-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>

5. <span data-ttu-id="ab81b-127">Zajistěte `With` , aby byl váš blok inicializován `With` spuštěním vstupního bodu příkazu.</span><span class="sxs-lookup"><span data-stu-id="ab81b-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab81b-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab81b-128">See also</span></span>

- [<span data-ttu-id="ab81b-129">Deklarace objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="ab81b-129">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="ab81b-130">Příkaz ReDim</span><span class="sxs-lookup"><span data-stu-id="ab81b-130">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="ab81b-131">Příkaz With...End With</span><span class="sxs-lookup"><span data-stu-id="ab81b-131">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
