---
title: Místní funkce vs. lambda výrazy
description: Zjistěte, proč mohou být místní funkce lepší volbou než výrazy lambda.
ms.date: 06/27/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.openlocfilehash: 13cc3fe47bbcd6a465347a6c991b2006586c78fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173338"
---
# <a name="local-functions-compared-to-lambda-expressions"></a>Místní funkce ve srovnání s lambda výrazy

Na první pohled jsou [si místní funkce](programming-guide/classes-and-structs/local-functions.md) a [lambda výrazy](./programming-guide/statements-expressions-operators/lambda-expressions.md) velmi podobné. V mnoha případech je volba mezi použitím lambda výrazů a místních funkcí otázkou stylu a osobních preferencí. Existují však skutečné rozdíly v tom, kde můžete použít jeden nebo druhý, že byste měli být vědomi.

Podívejme se na rozdíly mezi implementací místní funkce a lambda výraz faktoriálního algoritmu. Nejprve verze pomocí místní funkce:

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Kontrast, že implementace s verzí, která používá lambda výrazy:

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Místní funkce mají názvy. Lambda výrazy jsou anonymní metody, které jsou `Func` `Action` přiřazeny proměnné, které jsou nebo typy. Když deklarujete místní funkci, typy argumentů a návratový typ jsou součástí deklarace funkce. Místo toho, aby byly součástí těla výrazu lambda, jsou typy argumentů a návratový typ součástí deklarace typu proměnné výrazu lambda. Tyto dva rozdíly mohou mít za následek jasnější kód.

Místní funkce mají různá pravidla pro jednoznačné přiřazení než výrazy lambda. Místní deklarace funkce lze odkazovat z libovolného umístění kódu, kde je v oboru. Výraz lambda musí být přiřazen proměnné delegáta před tím, než k němu bude přístupná (nebo volána prostřednictvím delegáta odkazujícího na výraz lambda.) Všimněte si, že verze pomocí výrazu lambda musí deklarovat a inicializovat výraz lambda `nthFactorial` před jeho definováním. Pokud tak neučiníte, dojde k `nthFactorial` chybě čas kompilace pro odkazování před jeho přiřazením.
Tyto rozdíly znamenají, že rekurzivní algoritmy lze snadněji vytvořit pomocí místních funkcí. Můžete deklarovat a definovat místní funkci, která volá sama sebe. Lambda výrazy musí být deklarovány a přiřazena výchozí hodnota před jejich přenastavení na tělo, které odkazuje na stejný výraz lambda.

Pravidla jednoznačného přiřazení také ovlivňují všechny proměnné, které jsou zachyceny místním výrazem funkce nebo lambda. Místní funkce i pravidla výrazu lambda vyžadují, aby všechny zachycené proměnné byly jednoznačně přiřazeny v okamžiku, kdy je místní funkce nebo výraz lambda převeden na delegáta. Rozdíl je, že lambda výrazy jsou převedeny na delegáty, když jsou deklarovány. Místní funkce jsou převedeny na delegáty pouze v případě, že se používají jako delegát. Pokud deklarujete místní funkci a pouze na ni odkazujete voláním jako metoda, nebude převedena na delegáta. Toto pravidlo umožňuje deklarovat místní funkci na libovolném vhodném místě v jeho oboru uzavření. Je běžné deklarovat místní funkce na konci nadřazené metody za všechny příkazy return.

Za třetí, kompilátor může provádět statickou analýzu, která umožňuje místním funkcím určitě přiřadit zachycené proměnné v ohraničujícím oboru. Vezměme si tento příklad:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Kompilátor může `LocalFunction` určit, `y` že určitě přiřadí při volání. Protože `LocalFunction` je volána `y` před příkazem, `return` `return` je určitě přiřazena v příkazu.

Analýza, která umožňuje ukázkovou analýzu umožňuje čtvrtý rozdíl.
V závislosti na jejich použití místní funkce můžete vyhnout přidělení haldy, které jsou vždy nezbytné pro výrazy lambda. Pokud místní funkce není nikdy převedena na delegáta a žádná z proměnných zachycených místní funkcí je zachycena jinými lambdy nebo místními funkcemi, které jsou převedeny na delegáty, může se kompilátor vyhnout přidělení haldy.

Vezměme si tento asynchronní příklad:

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

Uzavření pro tento výraz lambda `index` `name` obsahuje `address`proměnné , a proměnné. V případě místních funkcí může být objekt, který `struct` implementuje uzavření typu. Tento typ struktury by byl předán odkazem na místní funkci. Tento rozdíl v implementaci by ušetřit na přidělení.

Instance nezbytné pro lambda výrazy znamená další přidělení paměti, které mohou být faktor výkonu v časově kritické cesty kódu.
Místní funkce nevznikají tuto režii. Ve výše uvedeném příkladu má verze místních funkcí o 2 méně přidělení než verze výrazu lambda.

> [!NOTE]
> Místní ekvivalent funkce této metody také používá třídu pro uzavření. Zda uzavření pro místní funkce je `class` implementována jako nebo `struct` nebo je podrobnosti implementace. Místní funkce může `struct` používat vzhledem k tomu, `class`lambda bude vždy používat .

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

Jednou z konečných výhod, které nejsou v této ukázce prokázány, je, že místní funkce mohou být implementovány jako iterátory pomocí `yield return` syntaxe k vytvoření posloupnosti hodnot. Příkaz `yield return` není povolen ve výrazech lambda.

Zatímco místní funkce se může zdát redundantní pro lambda výrazy, ve skutečnosti slouží různým účelům a mají různé použití.
Místní funkce jsou efektivnější pro případ, pokud chcete napsat funkci, která je volána pouze z kontextu jiné metody.
