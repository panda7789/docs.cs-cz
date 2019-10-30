---
title: Lokální funkce vs. výrazy lambda
description: Přečtěte si, proč místní funkce mohou být lepší volbou než výrazy lambda.
ms.date: 06/27/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.openlocfilehash: a644b6868a37b3d6231a514dc37030cae062785a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038803"
---
# <a name="local-functions-compared-to-lambda-expressions"></a>Místní funkce ve srovnání s lambda výrazy

Na první pohled jsou [místní funkce](programming-guide/classes-and-structs/local-functions.md) a [výrazy lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) velmi podobné. V mnoha případech je volba mezi používáním výrazů lambda a místními funkcemi v oblasti stylu a osobní preference. Existují však reálné rozdíly v tom, kde můžete použít jednu nebo druhou, o které byste měli vědět.

Pojďme se podívat na rozdíly mezi implementací algoritmu faktoriál lokální funkce a výrazu lambda. První verze pomocí místní funkce:

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Naproti tomu implementace s verzí, která používá výrazy lambda:

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Místní funkce mají názvy. Výrazy lambda jsou anonymní metody, které jsou přiřazeny k proměnným, které jsou `Func` nebo `Action` typech. Při deklaraci místní funkce jsou typy argumentů a návratový typ součástí deklarace funkce. Namísto části těla výrazu lambda jsou typy argumentů a návratový typ součástí deklarace typu proměnné výrazu lambda. Tyto dvě rozdíly mohou být způsobeny jasným kódem.

Místní funkce mají různá pravidla pro jednoznačné přiřazení než výrazy lambda. Na deklaraci místní funkce se dá odkazovat z libovolného umístění kódu, kde se nachází v oboru. Výraz lambda musí být přiřazen proměnné delegáta před tím, než může být k němu přistupný (nebo volán prostřednictvím delegáta odkazujícího na výraz lambda.) Všimněte si, že verze s výrazem lambda musí deklarovat a inicializovat výraz lambda `nthFactorial` před jeho definováním. To nevede k chybě kompilace pro odkazování `nthFactorial` před jejich přiřazením.
Tyto rozdíly znamenají, že rekurzivní algoritmy je snazší vytvořit pomocí místních funkcí. Můžete deklarovat a definovat místní funkci, která volá sama sebe. Lambda výrazy musí být deklarovány a přiřazena výchozí hodnota, aby bylo možné je znovu přiřadit k těle, který odkazuje na stejný výraz lambda.

Pravidla přiřazení mají vliv také na všechny proměnné, které jsou zachyceny místní funkcí nebo výrazem lambda. Místní funkce i pravidla výrazů lambda vyžadují, aby všechny zachycené proměnné byly jednoznačně přiřazeny v okamžiku, kdy je místní funkce nebo lambda výraz převedena na delegáta. Rozdílem je, že výrazy lambda jsou převedeny na delegáty při jejich deklaraci. Lokální funkce jsou převedeny na delegáty pouze v případě, že se používají jako delegát. Deklarujete-li místní funkci a pouze na ni odkazujete tak, že ji zavoláte jako metodu, nebude převedena na delegáta. Toto pravidlo umožňuje deklarovat místní funkci v jakémkoli vhodném umístění v jeho ohraničujícím oboru. Je běžné deklarovat místní funkce na konci nadřazené metody za libovolnými návratovými příkazy.

Třetí, kompilátor může provádět statickou analýzu, která umožňuje místním funkcím omezit přiřazení zachycených proměnných v ohraničujícím oboru. Vezměte v úvahu tento příklad:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Kompilátor může určit, že `LocalFunction` jednoznačně přiřadí `y` při volání. Vzhledem k tomu, že `LocalFunction` je volána před příkazem `return`, `y` je jednoznačně přiřazeno v příkazu `return`.

Analýza, která umožňuje ukázkovou analýzu, umožňuje čtvrtý rozdíl.
V závislosti na jejich použití se můžou místní funkce vyhnout přidělení haldy, které jsou vždy nutné pro výrazy lambda. Pokud místní funkce není nikdy převedena na delegáta a žádná z proměnných zachycených lokální funkcí není zachycena jinými výrazy lambda nebo místními funkcemi, které jsou převedeny na delegáty, kompilátor může vyhnout přidělení haldy. 

Vezměte v úvahu tento asynchronní příklad:

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

Uzavření tohoto výrazu lambda obsahuje proměnné `address`, `index` a `name`. V případě místních funkcí může být objekt, který implementuje uzávěr, `struct` typ. Tento typ struktury by byl předán odkazem na místní funkci. Tento rozdíl v implementaci by byl uložen při přidělení.

Vytváření instancí nezbytných pro výrazy lambda znamená dodatečné přidělení paměti, což může být výkonový faktor v časově důležitých cestách kódu.
Místní funkce tyto režie neúčtují. V příkladu výše má verze lokálních funkcí 2 méně přidělení než verze výrazu lambda.

> [!NOTE]
> Lokální funkce ekvivalentní této metodě používá také třídu pro uzavření. Určuje, zda je uzavření místní funkce implementováno jako `class` nebo `struct` je podrobnosti implementace. Místní funkce může použít `struct`, zatímco lambda bude vždy používat `class`.

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

Jedna poslední výhoda není v této ukázce znázorněná, protože místní funkce se dají implementovat jako iterátory pomocí syntaxe `yield return` k vytvoření sekvence hodnot. Ve výrazech lambda není povolený příkaz `yield return`.

I když se místní funkce můžou jevit jako redundantní pro lambda výrazy, mají ve skutečnosti různé účely a mají odlišná použití.
Lokální funkce jsou efektivnější pro případ, když chcete napsat funkci, která je volána pouze z kontextu jiné metody.
