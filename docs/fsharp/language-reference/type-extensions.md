---
title: Rozšíření typů (F#)
description: 'Zjistěte, jak povolit rozšíření typů F #, že přidáte nové členy typu dříve definovaném objektu.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 3399778799fbf0f8eee56e332135656150918a60
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="type-extensions"></a>Rozšíření typů

Typ rozšíření můžete přidat nové členy typu dříve definovaný objekt.

## <a name="syntax"></a>Syntaxe

```fsharp
// Intrinsic extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]

// Optional extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]
```

## <a name="remarks"></a>Poznámky
Existují dvě formy typ rozšíření, které mají mírně odlišné syntaxe a chování. *Vnitřní rozšíření* jako typ rozšiřovanou je rozšíření, které se zobrazí ve stejném oboru názvů nebo modul, ve stejném souboru zdroje a ve stejném sestavení (DLL nebo spustitelného souboru). *Volitelné rozšíření* je rozšíření, které se zobrazí mimo původní modulu, obor názvů nebo sestavení rozšiřovanou typu. Vnitřní rozšíření zobrazí na typ, pokud typ je zkontrolován pomocí reflexe, ale nechcete volitelná rozšíření. Volitelné rozšíření musí být v modulech a jsou pouze v oboru, když modul, který obsahuje rozšíření je otevřený.

V předchozích syntaxi *typename* představuje typ, který je právě rozšířeno. Je možné rozšířit žádný typ, který je přístupný, ale název typu musí být název skutečný typ zkratka typu. Můžete definovat více členů v jeden typ rozšíření. *Vlastní identifikátor* představuje instanci objektu volaná, stejně jako obyčejnou členy.

`end` – Klíčové slovo je v prostá syntaxe volitelné.

Stejně jako ostatní členové na typu třídy lze členy definovanou v rozšíření typu. Podobně jako ostatní členové mohou být statické nebo instance členy. Tyto metody se také označují jako *rozšiřující metody*; vlastnosti se označují jako *– vlastnosti rozšíření*a tak dále. Volitelné rozšíření členy zkompilovány pro statické členy, pro které se implicitně předá instanci objektu jako první parametr. Však budou fungovat, jako kdyby byly členy instancí nebo statické členy podle jak jsou deklarované. Implicitní rozšíření členové jsou zahrnuty mezi členy typu a dá se používat bez omezení.

Metody rozšíření nemůže být virtuální nebo abstraktní metody. Se může přetížit jiných metod se stejným názvem, ale dává přednost bez rozšiřující metody v případě nejednoznačné volání do kompilátoru.

Pokud pro jeden typ existuje několik rozšíření vnitřního typu, všichni členové musí být jedinečný. Pro typ volitelné rozšíření mohou mít členové v jiný typ rozšíření do stejného typu stejné názvy. Pouze v případě, že kód klienta otevře dva různé obory, které definují stejné názvy členů dojít k chybám nejednoznačnosti.

V následujícím příkladu má typ v modulu vnitřní typ rozšíření. Na kód klienta mimo modul typ rozšíření se zobrazí jako regulární člen typu ve všech ohledech.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3701.fs)]

Vnitřní typ rozšíření můžete použít k oddělení definici typu do oddílů. To může být užitečné při správě definice rozsáhlého typu, například si nechat generované kompilátorem kód a kód vytvořené v samostatné nebo seskupit kód vytvořené jiné osoby nebo ve spojení s jinou funkci.

V následujícím příkladu rozšiřuje volitelné typu rozšíření `System.Int32` typ pomocí metody rozšíření `FromString` statický člen, který volá `Parse`. `testFromString` Metoda ukazuje, že stejně jako libovolný člen instance se nazývá nového člena.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3702.fs)]

Nový člen instance se zobrazí jako jakékoliv jiné metody `Int32` typu v technologii IntelliSense, ale jenom v případě, že modul, který obsahuje rozšíření je otevřené nebo jinak v oboru.

## <a name="generic-extension-methods"></a>Obecný rozšiřující metody
Před F # 3.1, kompilátor jazyka F # nepodporovala použití jazyka C# – styl rozšiřující metody s proměnné obecného typu, typ pole, řazené kolekce členů nebo typu funkce F # jako parametr "Tento". F # 3.1 podporuje použití těchto rozšíření členů.

Například v F # 3.1 kódu, můžete použít metody rozšíření s podpisy, které se podobají syntaxi v jazyce C#:

```csharp
static member Method<T>(this T input, T other)
```

Tento postup je zvlášť užitečné, když je omezené parametr obecného typu. Navíc můžete teď deklarovat rozšíření členy takto v F # – kód a definovat další, sémanticky bohatou sadu rozšiřující metody. V jazyce F # obvykle definovat rozšíření členy jako následující příklad ukazuje:

```fsharp
open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq { for x in xs do for i in 1 .. n do yield x }
```

Ale pro obecný typ, nemusí být omezené proměnná typu. Nyní můžete deklarovat C# – styl rozšíření člena v F # na toto omezení obejít. Když zkombinujete tento druh deklarace s vložených funkcí jazyka F #, může být obecné algoritmy jako rozšíření členy.

Vezměte v úvahu následující prohlášení:

```fsharp
[<Extension>]
type ExtraCSharpStyleExtensionMethodsInFSharp () =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

Pomocí tohoto prohlášení, můžete napsat kód, který se podobá následující ukázka.

```fsharp
let listOfIntegers = [ 1 .. 100 ]
let listOfBigIntegers = [ 1I to 100I ]
let sum1 = listOfIntegers.Sum()
let sum2 = listOfBigIntegers.Sum()
```

V tomto kódu má stejný kód obecné aritmetické použije dva typy seznamů bez přetížení definováním členem jedné rozšíření.


## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

[Členové](members/index.md)
