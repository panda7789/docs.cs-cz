---
title: Lokální funkce vs. výrazy lambda
description: Zjistěte, proč lokální funkce může být vhodnější než výrazů lambda.
ms.date: 06/27/2016
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.openlocfilehash: 2b98ebeeb3866779715fa629c2518f739e196ae8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740429"
---
# <a name="local-functions-compared-to-lambda-expressions"></a>Lokální funkce ve srovnání s výrazy lambda

Na první pohled [lokální funkce](programming-guide/classes-and-structs/local-functions.md) a [výrazy lambda](lambda-expressions.md) jsou velmi podobné. V mnoha případech mezi pomocí výrazů lambda a lokální funkce je otázkou styl a osobních preferencích. Existují však skutečné rozdíly ve které můžete použít jeden z nich, kterých byste měli vědět.

Podívejme se na rozdíly mezi lokální funkcí a implementací výraz lambda faktoriálu algoritmu. První verze pomocí lokální funkce:

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Kontrast tuto implementaci s verzí, který používá výrazy lambda:

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Lokální funkce mají názvy. Výrazy lambda jsou anonymní metody, které jsou přiřazeny proměnné, které jsou `Func` nebo `Action` typy. Při deklaraci lokální funkce typy argumentů a návratový typ jsou součástí deklarace funkce. Namísto část těla výrazu lambda výraz, typ argumentu a návratový typ jsou součástí deklarace proměnné typu výrazu lambda. Tyto dva rozdíly může vést k srozumitelnější kód.

Místní funkce mají jiná pravidla pro jednoznačného přiřazení než výrazů lambda. Deklarace lokální funkce lze odkazovat z libovolného kódu místa, kde se nachází v oboru. Výraz lambda musí být přiřazen proměnné delegáta předtím, než ho můžete získat přístup (nebo ji volat prostřednictvím delegáta odkazující na výraz lambda.) Všimněte si, že verze použití výrazu lambda musí deklarovat a inicializovat výraz lambda `nthFactorial` před potřeba ho definovat. Pokud to neuděláte má za následek chybu v době kompilace pro odkazování na `nthFactorial` před přiřazením.
Tyto rozdíly znamená, že jsou rekurzivní algoritmy vytvářel pomocí místních funkcí. Můžete deklarovat a definovat místní funkci, která se zavolá sama sebe. Výrazy lambda musí být deklarovány a přiřadit výchozí hodnotu dříve, než je možné znovu přiřazen do textu, který odkazuje na stejný výraz lambda.

Pravidla jednoznačného přiřazení také vliv na všechny proměnné, které jsou zachyceny na základě místní funkce nebo lambda výraz. Lambda výraz pravidla i lokální funkce vyžadují, že všechny zachycené proměnné jsou jednoznačně přiřazena v okamžiku, když místní funkce nebo lambda výraz je převeden na delegáta. Rozdíl je, že výrazy lambda jsou převedeny na delegáty, pokud jsou deklarovány. Lokální funkce jsou převedeny na delegáty pouze při použití jako delegát. Je-li deklarovat lokální funkce a jenom na něj odkazovat pomocí volání jako metodu, nebudou převedeny na delegáta. Toto pravidlo umožňuje deklarovat lokální funkce v libovolném vhodné umístění ve svém nadřazeném oboru. Je běžné, chcete-li deklarovat lokální funkce na konci nadřazenou metodu po všechny návratové příkazy.

Třetí kompilátor může provádět statické analýzy umožňující místní funkce jednoznačně přiřadit zachyceným proměnným v nadřazeném oboru. Podívejte se například:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Kompilátor může určit, který `LocalFunction` jednoznačně přiřadí `y` při volání. Protože `LocalFunction` je volána před provedením `return` příkazu `y` je jednoznačně přiřazena v `return` příkazu.

Analýzy, která umožňuje analýzu příklad umožňuje čtvrtý rozdíl.
V závislosti na jejich používání se můžete vyhnout místních funkcí přidělení haldy, které jsou vždy nezbytné pro výrazy lambda. Pokud je lokální funkce nikdy převeden na delegáta a žádné zachycené ve funkci místní proměnné nezachytává dalších výrazů lambda nebo místní funkce, které jsou převedeny na delegáty, kompilátor se vyhnout přidělení haldy. 

Podívejte se například asynchronní:

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

Obsahuje uzavření pro tento výraz lambda `address`, `index` a `name` proměnné. V případě místních funkcí, může být objekt, který implementuje uzavření `struct` typu. Tento typ struktury by být předány podle odkazu na místní funkci. Tento rozdíl v implementaci byste uložit na přidělení.

Instance, které jsou nezbytné pro výrazy lambda znamená, že paměť navíc přidělení, které mohou být faktor výkonu v cestách časově kritického kódu.
Lokální funkce nejsou tato dodatečná režie spojené. V předchozím příkladu má lokální funkce verze 2 přidělení méně než verze výrazu lambda.

> [!NOTE]
> Lokální funkce ekvivalent tato metoda také používá třídu pro uzavření. Zda uzávěru lokální funkce je implementovaná jako `class` nebo `struct` je podrobnost implementace. Použít lokální funkci `struct` že výraz lambda bude vždy používat `class`.

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

Jednou z výhod konečné není ukázáno v tomto příkladu je, že je lokální funkce implementovat jako iterátory, přičemž pomocí `yield return` syntaxi pro vytvoření sekvenci hodnot. `yield return` Nejsou povoleny ve výrazech lambda.

Zatímco lokální funkce se může zdát redundantní pro výrazy lambda, jsou ve skutečnosti slouží k jiným účelům a mají různá použití.
Lokální funkce jsou efektivnější pro případ, když chcete vytvořit funkci, která je volána pouze z kontextu jinou metodu.
