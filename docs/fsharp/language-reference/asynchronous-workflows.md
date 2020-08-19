---
title: Asynchronní pracovní postupy
description: 'Přečtěte si o podpoře v programovacím jazyce F # pro asynchronní provádění výpočtů, které se spouštějí bez blokování provádění jiné práce.'
ms.date: 08/15/2020
ms.openlocfilehash: ac727fc630f13db01da964131ab39dc242a12cd1
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557708"
---
# <a name="asynchronous-workflows"></a>Asynchronní pracovní postupy

Tento článek popisuje podporu v F # pro asynchronní provádění výpočtů, tedy bez blokování provádění jiné práce. Asynchronní výpočty lze například použít k psaní aplikací, které mají uživatelská rozhraní, které nadále reagují na uživatele, když aplikace provádí jinou práci.

## <a name="syntax"></a>Syntax

```fsharp
async { expression }
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi je výpočet reprezentovaný jako `expression` nastavený na asynchronní spouštění, to znamená, že bez blokování aktuálního výpočetního vlákna, když se provádí asynchronní operace spánku, vstup/výstup a další asynchronní operace. Asynchronní výpočty jsou často spouštěny na vlákně na pozadí, zatímco provádění pokračuje v aktuálním vlákně. Typ výrazu je `Async<'T>` , kde `'T` je typ vrácený výrazem při `return` použití klíčového slova. Kód v takovém výrazu je označován jako *asynchronní blok*nebo *asynchronní blok*.

Existuje celá řada způsobů programování asynchronně a [`Async`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html) Třída poskytuje metody, které podporují několik scénářů. Obecným přístupem je vytvořit `Async` objekty, které reprezentují výpočty nebo výpočty, které chcete spouštět asynchronně, a potom tyto výpočty spustit pomocí jedné ze spouštěcích funkcí. Různé funkce triggeru poskytují různé způsoby spouštění asynchronních výpočtů a to, které použití závisí na tom, zda chcete použít aktuální vlákno, vlákno na pozadí nebo objekt .NET Framework úlohy a zda existují funkce pro pokračování, které by měly být spuštěny po dokončení výpočtu. Například pro spuštění asynchronního výpočtu v aktuálním vlákně můžete použít [`Async.StartImmediate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#StartImmediate) . Když spustíte asynchronní výpočet z vlákna uživatelského rozhraní, nezablokujete hlavní smyčku událostí, která zpracovává uživatelské akce, jako jsou stisknutí kláves a aktivita myši, takže vaše aplikace zůstane v chodu.

## <a name="asynchronous-binding-by-using-let"></a>Asynchronní vazby pomocí let!

V asynchronním pracovním postupu jsou některé výrazy a operace synchronní a některé jsou delší výpočetní prostředky, které jsou navržené tak, aby vrátily výsledek asynchronně. Při asynchronním volání metody namísto běžné `let` vazby použijete `let!` . Výsledkem je, že se má `let!` Povolit provádění pokračování na dalších výpočtech nebo vláknech během provádění výpočtu. Po pravé straně se `let!` vazba vrátí zbytek asynchronního pracovního postupu, který pokračuje v provádění.

Následující kód ukazuje rozdíl mezi `let` a `let!` . Řádek kódu, který používá `let` pouze, vytvoří asynchronní výpočet jako objekt, který lze spustit později pomocí, například `Async.StartImmediate` nebo [`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) . Řádek kódu, který používá `let!` nástroj, spustí výpočet a poté je vlákno pozastaveno, dokud nebude výsledek k dispozici, v němž bude provádění pokračovat.

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

Kromě `let!` toho můžete použít `use!` k provádění asynchronních vazeb. Rozdíl mezi `let!` a `use!` je stejný jako rozdíl mezi `let` a `use` . V případě `use!` je objekt odstraněn v blízkosti aktuálního oboru. Všimněte si, že v aktuální verzi jazyka F # `use!` neumožňuje inicializaci hodnoty na hodnotu null, i když to `use` dělá.

## <a name="asynchronous-primitives"></a>Asynchronní primitivní prvky

Metoda, která provádí jednu asynchronní úlohu a vrací výsledek, se nazývá *asynchronní primitiva*a je navržena speciálně pro použití s `let!` . Několik asynchronních primitivních elementů je definováno v základní knihovně jazyka F #. V modulu jsou definovány dvě takové metody pro webové aplikace [`FSharp.Control.WebExtensions`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html) : [`WebRequest.AsyncGetResponse`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html#AsyncGetResponse) a [`WebClient.AsyncDownloadString`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html#AsyncDownloadString) . Obě primitiva stahují data z webové stránky s ohledem na adresu URL. `AsyncGetResponse` vytvoří `System.Net.WebResponse` objekt a `AsyncDownloadString` vytvoří řetězec, který představuje kód HTML webové stránky.

Modul obsahuje několik primitiv pro asynchronní vstupně-výstupní operace [`FSharp.Control.CommonExtensions`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-commonextensions.html) . Tyto rozšiřující metody `System.IO.Stream` třídy jsou [`Stream.AsyncRead`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-commonextensions.html#AsyncRead) a [`Stream.AsyncWrite`](hhttps://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-commonextensions.html#AsyncWrite) .

Můžete také napsat vlastní asynchronní primitivy definováním funkce, jejíž kompletní tělo je uzavřeno v asynchronním bloku.

Chcete-li použít asynchronní metody v .NET Framework, které jsou navrženy pro jiné asynchronní modely pomocí asynchronního programovacího modelu F #, vytvořte funkci, která vrátí objekt jazyka F # `Async` . Knihovna jazyka F # obsahuje funkce, které usnadňují provádění.

Zde je uveden jeden příklad použití asynchronních pracovních postupů. k dispozici je mnoho dalších v dokumentaci pro metody [asynchronní třídy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html).

Tento příklad ukazuje, jak použít asynchronní pracovní postupy k paralelnímu provádění výpočtů.

V následujícím příkladu kódu funkce `fetchAsync` získá text HTML vrácený z webové žádosti. `fetchAsync`Funkce obsahuje asynchronní blok kódu. Pokud je vytvořena vazba na výsledek asynchronního primitiva, v tomto případě [`AsyncDownloadString`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html#AsyncDownloadString) `let!` je použita místo `let` .

Funkci použijete [`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) ke spuštění asynchronní operace a čekání na její výsledek. Jako příklad můžete spustit více asynchronních operací paralelně pomocí [`Async.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#Parallel) funkce společně s `Async.RunSynchronously` funkcí. `Async.Parallel`Funkce přebírá seznam `Async` objektů, nastavuje kód pro každý `Async` objekt úlohy, který se má spustit paralelně, a vrátí `Async` objekt, který představuje paralelní výpočet. Stejně jako u jediné operace zavoláte `Async.RunSynchronously` k zahájení provádění.

`runAll`Funkce spustí paralelní tři asynchronní pracovní postupy a počká, dokud všechny nedokončí.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](index.md)
- [Výpočetní výrazy](computation-expressions.md)
- [Control. Async – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)
