---
title: Lokální funkce oproti výrazy lambda
description: Zjistěte, proč lokální funkce může být vhodnější než výrazy lambda.
ms.date: 06/27/2016
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.openlocfilehash: 0dfd34c5637bb4b8ae64a66e1ca1164fddec2cd7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="local-functions-compared-to-lambda-expressions"></a>Lokální funkce ve srovnání s výrazy lambda

Na první pohled [lokální funkce](programming-guide/classes-and-structs/local-functions.md) a [výrazy lambda](lambda-expressions.md) jsou velmi podobné. V mnoha případech je výběr mezi použitím lambda – výrazy a lokální funkce řádu style a osobní preference. Existují však skutečné rozdíly ve kterém můžete použít jeden z nich, které byste měli vědět.

Podívejme se na rozdíly mezi místní funkce a implementace výrazu lambda faktoriálu algoritmu. První verzi pomocí místní funkce:

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Kontrastu této implementace s verzí, která používá výrazy lambda:

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Místní funkce mají názvy. Anonymní metody, které jsou přiřazeny k proměnné, které jsou jsou výrazy lambda `Func` nebo `Action` typy. Po deklarování místní funkce typy argumentů a návratový typ jsou součástí deklarace funkce. Namísto část textu argument lambda výrazu, typy argumentů a návratový typ jsou součástí deklarace proměnné typu výrazu lambda. Tyto dvě rozdíly může vést k jasnější kódu.

Místní funkce mají různá pravidla pro jednoznačné přiřazení než výrazy lambda. Deklarace místní funkce lze odkazovat z libovolného místa kódu, kde se nachází v oboru. Výraz lambda musí být přiřazený k proměnné delegáta předtím, než může být přístup (nebo zavolaném prostřednictvím delgate odkazující na výrazu lambda.) Všimněte si, že verze pomocí výrazu lambda musí deklarovat a inicializace výrazu lambda `nthFactorial` před definováním ho. Proti tomu má za následek chybu v době kompilace pro odkazování na `nthFactorial` před jeho přiřazení.
Tyto rozdíly znamená, že rekurzivní algoritmů je snazší vytvářet pomocí místní funkcí. Můžete deklarovat a definovat místní funkci, která volá sám sebe. Lambda – výrazy musí být deklarován a přiřazené výchozí hodnotu, než můžou být znovu přiřazen k obsahu, která odkazuje na stejný výraz lambda.

Pravidla jednoznačné přiřazení ovlivní také jakékoli proměnné, které jsou zachyceny místní funkce nebo lamdba epression. Místní funkce a pravidel výrazu lambda požadovat, aby všechny zaznamenané proměnné výborný přiřazené v bodě při převodu místní funkce nebo lambda výraz delegáta. Rozdíl je, že výrazy lambda se převedou na delegáti, když jsou deklarovány. Lokální funkce se převedou na delegáty jenom v případě, že se používá jako delegáta. Pokud deklarovat místní funkce a odkazovat pouze na ho voláním jako metodu, nebudou převedeny na delegáta. Toto pravidlo umožňuje deklarovat místní funkce v libovolném vhodného umístění v jeho nadřazeného oboru. Je běžné deklarovat místní funkce na konci nadřazenou metodu po všech příkazech return.

Kompilátor třetí, můžete provést statické analýzy, která umožňuje místní funkce výborný přiřadit zaznamenané proměnné ve vymezeném oboru. Vezměte v úvahu v tomto příkladu:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Kompilátor můžete určit, který `LocalFunction` výborný přiřadí `y` při volání. Protože `LocalFunction` je volána před provedením `return` příkaz `y` definitiely přiřazen za `return` příkaz.

Analýza umožňující analysis příklad umožňuje čtvrtý rozdíl.
V závislosti na jejich použití se můžete vyhnout lokální funkce přidělení haldy, které jsou vždy potřebné pro výrazy lambda. Pokud je místní funkce nikdy převedeno na delegáta a žádné proměnné zachycenou místní funkce zachycenou další lambdas nebo místní funkce, které se převedou na delegáty, kompilátor se můžete vyhnout přidělení haldy. 

Tento příklad asynchronní vezměte v úvahu:

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

Obsahuje uzavření pro tento výraz lambda `address`, `index` a `name` proměnné. V případě místní funkce, může být objektu, který implementuje uzavření `struct` typu. Struktura typu by byly předány podle odkaz na tuto funkci místní. Tento rozdíl v implementaci by uložit na přidělení.

Instance, které jsou nezbytné pro výrazy lambda znamená přidělení paměť navíc, které můžou být faktor v cestách kód kritický pro čas.
Lokální funkce nevznikají Tato dodatečná režie. V předchozím příkladu musí lokální funkce verze 2 přidělení méně než verze výrazu lambda.

> [!NOTE]
> Místní funkce ekvivalent tato metoda také používá třídu pro uzavření. Jestli uzavření pro místní funkce je implementovaná jako `class` nebo `struct` je podrobností implementace. Může použít místní funkce `struct` zatímco lambda bude vždy používat `class`.

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

Jednou z výhod konečné není ukázáno v této ukázce je, že lokální funkce může být prováděny jako iterátory, pomocí `yield return` syntaxe k vytvoření pořadí hodnot. `yield return` Příkaz není povolen v výrazy lambda.

Při místní funkce se může zdát redundantní výrazy lambda, se ve skutečnosti slouží k jiným účelům a mít jiný používá.
Lokální funkce jsou efektivnější pro případ, pokud chcete vytvořit funkci, která je volána pouze z kontextu jinou metodu.
