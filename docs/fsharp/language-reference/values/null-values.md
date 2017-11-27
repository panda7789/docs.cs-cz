---
title: Hodnoty Null (F#)
description: "Zjistěte, jak se používá hodnota null v programovací jazyk F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 68ebd261-51cf-4582-b2dc-44c84d1c2500
ms.openlocfilehash: 01c14de00eb5efd0952145ffc8aabe69d65a3a48
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="null-values"></a><span data-ttu-id="a1452-104">Hodnoty Null</span><span class="sxs-lookup"><span data-stu-id="a1452-104">Null Values</span></span>

<span data-ttu-id="a1452-105">Toto téma popisuje, jak se používá hodnota null v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="a1452-105">This topic describes how the null value is used in F#.</span></span>


## <a name="null-value"></a><span data-ttu-id="a1452-106">Hodnoty Null</span><span class="sxs-lookup"><span data-stu-id="a1452-106">Null Value</span></span>
<span data-ttu-id="a1452-107">Hodnota null není obvykle používá v F # pro hodnoty nebo proměnné.</span><span class="sxs-lookup"><span data-stu-id="a1452-107">The null value is not normally used in F# for values or variables.</span></span> <span data-ttu-id="a1452-108">Hodnota null se však zobrazí jako neobvyklé hodnota v určitých situacích.</span><span class="sxs-lookup"><span data-stu-id="a1452-108">However, null appears as an abnormal value in certain situations.</span></span> <span data-ttu-id="a1452-109">Pokud typ je definovaná v F #, null není povolená jako regulární hodnotu, pokud [allownullliteral –](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) atribut se používá k typu.</span><span class="sxs-lookup"><span data-stu-id="a1452-109">If a type is defined in F#, null is not permitted as a regular value unless the [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) attribute is applied to the type.</span></span> <span data-ttu-id="a1452-110">Pokud typ je definovaná v jiném jazyce rozhraní .NET, null je možná hodnota a když jsou spolupracuje s takového typu, F # kódu setkat hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="a1452-110">If a type is defined in some other .NET language, null is a possible value, and when you are interoperating with such types, your F# code might encounter null values.</span></span>

<span data-ttu-id="a1452-111">Pro typ definovaný v jazyce F # a používají výhradně z F #, je jediným způsobem, jak vytvořit hodnotu null, přímo pomocí knihovny F # použití [unchecked.defaultof –](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) nebo [Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2).</span><span class="sxs-lookup"><span data-stu-id="a1452-111">For a type defined in F# and used strictly from F#, the only way to create a null value using the F# library directly is to use [Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) or [Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2).</span></span> <span data-ttu-id="a1452-112">Ale pro typ F #, který se používá z jinými jazyky rozhraní .NET, nebo pokud používáte tento typ pomocí rozhraní API, které není napsané v jazyce F #, jako je rozhraní .NET Framework, může dojít, hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="a1452-112">However, for an F# type that is used from other .NET languages, or if you are using that type with an API that is not written in F#, such as the .NET Framework, null values can occur.</span></span>

<span data-ttu-id="a1452-113">Můžete použít `option` typu v F # kdy můžete použít odkaz na proměnnou s hodnotou null možné v jiném jazyce .NET.</span><span class="sxs-lookup"><span data-stu-id="a1452-113">You can use the `option` type in F# when you might use a reference variable with a possible null value in another .NET language.</span></span> <span data-ttu-id="a1452-114">Místo null, se F # `option` typu, použijte možnost hodnotu `None` Pokud neexistuje žádný objekt.</span><span class="sxs-lookup"><span data-stu-id="a1452-114">Instead of null, with an F# `option` type, you use the option value `None` if there is no object.</span></span> <span data-ttu-id="a1452-115">Použijte možnost hodnotu `Some(obj)` s objektem `obj` po objekt.</span><span class="sxs-lookup"><span data-stu-id="a1452-115">You use the option value `Some(obj)` with an object `obj` when there is an object.</span></span> <span data-ttu-id="a1452-116">Další informace najdete v tématu [možnosti](../options.md).</span><span class="sxs-lookup"><span data-stu-id="a1452-116">For more information, see [Options](../options.md).</span></span>

<span data-ttu-id="a1452-117">`null` – Klíčové slovo je platný – klíčové slovo v jazyce F # a budete muset používat v případě, že pracujete s rozhraní API technologie .NET Framework nebo jiná rozhraní API, které jsou napsané v jiném jazyce .NET.</span><span class="sxs-lookup"><span data-stu-id="a1452-117">The `null` keyword is a valid keyword in the F# language, and you have to use it when you are working with .NET Framework APIs or other APIs that are written in another .NET language.</span></span> <span data-ttu-id="a1452-118">Dvě situace, ve kterých může být nutné hodnotu null jsou při volání rozhraní API .NET a předejte hodnotu null jako argument, a při interpretovat návratovou hodnotu nebo výstupní parametr z volání metody rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="a1452-118">The two situations in which you might need a null value are when you call a .NET API and pass a null value as an argument, and when you interpret the return value or an output parameter from a .NET method call.</span></span>

<span data-ttu-id="a1452-119">Chcete metoda .NET předat hodnotu null, použijte `null` – klíčové slovo v kódu volání.</span><span class="sxs-lookup"><span data-stu-id="a1452-119">To pass a null value to a .NET method, just use the `null` keyword in the calling code.</span></span> <span data-ttu-id="a1452-120">Následující příklad kódu to dokládá.</span><span class="sxs-lookup"><span data-stu-id="a1452-120">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

<span data-ttu-id="a1452-121">Interpretace hodnotu null, který byl získán z metody rozhraní .NET, použijte porovnávání vzorů, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="a1452-121">To interpret a null value that is obtained from a .NET method, use pattern matching if you can.</span></span> <span data-ttu-id="a1452-122">Následující příklad kódu ukazuje, jak použít porovnávání vzorů interpretovat hodnotu null, která je vrácena z `ReadLine` při pokusu o čtení za koncem vstupního datového proudu.</span><span class="sxs-lookup"><span data-stu-id="a1452-122">The following code example shows how to use pattern matching to interpret the null value that is returned from `ReadLine` when it tries to read past the end of an input stream.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

<span data-ttu-id="a1452-123">Hodnoty Null pro typy F # lze generovat také jinými způsoby, například při použití `Array.zeroCreate`, který volá `Unchecked.defaultof`.</span><span class="sxs-lookup"><span data-stu-id="a1452-123">Null values for F# types can also be generated in other ways, such as when you use `Array.zeroCreate`, which calls `Unchecked.defaultof`.</span></span> <span data-ttu-id="a1452-124">Musíte být opatrní s takový kód, aby zapouzdřené hodnotami null.</span><span class="sxs-lookup"><span data-stu-id="a1452-124">You must be careful with such code to keep the null values encapsulated.</span></span> <span data-ttu-id="a1452-125">V knihovně určena pouze pro F # nemáte zkontrolujte hodnoty null v každé funkci.</span><span class="sxs-lookup"><span data-stu-id="a1452-125">In a library intended only for F#, you do not have to check for null values in every function.</span></span> <span data-ttu-id="a1452-126">Pokud píšete knihovna pro spolupráci s jinými jazyky rozhraní .NET, možná budete muset přidat kontroluje null vstupní parametry a výjimku `ArgumentNullException`, stejně jako v kódu jazyka C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a1452-126">If you are writing a library for interoperation with other .NET languages, you might have to add checks for null input parameters and throw an `ArgumentNullException`, just as you do in C# or Visual Basic code.</span></span>

<span data-ttu-id="a1452-127">Následující kód slouží ke kontrole, pokud je libovolná hodnota je null.</span><span class="sxs-lookup"><span data-stu-id="a1452-127">You can use the following code to check if an arbitrary value is null.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a><span data-ttu-id="a1452-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1452-128">See Also</span></span>
[<span data-ttu-id="a1452-129">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="a1452-129">Values</span></span>](index.md)

[<span data-ttu-id="a1452-130">Výrazy shody</span><span class="sxs-lookup"><span data-stu-id="a1452-130">Match Expressions</span></span>](../match-expressions.md)
