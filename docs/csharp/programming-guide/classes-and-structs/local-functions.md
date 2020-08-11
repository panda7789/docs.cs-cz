---
title: Místní funkce – Průvodce programováním v C#
description: Místní funkce v jazyce C# jsou soukromé metody, které jsou vnořené v jiném členu a mohou být volány z jejich nadřazeného člena.
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 854ec7ab4a4cc637c0a5ad03e0344d2f1f7679d2
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063299"
---
# <a name="local-functions-c-programming-guide"></a>Místní funkce (Průvodce programováním v C#)

Počínaje jazykem C# 7,0 podporuje jazyk C# *místní funkce*. Lokální funkce jsou soukromé metody typu, které jsou vnořené v jiném členu. Mohou být volány pouze ze svých nadřazených členů. Místní funkce mohou být deklarovány v a volány z:

- Metody, zejména iterátorové metody a asynchronní metody
- Konstruktory
- Přistupující objekty vlastnosti
- Přístupové objekty událostí
- Anonymní metody
- Výrazy lambda
- Finalizační metody
- Jiné místní funkce

Místní funkce však nelze deklarovat uvnitř člena Expression-těle.

> [!NOTE]
> V některých případech můžete použít výraz lambda pro implementaci funkcí, které podporuje také místní funkce. Porovnání naleznete v tématu [místní funkce vs. lambda výrazy](#local-functions-vs-lambda-expressions).

Místní funkce usnadňují záměr vašeho kódu. Každý, kdo čte váš kód, uvidí, že metoda není možné volat s výjimkou obsahující metody. U týmových projektů také znemožňuje, aby jiný vývojář omylem volal metodu přímo z jiného místa ve třídě nebo struktuře.

## <a name="local-function-syntax"></a>Syntaxe lokální funkce

Lokální funkce je definována jako vnořená metoda uvnitř nadřazeného člena. Jeho definice má následující syntaxi:

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Místní funkce můžou používat modifikátory [Async](../../language-reference/keywords/async.md) a [unsafe](../../language-reference/keywords/unsafe.md) .

Všimněte si, že všechny místní proměnné, které jsou definovány v nadřazeném členu, včetně jeho parametrů metody, jsou přístupné v místní funkci.

Na rozdíl od definice metody nemůže definice lokální funkce zahrnovat modifikátor přístupu ke členu. Vzhledem k tomu, že všechny místní funkce jsou soukromé, včetně modifikátoru přístupu, jako je `private` klíčové slovo, vygeneruje chybu kompilátoru CS0106, modifikátor Private není pro tuto položku platný.

> [!NOTE]
> Před jazykem C# 8,0 nemohou místní funkce obsahovat `static` modifikátor. Zahrnutí `static` klíčového slova generuje chybu kompilátoru CS0106, modifikátor "static" není pro tuto položku platný. "

Kromě toho nelze atributy použít pro místní funkci nebo její parametry a parametry typu.

Následující příklad definuje místní funkci s názvem `AppendPathSeparator` , která je soukromá pro metodu s názvem `GetText` :

[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  

## <a name="local-functions-and-exceptions"></a>Místní funkce a výjimky

Jednou z užitečných funkcí lokálních funkcí je to, že může dojít k okamžitému povrchování výjimek. U iterátorů metod jsou výjimky vyhodnoceny pouze v případě, že je vyhodnocena vrácená sekvence, a ne při načtení iterátoru. Pro asynchronní metody jsou při očekávaných úlohách pozorovány jakékoli výjimky vyvolané v asynchronní metodě.

Následující příklad definuje `OddSequence` metodu, která vytváří výčty lichých čísel mezi zadaným rozsahem. Protože předá metodě Enumerator číslo větší než 100 `OddSequence` , vyvolá metoda <xref:System.ArgumentOutOfRangeException> . Jak výstup z příkladu ukazuje, plochy výjimky pouze při iteraci čísel, a ne při načtení čítače výčtu.

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]

Místo toho můžete vyvolat výjimku při provádění ověřování a před načtením iterátoru vrácením iterátoru z místní funkce, jak ukazuje následující příklad.

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Místní funkce lze použít podobným způsobem pro zpracování výjimek mimo asynchronní operaci. Výjimky vyvolané v asynchronní metodě obvykle vyžadují, abyste prozkoumali vnitřní výjimky <xref:System.AggregateException> . Místní funkce umožňují vašemu kódu selhání rychle a umožňují, aby vaše výjimka byla vyvolána a byla sledována synchronně.

Následující příklad používá asynchronní metodu pojmenovanou `GetMultipleAsync` k pozastavení po zadaný počet sekund a vrátí hodnotu, která je náhodné násobek tohoto počtu sekund. Maximální zpoždění je 5 sekund; <xref:System.ArgumentOutOfRangeException>výsledkem je, že je hodnota větší než 5. Jak ukazuje následující příklad, výjimka, která je vyvolána, když je předána hodnota 6 `GetMultipleAsync` metodě, je zabalena do metody <xref:System.AggregateException> po `GetMultipleAsync` zahájení provádění.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]

Stejně jako u metody iterátoru můžeme kód z tohoto příkladu Refaktorovat, aby bylo ověřování provedeno před voláním asynchronní metody. Jak ukazuje výstup z následujícího příkladu, není <xref:System.ArgumentOutOfRangeException> zabalen do <xref:System.AggregateException> .

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]

## <a name="local-functions-vs-lambda-expressions"></a>Lokální funkce vs. výrazy lambda

Na první pohled jsou místní funkce a [výrazy lambda](../../language-reference/operators/lambda-expressions.md) velmi podobné. V mnoha případech je volba mezi používáním výrazů lambda a místními funkcemi v oblasti stylu a osobní preference. Existují však reálné rozdíly v tom, kde můžete použít jednu nebo druhou, o které byste měli vědět.

Pojďme se podívat na rozdíly mezi implementací algoritmu faktoriál lokální funkce a výrazu lambda. První verze pomocí místní funkce:

[!code-csharp[LocalFunctionFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Naproti tomu implementace s verzí, která používá výrazy lambda:

[!code-csharp[26_LambdaFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Místní funkce mají názvy. Výrazy lambda jsou anonymní metody, které jsou přiřazeny k proměnným, které jsou `Func` nebo `Action` typy. Při deklaraci místní funkce jsou typy argumentů a návratový typ součástí deklarace funkce. Namísto části těla výrazu lambda jsou typy argumentů a návratový typ součástí deklarace typu proměnné výrazu lambda. Tyto dvě rozdíly mohou být způsobeny jasným kódem.

Místní funkce mají různá pravidla pro jednoznačné přiřazení než výrazy lambda. Na deklaraci místní funkce se dá odkazovat z libovolného umístění kódu, kde se nachází v oboru. Výraz lambda musí být přiřazen proměnné delegáta před tím, než bude k němu možné přistupovat (nebo volat prostřednictvím delegáta odkazujícího na výraz lambda). Všimněte si, že verze, která používá výraz lambda, musí deklarovat a inicializovat výraz lambda `nthFactorial` před jeho definováním. Neprovádí se proto Chyba kompilace pro odkazování `nthFactorial` před přiřazením. Tyto rozdíly znamenají, že rekurzivní algoritmy je snazší vytvořit pomocí místních funkcí. Můžete deklarovat a definovat místní funkci, která volá sama sebe. Lambda výrazy musí být deklarovány a přiřazena výchozí hodnota, aby bylo možné je znovu přiřadit k těle, který odkazuje na stejný výraz lambda.

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

Kompilátor může určit, že se `LocalFunction` při volání jednoznačně přiřadí `y` . Protože `LocalFunction` je volána před `return` příkazem, `y` je jednoznačně přiřazen v `return` příkazu.

Analýza, která umožňuje ukázkovou analýzu, umožňuje čtvrtý rozdíl. V závislosti na jejich použití se můžou místní funkce vyhnout přidělení haldy, které jsou vždy nutné pro výrazy lambda. Pokud místní funkce není nikdy převedena na delegáta a žádná z proměnných zachycených lokální funkcí není zachycena jinými výrazy lambda nebo místními funkcemi, které jsou převedeny na delegáty, kompilátor může vyhnout přidělení haldy.

Vezměte v úvahu tento asynchronní příklad:

[!code-csharp[TaskLambdaExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

Uzavření tohoto výrazu lambda obsahuje `address` `index` `name` proměnné a. V případě místních funkcí může být objekt, který implementuje uzávěr, `struct` typu. Tento typ struktury by byl předán odkazem na místní funkci. Tento rozdíl v implementaci by byl uložen při přidělení.

Vytváření instancí nezbytných pro výrazy lambda znamená dodatečné přidělení paměti, což může být výkonový faktor v časově důležitých cestách kódu. Místní funkce tyto režie neúčtují. V příkladu výše má verze lokálních funkcí 2 méně přidělení než verze výrazu lambda.

> [!NOTE]
> Lokální funkce ekvivalentní této metodě používá také třídu pro uzavření. Zda je uzavření místní funkce implementováno jako `class` nebo jako `struct` Podrobnosti implementace. Místní funkce může používat, `struct` zatímco lambda bude vždy používat `class` .

[!code-csharp[TaskLocalFunctionExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

Jedna poslední výhoda není v této ukázce znázorněna, protože lokální funkce lze implementovat jako iterátory pomocí `yield return` syntaxe k vytvoření sekvence hodnot. `yield return`Příkaz není ve výrazech lambda povolen.

I když se místní funkce můžou jevit jako redundantní pro lambda výrazy, mají ve skutečnosti různé účely a mají odlišná použití. Lokální funkce jsou efektivnější pro případ, když chcete napsat funkci, která je volána pouze z kontextu jiné metody.

## <a name="see-also"></a>Viz také

- [Metody](methods.md)
