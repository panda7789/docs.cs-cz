---
title: "Objektová proměnná nebo proměnná bloku With nebyla nastavena."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e1f587e194acf744b6ec9b8f1bede3acef7b753
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="337ca-102">Objektová proměnná nebo proměnná bloku With nebyla nastavena.</span><span class="sxs-lookup"><span data-stu-id="337ca-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="337ca-103">Odkazuje na neplatný objekt proměnnou.</span><span class="sxs-lookup"><span data-stu-id="337ca-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="337ca-104">Této chybě může dojít z několika důvodů:</span><span class="sxs-lookup"><span data-stu-id="337ca-104">This error can occur for several reasons:</span></span>  
  
-   <span data-ttu-id="337ca-105">Proměnná byla deklarována bez zadání typu.</span><span class="sxs-lookup"><span data-stu-id="337ca-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="337ca-106">Pokud je proměnná deklarována bez zadání typu, výchozí hodnoty na typ `Object`.</span><span class="sxs-lookup"><span data-stu-id="337ca-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>  
  
     <span data-ttu-id="337ca-107">Například proměnná definovaná s `Dim x` by být typu `Object;` proměnné deklarovat s `Dim x As String` by být typu `String`.</span><span class="sxs-lookup"><span data-stu-id="337ca-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="337ca-108">`Option Strict` Příkaz zakáže implicitní zadáte, která způsobí, že `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="337ca-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="337ca-109">Pokud není typu, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="337ca-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="337ca-110">V tématu [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="337ca-110">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
-   <span data-ttu-id="337ca-111">Pokoušíte se odkazovat na objekt, který je nastavený na`Nothing`</span><span class="sxs-lookup"><span data-stu-id="337ca-111">You are attempting to reference an object that has been set to `Nothing`</span></span>  
  
     <span data-ttu-id="337ca-112">.</span><span class="sxs-lookup"><span data-stu-id="337ca-112">.</span></span>  
  
-   <span data-ttu-id="337ca-113">Chcete získat přístup k elementu proměnná typu pole, který nebyl deklarován správně.</span><span class="sxs-lookup"><span data-stu-id="337ca-113">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>  
  
     <span data-ttu-id="337ca-114">Například pole deklarované jako `products() As String` chyba se aktivuje, pokud se pokusíte odkazovat na prvek pole `products(3) = "Widget"`.</span><span class="sxs-lookup"><span data-stu-id="337ca-114">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="337ca-115">Toto pole je žádné elementy a je považován za objekt.</span><span class="sxs-lookup"><span data-stu-id="337ca-115">The array has no elements and is treated as an object.</span></span>  
  
-   <span data-ttu-id="337ca-116">Pokoušíte se přístupového kódu v rámci `With...End With` blokovat před inicializací bloku.</span><span class="sxs-lookup"><span data-stu-id="337ca-116">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="337ca-117">A `With...End With` bloku se musí inicializovat spuštěním `With` příkaz vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="337ca-117">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="337ca-118">V dřívějších verzích systému Visual Basic nebo VBA tato chyba byla aktivována také přiřazením hodnoty proměnné bez použití `Set` – klíčové slovo (`x = "name"` místo `Set x = "name"`).</span><span class="sxs-lookup"><span data-stu-id="337ca-118">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="337ca-119">`Set` – Klíčové slovo již není platný v jazyce Visual Basic .net.</span><span class="sxs-lookup"><span data-stu-id="337ca-119">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="337ca-120">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="337ca-120">To correct this error</span></span>  
  
1.  <span data-ttu-id="337ca-121">Nastavit `Option Strict` k `On` přidáním následující kód do začátku souboru:</span><span class="sxs-lookup"><span data-stu-id="337ca-121">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2.  <span data-ttu-id="337ca-122">Pokud chcete povolit `Option Strict`, vyhledávání kódu pro všechny proměnné, které bylo zadáno bez typu (`Dim x` místo `Dim x As String`) a přidejte typ určený k deklaraci.</span><span class="sxs-lookup"><span data-stu-id="337ca-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>  
  
3.  <span data-ttu-id="337ca-123">Zajistěte, aby nejsou odkazující na objektová proměnná, která byla nastavena na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="337ca-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="337ca-124">Hledání kódu pro klíčové slovo `Nothing`a zkontrolovat, jestli váš kód tak, aby objekt není nastavený na `Nothing` až poté, co jste odkazuje.</span><span class="sxs-lookup"><span data-stu-id="337ca-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>  
  
4.  <span data-ttu-id="337ca-125">Ujistěte se, že jsou všechny proměnné pole dimenzovány předtím, než k nim přístup.</span><span class="sxs-lookup"><span data-stu-id="337ca-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="337ca-126">Je možné přiřadit dimenzi při prvním vytváření pole (`Dim x(5) As String` místo `Dim x() As String`), nebo použijte `ReDim` – klíčové slovo nastavit rozměry pole před první přístup.</span><span class="sxs-lookup"><span data-stu-id="337ca-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>  
  
5.  <span data-ttu-id="337ca-127">Zajistěte, aby vaše `With` bloku je inicializovat spuštěním `With` příkaz vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="337ca-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="337ca-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="337ca-128">See Also</span></span>  
 [<span data-ttu-id="337ca-129">Deklarace proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="337ca-129">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="337ca-130">ReDim – příkaz</span><span class="sxs-lookup"><span data-stu-id="337ca-130">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="337ca-131">S... End With – příkaz</span><span class="sxs-lookup"><span data-stu-id="337ca-131">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
