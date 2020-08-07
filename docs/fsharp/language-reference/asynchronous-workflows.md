---
title: Asynchronní pracovní postupy
description: 'Přečtěte si o podpoře v programovacím jazyce F # pro asynchronní provádění výpočtů, které se spouštějí bez blokování provádění jiné práce.'
ms.date: 05/16/2016
ms.openlocfilehash: 3bc24639b329401a8f944488e974f0739d4680df
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855462"
---
# <a name="asynchronous-workflows"></a>Asynchronní pracovní postupy

Tento článek popisuje podporu v F # pro asynchronní provádění výpočtů, tedy bez blokování provádění jiné práce. Asynchronní výpočty lze například použít k psaní aplikací, které mají uživatelská rozhraní, které nadále reagují na uživatele, když aplikace provádí jinou práci.

> [!NOTE]
> Reference k rozhraní docs.microsoft.com API pro F # není dokončená. Pokud narazíte na nefunkční odkazy, místo toho použijte [dokumentaci základní knihovny F #](https://fsharp.github.io/fsharp-core-docs/) .

## <a name="syntax"></a>Syntax

```fsharp
async { expression }
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi je výpočet reprezentovaný jako `expression` nastavený na asynchronní spouštění, to znamená, že bez blokování aktuálního výpočetního vlákna, když se provádí asynchronní operace spánku, vstup/výstup a další asynchronní operace. Asynchronní výpočty jsou často spouštěny na vlákně na pozadí, zatímco provádění pokračuje v aktuálním vlákně. Typ výrazu je `Async<'T>` , kde `'T` je typ vrácený výrazem při `return` použití klíčového slova. Kód v takovém výrazu je označován jako *asynchronní blok*nebo *asynchronní blok*.

Existuje celá řada způsobů programování asynchronně a [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7) Třída poskytuje metody, které podporují několik scénářů. Obecným přístupem je vytvořit `Async` objekty, které reprezentují výpočty nebo výpočty, které chcete spouštět asynchronně, a potom tyto výpočty spustit pomocí jedné ze spouštěcích funkcí. Různé funkce triggeru poskytují různé způsoby spouštění asynchronních výpočtů a to, které použití závisí na tom, zda chcete použít aktuální vlákno, vlákno na pozadí nebo objekt .NET Framework úlohy a zda existují funkce pro pokračování, které by měly být spuštěny po dokončení výpočtu. Například pro spuštění asynchronního výpočtu v aktuálním vlákně můžete použít [`Async.StartImmediate`](https://msdn.microsoft.com/library/2f71d1cc-187f-48cf-ac66-e7fda41c46e3) . Když spustíte asynchronní výpočet z vlákna uživatelského rozhraní, nezablokujete hlavní smyčku událostí, která zpracovává uživatelské akce, jako jsou stisknutí kláves a aktivita myši, takže vaše aplikace zůstane v chodu.

## <a name="asynchronous-binding-by-using-let"></a>Asynchronní vazby pomocí let!

V asynchronním pracovním postupu jsou některé výrazy a operace synchronní a některé jsou delší výpočetní prostředky, které jsou navržené tak, aby vrátily výsledek asynchronně. Při asynchronním volání metody namísto běžné `let` vazby použijete `let!` . Výsledkem je, že se má `let!` Povolit provádění pokračování na dalších výpočtech nebo vláknech během provádění výpočtu. Po pravé straně se `let!` vazba vrátí zbytek asynchronního pracovního postupu, který pokračuje v provádění.

Následující kód ukazuje rozdíl mezi `let` a `let!` . Řádek kódu, který používá `let` pouze, vytvoří asynchronní výpočet jako objekt, který lze spustit později pomocí, například `Async.StartImmediate` nebo [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) . Řádek kódu, který používá `let!` nástroj, spustí výpočet a poté je vlákno pozastaveno, dokud nebude výsledek k dispozici, v němž bude provádění pokračovat.

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

Kromě `let!` toho můžete použít `use!` k provádění asynchronních vazeb. Rozdíl mezi `let!` a `use!` je stejný jako rozdíl mezi `let` a `use` . V případě `use!` je objekt odstraněn v blízkosti aktuálního oboru. Všimněte si, že v aktuální verzi jazyka F # `use!` neumožňuje inicializaci hodnoty na hodnotu null, i když to `use` dělá.

## <a name="asynchronous-primitives"></a>Asynchronní primitivní prvky

Metoda, která provádí jednu asynchronní úlohu a vrací výsledek, se nazývá *asynchronní primitiva*a je navržena speciálně pro použití s `let!` . Několik asynchronních primitivních elementů je definováno v základní knihovně jazyka F #. V modulu jsou definovány dvě takové metody pro webové aplikace [`Microsoft.FSharp.Control.WebExtensions`](https://msdn.microsoft.com/library/95ef17bc-ee3f-44ba-8a11-c90fcf4cf003) : [`WebRequest.AsyncGetResponse`](https://msdn.microsoft.com/library/09a60c31-e6e2-4b5c-ad23-92a86e50060c) a [`WebClient.AsyncDownloadString`](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a) . Obě primitiva stahují data z webové stránky s ohledem na adresu URL. `AsyncGetResponse`vytvoří `System.Net.WebResponse` objekt a `AsyncDownloadString` vytvoří řetězec, který představuje kód HTML webové stránky.

Modul obsahuje několik primitiv pro asynchronní vstupně-výstupní operace [`Microsoft.FSharp.Control.CommonExtensions`](https://msdn.microsoft.com/library/2edb67cb-6814-4a30-849f-b6dbdd042396) . Tyto rozšiřující metody `System.IO.Stream` třídy jsou [`Stream.AsyncRead`](https://msdn.microsoft.com/library/85698aaa-bdda-47e6-abed-3730f59fda5e) a [`Stream.AsyncWrite`](https://msdn.microsoft.com/library/1b0a2751-e42a-47e1-bd27-020224adc618) .

Můžete také napsat vlastní asynchronní primitivy definováním funkce, jejíž kompletní tělo je uzavřeno v asynchronním bloku.

Chcete-li použít asynchronní metody v .NET Framework, které jsou navrženy pro jiné asynchronní modely pomocí asynchronního programovacího modelu F #, vytvořte funkci, která vrátí objekt jazyka F # `Async` . Knihovna jazyka F # obsahuje funkce, které usnadňují provádění.

Zde je uveden jeden příklad použití asynchronních pracovních postupů. k dispozici je mnoho dalších v dokumentaci pro metody [asynchronní třídy](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).

Tento příklad ukazuje, jak použít asynchronní pracovní postupy k paralelnímu provádění výpočtů.

V následujícím příkladu kódu funkce `fetchAsync` získá text HTML vrácený z webové žádosti. `fetchAsync`Funkce obsahuje asynchronní blok kódu. Pokud je vazba provedena na výsledek asynchronního primitiva, v tomto případě [`AsyncDownloadString`](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a) let! se místo let používá.

Funkci použijete [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) ke spuštění asynchronní operace a čekání na její výsledek. Jako příklad můžete spustit více asynchronních operací paralelně pomocí [`Async.Parallel`](https://msdn.microsoft.com/library/aa9b0355-2d55-4858-b943-cbe428de9dc4) funkce společně s `Async.RunSynchronously` funkcí. `Async.Parallel`Funkce přebírá seznam `Async` objektů, nastavuje kód pro každý `Async` objekt úlohy, který se má spustit paralelně, a vrátí `Async` objekt, který představuje paralelní výpočet. Stejně jako u jediné operace zavoláte `Async.RunSynchronously` k zahájení provádění.

`runAll`Funkce spustí paralelní tři asynchronní pracovní postupy a počká, dokud všechny nedokončí.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](index.md)
- [Výpočetní výrazy](computation-expressions.md)
- [Control. Async – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)
