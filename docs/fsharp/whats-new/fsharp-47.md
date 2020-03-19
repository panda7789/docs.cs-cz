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
# <a name="whats-new-in-f-47"></a>Co je nového ve F# 4.7

F# 4.7 přidává více vylepšení jazyka F#.

## <a name="get-started"></a>Začínáme

F# 4.7 je k dispozici ve všech distribucích .NET Core a nástrojích Visual Studio. [Můžete začít s F#](../get-started/index.md) a dozvíte se více.

## <a name="language-version"></a>Jazyková verze

Kompilátor F# 4.7 zavádí možnost nastavit efektivní jazykovou verzi prostřednictvím vlastnosti v souboru projektu:

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Můžete ji nastavit na `4.6` `4.7`hodnoty `latest`, `preview`, a . Výchozí formát je `latest`.

Pokud ji nastavíte na `preview`, kompilátor aktivuje všechny funkce Náhled Jazyka F#, které jsou implementovány v kompilátoru.

## <a name="implicit-yields"></a>Implicitní výnosy

Již není nutné použít `yield` klíčové slovo v polích, seznamech, sekvencích nebo výpočtových výrazech, kde lze odvodit typ. V následujícím příkladu oba výrazy vyžadovaly `yield` příkaz pro každou položku před F# 4.7:

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

Pokud zavedete `yield` jedno klíčové slovo, `yield` musí se na něj použít i každá další položka.

Implicitní výnosy nejsou aktivovány při použití `yield!` ve výrazu, který také používá k tomu něco jako vyrovnat posloupnost. V těchto případech `yield` musíte pokračovat v používání i dnes.

## <a name="wildcard-identifiers"></a>Identifikátory zástupných symbolů

V kódu F# zahrnující třídy, vlastní identifikátor musí být vždy explicitní v deklaracích členů. Ale v případech, kdy se vlastní identifikátor nikdy nepoužívá, tradičně byla konvence použít dvojité podtržítko k označení bezejmenných vlastních identifikátorů. Nyní můžete použít jedno podtržítko:

```fsharp
type C() =
    member _.M() = ()
```

To platí i `for` pro smyčky:

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a>Uvolnění odsazení

Před F# 4.7 požadavky na odsazení pro primární konstruktor a statické argumenty členů vyžaduje nadměrné odsazení. Nyní vyžadují pouze jeden obor odsazení:

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
