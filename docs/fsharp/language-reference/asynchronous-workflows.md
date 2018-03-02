---
title: "Asynchronní pracovní postupy (F#)"
description: "Další informace o podpoře v programovací jazyk pro asynchronně, provádění výpočtů F # které provedou bez blokování provádění jinou práci."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ee2bb9bf-e04a-4fbe-bf58-46d07229e981
ms.openlocfilehash: e1cbdb452c8f77d97a0231a5ec75d752a98d2ed6
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2018
---
# <a name="asynchronous-workflows"></a>Asynchronní pracovní postupy

> [!NOTE]
Rozhraní API použití odkazu přejdete na webu MSDN.  Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.

Toto téma popisuje podporu v F # pro provádění výpočtů asynchronně, který je bez blokování provádění jinou práci. Například asynchronní výpočty slouží k zápisu aplikace, které mají uživatelská rozhraní, které zůstávají reaguje na uživatele, jak aplikace provede další práci.

## <a name="syntax"></a>Syntaxe

```fsharp
async { expression }
```

## <a name="remarks"></a>Poznámky

V předchozích syntaxi výpočet reprezentována `expression` je nastavení spuštění asynchronně, který je bez blokování aktuální vlákno výpočetní při provádění operace asynchronní režimu spánku, vstupně-výstupních operací a další asynchronní operace jsou. Asynchronní výpočty jsou často zahájeno vlákna na pozadí při spuštění bude pokračovat na aktuální vlákno. Typ výrazu je `Async<'T>`, kde `'T` je typ vrácený výrazem při `return` – klíčové slovo se používá. Kód v takové výraz se označuje jako *asynchronní bloku*, nebo *asynchronní bloku*.

Existuje mnoho různých způsobů programování asynchronně a [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7) třída poskytuje metody, které podporují několik scénářů. Obecný přístup je vytvoření `Async` objekty, které představují výpočtu nebo výpočtů, u kterých chcete spustit asynchronně a pak spusťte tyto výpočty pomocí jedné z spouštěcí funkce. Různé spouštěcí funkce poskytují různé způsoby spuštění asynchronní výpočty a který, kterou použijete, závisí na tom, jestli chcete používat aktuální vlákno, vlákna na pozadí nebo objekt úlohy rozhraní .NET Framework a jestli existují pokračování Funkce, které měly být spuštěny po dokončení výpočet. Například spusťte asynchronní výpočetní na aktuální vlákno, můžete použít [ `Async.StartImmediate` ](https://msdn.microsoft.com/library/2f71d1cc-187f-48cf-ac66-e7fda41c46e3). Když spustíte asynchronní výpočetní z vlákna uživatelského rozhraní, nejsou blokovány smyčky hlavní událost, která zpracovává uživatelské akcí, například stisknutí kláves a aktivity myši, vaše aplikace stále poměrně rychle reaguje.

## <a name="asynchronous-binding-by-using-let"></a>Asynchronní vazby pomocí umožňují!

V pracovním postupu asynchronní některé operace a výrazy jsou synchronní a některé jsou delší výpočtů, které jsou určeny k vrácení výsledku asynchronně. Když zavoláte metodu asynchronně, místo běžný `let` vazby, můžete použít `let!`. Účinek `let!` je umožnit spouštění jako provádí výpočet pokračujte na další výpočty nebo vláken. Po pravé straně `let!` vazby Vrátí zbytek asynchronní pracovního postupu obnoví spuštění.

Následující kód ukazuje rozdíl mezi `let` a `let!`. Řádek kódu, který používá `let` právě vytvoří asynchronní výpočetní jako objekt, který můžete spustit později pomocí, například `Async.StartImmediate` nebo [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b). Řádek kódu, který používá `let!` spustí výpočet, a pak vlákno je pozastaveno, dokud výsledek je k dispozici, na které bodu provádění pokračuje.

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

Kromě `let!`, můžete použít `use!` k provedení asynchronní vazby. Rozdíl mezi `let!` a `use!` je stejný jako rozdíl mezi `let` a `use`. Pro `use!`, objekt je odstraněny na ukončení aktuálního oboru. Všimněte si, že se v aktuální verzi jazyka F # `use!` nepovoluje hodnotu inicializace na hodnotu null, i když `use` nepodporuje.

## <a name="asynchronous-primitives"></a>Asynchronní primitivní elementy.

Je volána metoda, která provede asynchronní jednu úlohu a vrátí výsledek *asynchronní primitivní*, a ty jsou navrženy speciálně pro použití s `let!`. Několik asynchronní primitiv jsou definovány v základní knihovny F #. Tyto dvě metody pro webové aplikace jsou definovány v modulu [ `Microsoft.FSharp.Control.WebExtensions` ](https://msdn.microsoft.com/library/95ef17bc-ee3f-44ba-8a11-c90fcf4cf003): [ `WebRequest.AsyncGetResponse` ](https://msdn.microsoft.com/library/09a60c31-e6e2-4b5c-ad23-92a86e50060c) a [ `WebClient.AsyncDownloadString` ](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a). Obě primitiv stahování dat z webové stránky, danou adresu URL. `AsyncGetResponse` vytváří `System.Net.WebResponse` objekt, a `AsyncDownloadString` vytvoří řetězec, který představuje HTML pro webovou stránku.

Několik primitiv pro asynchronní vstupně-výstupní operace jsou součástí [ `Microsoft.FSharp.Control.CommonExtensions` ](https://msdn.microsoft.com/library/2edb67cb-6814-4a30-849f-b6dbdd042396) modulu. Tyto metody rozšíření `System.IO.Stream` třídy jsou [ `Stream.AsyncRead` ](https://msdn.microsoft.com/library/85698aaa-bdda-47e6-abed-3730f59fda5e) a [ `Stream.AsyncWrite` ](https://msdn.microsoft.com/library/1b0a2751-e42a-47e1-bd27-020224adc618).

Jsou k dispozici v dalších asynchronní primitiv [F # PowerTools](https://fsprojects.github.io/VisualFSharpPowerTools/). Je také možné zapsat vlastní asynchronní primitiv definováním funkce, jehož dokončení textu je uzavřené v bloku asynchronní.

Chcete-li použít asynchronních metod v rozhraní .NET Framework, které jsou určené pro dalšími asynchronními modely F # asynchronní programování modelu, vytvoříte funkci, která vrátí F # `Async` objektu. Knihovny F # obsahuje funkce, které usnadnění udělat.

Jedním z příkladů použití asynchronní pracovní postupy je součástí zde; Existuje mnoho dalších v dokumentaci pro metody [Async – třída](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).

Tento příklad ukazuje, jak používat asynchronní pracovní postupy k provádění výpočtů paralelně.

V následujícím příkladu kódu funkci `fetchAsync` získá HTML text vrácená z webového požadavku. `fetchAsync` Funkce obsahuje asynchronní blok kódu. Když vazbu přišla výsledek asynchronní primitivní, v takovém případě [ `AsyncDownloadString` ](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a), umožňují! se používá namísto umožňují.

Pomocí funkce [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) k provedení asynchronní operaci a počkat na její výsledek. Jako příklad můžete spouštět více asynchronní operace paralelně pomocí [ `Async.Parallel` ](https://msdn.microsoft.com/library/aa9b0355-2d55-4858-b943-cbe428de9dc4) fungovat společně s `Async.RunSynchronously` funkce. `Async.Parallel` Funkce přebírá seznam `Async` objekty, nastaví kód pro každou `Async` objekt úlohy ke spuštění v paralelní a vrátí `Async` objekt, který reprezentuje paralelní výpočty. Stejně jako u jednu operaci zavolání `Async.RunSynchronously` jeho spuštění.

`runAll` Funkce spustí paralelně tři asynchronní pracovní postupy a počká, až budou všechny dokončili.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka F#](index.md)

[Výpočetní výrazy](computation-expressions.md)

[Control.Async – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)
