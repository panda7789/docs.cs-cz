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
# <a name="whats-new-in-f-47"></a>Co je nového v F# 4,7

F#4,7 přidává k F# jazyku více vylepšení.

## <a name="get-started"></a>Začínáme

F#4,7 je k dispozici ve všech distribucích .NET Core a nástrojích sady Visual Studio. Začněte [s F# ](../get-started/index.md) a získejte další informace.

## <a name="language-version"></a>Verze jazyka

Kompilátor F# 4,7 zavádí možnost nastavení efektivní jazykové verze prostřednictvím vlastnosti v souboru projektu:

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Můžete ji nastavit na hodnoty `4.6`, `4.7`, `latest`a `preview`. Výchozí hodnota je `latest`.

Pokud nastavíte `preview`, kompilátor bude aktivovat všechny F# funkce verze Preview, které jsou implementovány ve vašem kompilátoru.

## <a name="implicit-yields"></a>Implicitní výnosy

Již nemusíte používat klíčové slovo `yield` v polích, seznamech, sekvencích nebo výpočtových výrazech, kde lze typ odvodit. V následujícím příkladu oba výrazy vyžadovaly příkaz `yield` pro každou položku před F# 4,7:

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

Pokud zavedete jedno klíčové slovo `yield`, musí mít každá další položka také `yield` na ni použit.

Implicitní výnosy nejsou aktivovány při použití ve výrazu, který také používá `yield!` k tomu, aby něco vypadalo jako sloučení sekvence. V těchto případech musíte nadále používat `yield` dnes.

## <a name="wildcard-identifiers"></a>Identifikátory zástupných znaků

V F# kódu zahrnujícím třídy musí mít držitel v deklaracích členů vždycky explicitní identifikátor. V případech, kdy se držitel nikdy nepoužívá, se tradičně použila konvence k použití dvojitého podtržítka k označení vlastních identifikátorů Nameless. Teď můžete použít jedno podtržítko:

```fsharp
type C() =
    member _.M() = ()
```

To platí i pro `for` smyčky:

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a>Zvětšení odsazení

Před F# 4,7 se požadavky odsazení pro primární konstruktor a statické členské argumenty vyžadovaly nadměrné odsazení. Nyní vyžadují pouze jeden rozsah odsazení:

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
