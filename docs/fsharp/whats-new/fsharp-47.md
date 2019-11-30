---
title: Co je nového v F# 4,7 – F# příručka
description: Získejte přehled o nových funkcích dostupných v F# 4,7.
ms.date: 11/27/2019
ms.openlocfilehash: 203b258466cb9f1f50215ecf8884e92e7e86416b
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644066"
---
# <a name="whats-new-in-f-47"></a><span data-ttu-id="5404a-103">Co je nového v F# 4,7</span><span class="sxs-lookup"><span data-stu-id="5404a-103">What's new in F# 4.7</span></span>

<span data-ttu-id="5404a-104">F#4,7 přidává k F# jazyku více vylepšení.</span><span class="sxs-lookup"><span data-stu-id="5404a-104">F# 4.7 adds multiple improvements to the F# language.</span></span>

## <a name="get-started"></a><span data-ttu-id="5404a-105">Začínáme</span><span class="sxs-lookup"><span data-stu-id="5404a-105">Get started</span></span>

<span data-ttu-id="5404a-106">F#4,7 je k dispozici ve všech distribucích .NET Core a nástrojích sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5404a-106">F# 4.7 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="5404a-107">Začněte [s F# ](../get-started/index.md) a získejte další informace.</span><span class="sxs-lookup"><span data-stu-id="5404a-107">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="language-version"></a><span data-ttu-id="5404a-108">Verze jazyka</span><span class="sxs-lookup"><span data-stu-id="5404a-108">Language version</span></span>

<span data-ttu-id="5404a-109">Kompilátor F# 4,7 zavádí možnost nastavení efektivní jazykové verze prostřednictvím vlastnosti v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="5404a-109">The F# 4.7 compiler introduces the ability to set your effective language version via a property in your project file:</span></span>

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="5404a-110">Můžete ji nastavit na hodnoty `4.6`, `4.7`, `latest`a `preview`.</span><span class="sxs-lookup"><span data-stu-id="5404a-110">You can set it to the values `4.6`, `4.7`, `latest`, and `preview`.</span></span> <span data-ttu-id="5404a-111">Výchozí hodnota je `latest`.</span><span class="sxs-lookup"><span data-stu-id="5404a-111">The default is `latest`.</span></span>

<span data-ttu-id="5404a-112">Pokud nastavíte `preview`, kompilátor bude aktivovat všechny F# funkce verze Preview, které jsou implementovány ve vašem kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="5404a-112">If you set it to `preview`, your compiler will activate all F# preview features that are implemented in your compiler.</span></span>

## <a name="implicit-yields"></a><span data-ttu-id="5404a-113">Implicitní výnosy</span><span class="sxs-lookup"><span data-stu-id="5404a-113">Implicit yields</span></span>

<span data-ttu-id="5404a-114">Již nemusíte používat klíčové slovo `yield` v polích, seznamech, sekvencích nebo výpočtových výrazech, kde lze typ odvodit.</span><span class="sxs-lookup"><span data-stu-id="5404a-114">You no longer need to apply the `yield` keyword in arrays, lists, sequences, or computation expressions where the type can be inferred.</span></span> <span data-ttu-id="5404a-115">V následujícím příkladu oba výrazy vyžadovaly příkaz `yield` pro každou položku před F# 4,7:</span><span class="sxs-lookup"><span data-stu-id="5404a-115">In the following example, both expressions required the `yield` statement for each entry prior to F# 4.7:</span></span>

```fsharp
let s = seq { 1; 2; 3; 4; 5 }

let daysOfWeek includeWeekend =
    [ 
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then 
            "Saturday"
            "Sunday"
    ] 
```

<span data-ttu-id="5404a-116">Pokud zavedete jedno klíčové slovo `yield`, musí mít každá další položka také `yield` na ni použit.</span><span class="sxs-lookup"><span data-stu-id="5404a-116">If you introduce a single `yield` keyword, every other item must also have `yield` applied to it.</span></span>

<span data-ttu-id="5404a-117">Implicitní výnosy nejsou aktivovány při použití ve výrazu, který také používá `yield!` k tomu, aby něco vypadalo jako sloučení sekvence.</span><span class="sxs-lookup"><span data-stu-id="5404a-117">Implicit yields are not activated when used in an expression that also uses `yield!` to do something like flatten a sequence.</span></span> <span data-ttu-id="5404a-118">V těchto případech musíte nadále používat `yield` dnes.</span><span class="sxs-lookup"><span data-stu-id="5404a-118">You must continue to use `yield` today in these cases.</span></span>

## <a name="wildcard-identifiers"></a><span data-ttu-id="5404a-119">Identifikátory zástupných znaků</span><span class="sxs-lookup"><span data-stu-id="5404a-119">Wildcard identifiers</span></span>

<span data-ttu-id="5404a-120">V F# kódu zahrnujícím třídy musí mít držitel v deklaracích členů vždycky explicitní identifikátor.</span><span class="sxs-lookup"><span data-stu-id="5404a-120">In F# code involving classes, the self-identifier needs to always be explicit in member declarations.</span></span> <span data-ttu-id="5404a-121">V případech, kdy se držitel nikdy nepoužívá, se tradičně použila konvence k použití dvojitého podtržítka k označení vlastních identifikátorů Nameless.</span><span class="sxs-lookup"><span data-stu-id="5404a-121">But in cases where the self-identifier is never used, it has traditionally been convention to use a double-underscore to indicate a nameless self-identifiers.</span></span> <span data-ttu-id="5404a-122">Teď můžete použít jedno podtržítko:</span><span class="sxs-lookup"><span data-stu-id="5404a-122">You can now use a single underscore:</span></span>

```fsharp
type C() =
    member _.M() = ()
```

<span data-ttu-id="5404a-123">To platí i pro `for` smyčky:</span><span class="sxs-lookup"><span data-stu-id="5404a-123">This also applies for `for` loops:</span></span>

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a><span data-ttu-id="5404a-124">Zvětšení odsazení</span><span class="sxs-lookup"><span data-stu-id="5404a-124">Indentation relaxations</span></span>

<span data-ttu-id="5404a-125">Před F# 4,7 se požadavky odsazení pro primární konstruktor a statické členské argumenty vyžadovaly nadměrné odsazení.</span><span class="sxs-lookup"><span data-stu-id="5404a-125">Prior to F# 4.7, the indentation requirements for primary constructor and static member arguments required excessive indentation.</span></span> <span data-ttu-id="5404a-126">Nyní vyžadují pouze jeden rozsah odsazení:</span><span class="sxs-lookup"><span data-stu-id="5404a-126">They now only require a single indentation scope:</span></span>

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
