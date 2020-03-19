---
title: Co je nového ve F# 4.7 - F# Guide
description: Získejte přehled o nových funkcích dostupných v f# 4.7.
ms.date: 11/27/2019
ms.openlocfilehash: 7a6e744a398719bcb55d168dd700459e0b122dd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185874"
---
# <a name="whats-new-in-f-47"></a><span data-ttu-id="806cc-103">Co je nového ve F# 4.7</span><span class="sxs-lookup"><span data-stu-id="806cc-103">What's new in F# 4.7</span></span>

<span data-ttu-id="806cc-104">F# 4.7 přidává více vylepšení jazyka F#.</span><span class="sxs-lookup"><span data-stu-id="806cc-104">F# 4.7 adds multiple improvements to the F# language.</span></span>

## <a name="get-started"></a><span data-ttu-id="806cc-105">Začínáme</span><span class="sxs-lookup"><span data-stu-id="806cc-105">Get started</span></span>

<span data-ttu-id="806cc-106">F# 4.7 je k dispozici ve všech distribucích .NET Core a nástrojích Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="806cc-106">F# 4.7 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="806cc-107">[Můžete začít s F#](../get-started/index.md) a dozvíte se více.</span><span class="sxs-lookup"><span data-stu-id="806cc-107">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="language-version"></a><span data-ttu-id="806cc-108">Jazyková verze</span><span class="sxs-lookup"><span data-stu-id="806cc-108">Language version</span></span>

<span data-ttu-id="806cc-109">Kompilátor F# 4.7 zavádí možnost nastavit efektivní jazykovou verzi prostřednictvím vlastnosti v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="806cc-109">The F# 4.7 compiler introduces the ability to set your effective language version via a property in your project file:</span></span>

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="806cc-110">Můžete ji nastavit na `4.6` `4.7`hodnoty `latest`, `preview`, a .</span><span class="sxs-lookup"><span data-stu-id="806cc-110">You can set it to the values `4.6`, `4.7`, `latest`, and `preview`.</span></span> <span data-ttu-id="806cc-111">Výchozí formát je `latest`.</span><span class="sxs-lookup"><span data-stu-id="806cc-111">The default is `latest`.</span></span>

<span data-ttu-id="806cc-112">Pokud ji nastavíte na `preview`, kompilátor aktivuje všechny funkce Náhled Jazyka F#, které jsou implementovány v kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="806cc-112">If you set it to `preview`, your compiler will activate all F# preview features that are implemented in your compiler.</span></span>

## <a name="implicit-yields"></a><span data-ttu-id="806cc-113">Implicitní výnosy</span><span class="sxs-lookup"><span data-stu-id="806cc-113">Implicit yields</span></span>

<span data-ttu-id="806cc-114">Již není nutné použít `yield` klíčové slovo v polích, seznamech, sekvencích nebo výpočtových výrazech, kde lze odvodit typ.</span><span class="sxs-lookup"><span data-stu-id="806cc-114">You no longer need to apply the `yield` keyword in arrays, lists, sequences, or computation expressions where the type can be inferred.</span></span> <span data-ttu-id="806cc-115">V následujícím příkladu oba výrazy vyžadovaly `yield` příkaz pro každou položku před F# 4.7:</span><span class="sxs-lookup"><span data-stu-id="806cc-115">In the following example, both expressions required the `yield` statement for each entry prior to F# 4.7:</span></span>

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

<span data-ttu-id="806cc-116">Pokud zavedete `yield` jedno klíčové slovo, `yield` musí se na něj použít i každá další položka.</span><span class="sxs-lookup"><span data-stu-id="806cc-116">If you introduce a single `yield` keyword, every other item must also have `yield` applied to it.</span></span>

<span data-ttu-id="806cc-117">Implicitní výnosy nejsou aktivovány při použití `yield!` ve výrazu, který také používá k tomu něco jako vyrovnat posloupnost.</span><span class="sxs-lookup"><span data-stu-id="806cc-117">Implicit yields are not activated when used in an expression that also uses `yield!` to do something like flatten a sequence.</span></span> <span data-ttu-id="806cc-118">V těchto případech `yield` musíte pokračovat v používání i dnes.</span><span class="sxs-lookup"><span data-stu-id="806cc-118">You must continue to use `yield` today in these cases.</span></span>

## <a name="wildcard-identifiers"></a><span data-ttu-id="806cc-119">Identifikátory zástupných symbolů</span><span class="sxs-lookup"><span data-stu-id="806cc-119">Wildcard identifiers</span></span>

<span data-ttu-id="806cc-120">V kódu F# zahrnující třídy, vlastní identifikátor musí být vždy explicitní v deklaracích členů.</span><span class="sxs-lookup"><span data-stu-id="806cc-120">In F# code involving classes, the self-identifier needs to always be explicit in member declarations.</span></span> <span data-ttu-id="806cc-121">Ale v případech, kdy se vlastní identifikátor nikdy nepoužívá, tradičně byla konvence použít dvojité podtržítko k označení bezejmenných vlastních identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="806cc-121">But in cases where the self-identifier is never used, it has traditionally been convention to use a double-underscore to indicate a nameless self-identifiers.</span></span> <span data-ttu-id="806cc-122">Nyní můžete použít jedno podtržítko:</span><span class="sxs-lookup"><span data-stu-id="806cc-122">You can now use a single underscore:</span></span>

```fsharp
type C() =
    member _.M() = ()
```

<span data-ttu-id="806cc-123">To platí i `for` pro smyčky:</span><span class="sxs-lookup"><span data-stu-id="806cc-123">This also applies for `for` loops:</span></span>

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a><span data-ttu-id="806cc-124">Uvolnění odsazení</span><span class="sxs-lookup"><span data-stu-id="806cc-124">Indentation relaxations</span></span>

<span data-ttu-id="806cc-125">Před F# 4.7 požadavky na odsazení pro primární konstruktor a statické argumenty členů vyžaduje nadměrné odsazení.</span><span class="sxs-lookup"><span data-stu-id="806cc-125">Prior to F# 4.7, the indentation requirements for primary constructor and static member arguments required excessive indentation.</span></span> <span data-ttu-id="806cc-126">Nyní vyžadují pouze jeden obor odsazení:</span><span class="sxs-lookup"><span data-stu-id="806cc-126">They now only require a single indentation scope:</span></span>

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
