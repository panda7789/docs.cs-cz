---
title: Asynchronní pracovní postupy (F#)
description: 'Další informace o podpoře F # programovací jazyk pro provádění výpočtů asynchronně, které se spustí bez blokování provádění jiné práce.'
ms.date: 05/16/2016
ms.openlocfilehash: 9516a281701b6c431fc950fe6881359f9c8a672b
ms.sourcegitcommit: dc02d7d95f1e3efcc7166eaf431b0ec0dc9d8dca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37143502"
---
# <a name="asynchronous-workflows"></a>Asynchronní pracovní postupy

> [!NOTE]
Odkaz rozhraní API se dostanete na webu MSDN.  Reference k rozhraní API webu docs.microsoft.com není dokončena.

Toto téma popisuje podporu v jazyce F # pro provádění výpočtů asynchronně, to znamená bez blokování provádění jiné práce. Například asynchronních výpočtů je možné psát aplikace, které mají uživatelská rozhraní, která nadále reagovat na uživatele, jelikož aplikace provede další práci.

## <a name="syntax"></a>Syntaxe

```fsharp
async { expression }
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi výpočtu reprezentována `expression` nastaven na spuštění asynchronně, to znamená bez blokování aktuální vlákno výpočtu. když se provádí operace asynchronního z režimu spánku, vstupně-výstupní operace a jiné asynchronní operace. Asynchronní výpočty jsou často spuštěna ve vlákně na pozadí, když provádění pokračuje v aktuálním vláknu. Typ výrazu je `Async<'T>`, kde `'T` je typu vracenému výrazem při `return` – klíčové slovo se používá. Kód v takový výraz se označuje jako *asynchronní bloku*, nebo *bloku async*.

Existuje řada různých způsobů asynchronně, programování a [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7) třída poskytuje metody, které podporují několik scénářů. Obecný postup je vytvořit `Async` objekty, které představují výpočtu nebo výpočty, které chcete spustit asynchronně a pak spusťte tyto výpočty pomocí jedné z spouštěcí funkce. Různé spouštěcí funkce poskytují různé možnosti spouštění asynchronních výpočtů a ten, který jste použít závisí na tom, jestli chcete použít aktuální vlákno, vlákno na pozadí nebo úloh objekt rozhraní .NET Framework a jestli existují pokračování Funkce, které by měly být spuštěny po dokončení výpočtu. Například v aktuálním vláknu spuštění asynchronního výpočtu, můžete použít [ `Async.StartImmediate` ](https://msdn.microsoft.com/library/2f71d1cc-187f-48cf-ac66-e7fda41c46e3). Při spuštění asynchronního výpočtu z vlákna uživatelského rozhraní neblokujete smyčky hlavních událostí, která zpracovává uživatelské akce, jako je například úhozy na klávesnici a myš aktivity, takže vaše aplikace stále poměrně rychle reaguje.

## <a name="asynchronous-binding-by-using-let"></a>Asynchronní vazby pomocí let!

V asynchronním pracovním postupu některé výrazy a operace jsou synchronní a některé jsou delší výpočty, které jsou určeny k vrácení výsledku asynchronně. Pokud voláte metodu asynchronně, namísto běžný `let` vazby, použijete `let!`. Účinek `let!` je umožnit provádění pokračovat na další výpočtů nebo vlákna, jak se provádí výpočet. Po pravé straně `let!` vazby Vrátí zbytek asynchronní pracovní postup pokračuje v provádění.

Následující kód ukazuje rozdíl mezi `let` a `let!`. Řádek kódu, který používá `let` pouze vytvoří asynchronní výpočet jako objekt, který později můžete spustit pomocí, například `Async.StartImmediate` nebo [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b). Řádek kódu, který používá `let!` spustí výpočet, a potom vlákno je pozastaveno, dokud výsledek je k dispozici, na které bod provádění pokračuje.

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

Kromě `let!`, můžete použít `use!` provádět asynchronní vazby. Rozdíl mezi `let!` a `use!` je stejný jako rozdíl mezi `let` a `use`. Pro `use!`, vyřazení objektu z na konci aktuálního oboru. Všimněte si, že v aktuální verzi jazyka F # `use!` neumožňuje hodnotu má být inicializován na hodnotu null, i když `use` nepodporuje.

## <a name="asynchronous-primitives"></a>Asynchronní primitiv

Je volána metoda, která provádí jednu asynchronní úlohu a vrátí výsledek *asynchronní primitivní*, a ty jsou navrženy speciálně pro použití s `let!`. Několik asynchronních primitivních elementů jsou definovány v základní knihovně F #. Tyto dvě metody pro webové aplikace, které jsou definovány v modulu [ `Microsoft.FSharp.Control.WebExtensions` ](https://msdn.microsoft.com/library/95ef17bc-ee3f-44ba-8a11-c90fcf4cf003): [ `WebRequest.AsyncGetResponse` ](https://msdn.microsoft.com/library/09a60c31-e6e2-4b5c-ad23-92a86e50060c) a [ `WebClient.AsyncDownloadString` ](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a). Obě primitivy stáhnout data z webové stránky, případě adresy URL. `AsyncGetResponse` vytvoří `System.Net.WebResponse` objektu, a `AsyncDownloadString` vytvoří řetězec, který představuje kód HTML na webové stránce.

Jsou součástí několika primitivy pro asynchronní vstupně-výstupních operací [ `Microsoft.FSharp.Control.CommonExtensions` ](https://msdn.microsoft.com/library/2edb67cb-6814-4a30-849f-b6dbdd042396) modulu. Tyto metody rozšíření `System.IO.Stream` třídy jsou [ `Stream.AsyncRead` ](https://msdn.microsoft.com/library/85698aaa-bdda-47e6-abed-3730f59fda5e) a [ `Stream.AsyncWrite` ](https://msdn.microsoft.com/library/1b0a2751-e42a-47e1-bd27-020224adc618).

Můžete taky psát vlastní asynchronní primitivy definováním funkce, jejíž dokončení textové uzavřen v bloku async.

Pokud chcete používat asynchronní metody v rozhraní .NET Framework, které jsou určeny pro dalšími asynchronními modely s F # asynchronní programovací model, vytvoříte funkci, která vrátí jazyka F # `Async` objektu. Knihovna jazyka F # obsahuje funkce, které usnadňují to udělat.

Jedním z příkladů použití asynchronních pracovních postupech je zde uveden; existuje řada dalších v dokumentaci k pro metody [asynchronní třídy](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).

Tento příklad ukazuje, jak pomocí provádí paralelní výpočty asynchronní pracovní postupy.

V následujícím příkladu kódu funkce `fetchAsync` získá HTML text vrácené webové žádosti. `fetchAsync` Funkce obsahuje asynchronní bloku kódu. Když vazbu se provádí na výsledek asynchronní Primitivum, v tomto případě [ `AsyncDownloadString` ](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a), let! používá se místo výrazu let.

Použijte funkci [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) ke spouštění asynchronní operace a počkat na jeho výsledek. Například můžete spustit několik asynchronních operací paralelně s použitím [ `Async.Parallel` ](https://msdn.microsoft.com/library/aa9b0355-2d55-4858-b943-cbe428de9dc4) společně s funkcí `Async.RunSynchronously` funkce. `Async.Parallel` Funkce přebírá seznam `Async` objekty, nastaví kód pro každý `Async` objekt úlohy pro spuštění v paralelních a vrátí `Async` objekt, který reprezentuje paralelní výpočet. Stejně jako u jedné operace volat `Async.RunSynchronously` jeho spuštění.

`runAll` Funkce spustí tři asynchronní pracovní postupy v paralelních a počká, dokud nebude vše dokončena.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka F#](index.md)

[Výpočetní výrazy](computation-expressions.md)

[Control.Async – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)
