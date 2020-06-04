---
title: Objektová proměnná nebo proměnná bloku With nebyla nastavena.
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: d1778e2bb58d32e976f10b3fba1637918278d36e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409280"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="8d503-102">Objektová proměnná nebo proměnná bloku With nebyla nastavena.</span><span class="sxs-lookup"><span data-stu-id="8d503-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="8d503-103">Je odkazováno na neplatnou proměnnou objektu.</span><span class="sxs-lookup"><span data-stu-id="8d503-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="8d503-104">K této chybě může dojít z několika důvodů:</span><span class="sxs-lookup"><span data-stu-id="8d503-104">This error can occur for several reasons:</span></span>

- <span data-ttu-id="8d503-105">Proměnná byla deklarována bez určení typu.</span><span class="sxs-lookup"><span data-stu-id="8d503-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="8d503-106">Je-li proměnná deklarována bez určení typu, je použita výchozí hodnota typu `Object` .</span><span class="sxs-lookup"><span data-stu-id="8d503-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>

    <span data-ttu-id="8d503-107">Například Proměnná deklarovaná s by měla `Dim x` být typu `Object;` Proměnná s deklarací `Dim x As String` by byla typu `String` .</span><span class="sxs-lookup"><span data-stu-id="8d503-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>

    > [!TIP]
    > <span data-ttu-id="8d503-108">`Option Strict`Příkaz nepovoluje implicitní zadání, které má za následek `Object` typ.</span><span class="sxs-lookup"><span data-stu-id="8d503-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="8d503-109">Pokud vynecháte typ, dojde k chybě při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="8d503-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="8d503-110">Viz [příkaz Option Strict](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8d503-110">See [Option Strict Statement](../statements/option-strict-statement.md).</span></span>

- <span data-ttu-id="8d503-111">Pokoušíte se vytvořit odkaz na objekt, který byl nastaven na hodnotu `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="8d503-111">You are attempting to reference an object that has been set to `Nothing`.</span></span>

- <span data-ttu-id="8d503-112">Pokoušíte se o přístup k prvku proměnné pole, která nebyla správně deklarována.</span><span class="sxs-lookup"><span data-stu-id="8d503-112">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>

    <span data-ttu-id="8d503-113">Například pole deklarované jako `products() As String` aktivuje chybu, pokud se pokusíte odkazovat na prvek pole `products(3) = "Widget"` .</span><span class="sxs-lookup"><span data-stu-id="8d503-113">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="8d503-114">Pole nemá žádné elementy a je považováno za objekt.</span><span class="sxs-lookup"><span data-stu-id="8d503-114">The array has no elements and is treated as an object.</span></span>

- <span data-ttu-id="8d503-115">Pokoušíte se o přístup k kódu v rámci `With...End With` bloku před inicializací bloku.</span><span class="sxs-lookup"><span data-stu-id="8d503-115">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="8d503-116">`With...End With`Blok musí být inicializován spuštěním `With` vstupního bodu příkazu.</span><span class="sxs-lookup"><span data-stu-id="8d503-116">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>

> [!NOTE]
> <span data-ttu-id="8d503-117">V dřívějších verzích Visual Basic nebo v jazyce VBA se tato chyba aktivovala také přiřazením hodnoty proměnné bez použití `Set` klíčového slova ( `x = "name"` místo `Set x = "name"` ).</span><span class="sxs-lookup"><span data-stu-id="8d503-117">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="8d503-118">`Set`Klíčové slovo již není platné v Visual Basic .NET.</span><span class="sxs-lookup"><span data-stu-id="8d503-118">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8d503-119">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8d503-119">To correct this error</span></span>

1. <span data-ttu-id="8d503-120">Nastavte `Option Strict` na `On` začátek souboru přidáním následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="8d503-120">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>

    ```vb
    Option Strict On
    ```

    <span data-ttu-id="8d503-121">Při spuštění projektu se zobrazí chyba kompilátoru v **Seznam chyb** pro jakoukoliv proměnnou, která byla zadána bez typu.</span><span class="sxs-lookup"><span data-stu-id="8d503-121">When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.</span></span>

2. <span data-ttu-id="8d503-122">Pokud nechcete povolit `Option Strict` , vyhledejte v kódu proměnné, které byly zadány bez typu ( `Dim x` namísto `Dim x As String` ) a přidejte do deklarace zamýšlený typ.</span><span class="sxs-lookup"><span data-stu-id="8d503-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>

3. <span data-ttu-id="8d503-123">Ujistěte se, že neodkazujete na proměnnou objektu, která je nastavená na `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="8d503-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="8d503-124">Vyhledejte kód klíčového slova `Nothing` a upravte kód tak, aby objekt nebyl nastaven na hodnotu `Nothing` až po jeho odkazování.</span><span class="sxs-lookup"><span data-stu-id="8d503-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>

4. <span data-ttu-id="8d503-125">Ujistěte se, že všechny proměnné pole jsou dimenze, než k nim přistupujete.</span><span class="sxs-lookup"><span data-stu-id="8d503-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="8d503-126">Dimenzi můžete přiřadit buď při prvním vytvoření pole ( `Dim x(5) As String` místo `Dim x() As String` ), nebo pomocí `ReDim` klíčového slova pro nastavení rozměrů pole před prvním přístupem.</span><span class="sxs-lookup"><span data-stu-id="8d503-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>

5. <span data-ttu-id="8d503-127">Zajistěte, aby `With` byl váš blok inicializován spuštěním `With` vstupního bodu příkazu.</span><span class="sxs-lookup"><span data-stu-id="8d503-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d503-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d503-128">See also</span></span>

- [<span data-ttu-id="8d503-129">Deklarace proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="8d503-129">Object Variable Declaration</span></span>](../../programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="8d503-130">ReDim – příkaz</span><span class="sxs-lookup"><span data-stu-id="8d503-130">ReDim Statement</span></span>](../statements/redim-statement.md)
- [<span data-ttu-id="8d503-131">With...End With – příkaz</span><span class="sxs-lookup"><span data-stu-id="8d503-131">With...End With Statement</span></span>](../statements/with-end-with-statement.md)
