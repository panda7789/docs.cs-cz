---
title: Místní funkce – programovací příručka Jazyka C#
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 200fbd097b7c71a1cd392d62622955528a80fd66
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102941"
---
# <a name="local-functions-c-programming-guide"></a>Místní funkce (Průvodce programováním jazyka C#)

Počínaje c# 7.0, C# podporuje *místní funkce*. Místní funkce jsou soukromé metody typu, které jsou vnořeny v jiném členu. Mohou být volány pouze z jejich obsahující člen. Místní funkce lze deklarovat a volat z:

- Metody, zejména metody iterátoru a asynchronní metody
- Konstruktory
- Přístupové objekty vlastností
- Přistupující přístupové akce
- Anonymní metody
- Výrazy lambda
- Finalizační metody
- Další místní funkce

Místní funkce však nelze deklarovat uvnitř člena s výrazem.

> [!NOTE]
> V některých případech můžete použít výraz lambda k implementaci funkcí podporovaných také místní funkcí. Porovnání naleznete v tématu [Místní funkce vs. lambda výrazy](#local-functions-vs-lambda-expressions).

Místní funkce, aby záměr kódu jasné. Každý, kdo čte váš kód, vidí, že metoda není volatelná s výjimkou metody obsahující. Pro týmové projekty také znemožňují jinému vývojáři chybně volat metodu přímo z jiných míst ve třídě nebo struktuře.

## <a name="local-function-syntax"></a>Syntaxe místní funkce

Místní funkce je definována jako vnořená metoda uvnitř obsahujícího člena. Jeho definice má následující syntaxi:

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Místní funkce mohou používat [asynchronní](../../language-reference/keywords/async.md) a [nebezpečné](../../language-reference/keywords/unsafe.md) modifikátory.

Všimněte si, že všechny místní proměnné, které jsou definovány v obsahující člen, včetně jeho parametry metody, jsou přístupné v místní funkci.

Na rozdíl od definice metody nemůže definice místní funkce obsahovat modifikátor přístupu člena. Vzhledem k tomu, že všechny místní funkce `private` jsou soukromé, včetně modifikátoru přístupu, například klíčové slovo, generuje chybu kompilátoru CS0106, "Modifikátor 'private' není platný pro tuto položku.

> [!NOTE]
> Před C# 8.0 místní funkce `static` nemohou obsahovat modifikátor. Včetně `static` klíčového slova generuje chybu kompilátoru CS0106, "Modifikátor 'statické' není platný pro tuto položku."

Kromě toho atributy nelze použít na místní funkci nebo na její parametry a parametry typu.

Následující příklad definuje místní funkci `AppendPathSeparator` s názvem, která `GetText`je soukromá pro metodu s názvem :

[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  

## <a name="local-functions-and-exceptions"></a>Místní funkce a výjimky

Jednou z užitečných funkcí místních funkcí je, že mohou povolit výjimky na povrch okamžitě. Pro metodu iterátory výjimky jsou zobrazeny pouze v případě, že vrácená sekvence je výčtu a ne při iterátoru je načten. Pro asynchronní metody jsou pozorovány všechny výjimky vyzdvižené v asynchronní metodě, když je očekávaná vrácená úloha.

Následující příklad definuje `OddSequence` metodu, která vytvoří vyjmenovává lichá čísla mezi zadaným rozsahem. Protože předá číslo větší než 100 do metody `OddSequence` čítače <xref:System.ArgumentOutOfRangeException>výčtu, metoda vyvolá . Jak ukazuje výstup z příkladu, výjimka se zobrazí pouze při iterát čísla a ne při načtení čítače výčtu.

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]

Místo toho můžete vyvolat výjimku při provádění ověření a před načtením iterátoru vrácením iterátoru z místní funkce, jak ukazuje následující příklad.

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Místní funkce lze použít podobným způsobem pro zpracování výjimek mimo asynchronní operaci. Obvykle výjimky vyzývané v asynchronní metodě <xref:System.AggregateException>vyžadují, abyste prozkoumali vnitřní výjimky . Místní funkce umožňují váš kód selhat rychle a umožňují výjimku, které mají být vyvolány a sledovány synchronně.

Následující příklad používá asynchronní metodu s názvem `GetMultipleAsync` pozastavit po zadaný počet sekund a vrátit hodnotu, která je náhodný násobek tohoto počtu sekund. Maximální zpoždění je 5 sekund; výsledky, <xref:System.ArgumentOutOfRangeException> pokud je hodnota větší než 5. Jak ukazuje následující příklad, výjimka, která je vyvolána při `GetMultipleAsync` předání hodnoty 6 <xref:System.AggregateException> metodě, je zabalena v po `GetMultipleAsync` zahájení spuštění metody.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]

Stejně jako jsme to udělali s metodou iterátoru, můžeme refaktorovat kód z tohoto příkladu provést ověření před voláním asynchronní metody. Jak ukazuje výstup z následujícího <xref:System.ArgumentOutOfRangeException> příkladu, není <xref:System.AggregateException>zabalen v .

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]

## <a name="local-functions-vs-lambda-expressions"></a>Místní funkce vs. lambda výrazy

Na první pohled jsou si místní funkce a [lambda výrazy](../statements-expressions-operators/lambda-expressions.md) velmi podobné. V mnoha případech je volba mezi použitím lambda výrazů a místních funkcí otázkou stylu a osobních preferencí. Existují však skutečné rozdíly v tom, kde můžete použít jeden nebo druhý, že byste měli být vědomi.

Podívejme se na rozdíly mezi implementací místní funkce a lambda výraz faktoriálního algoritmu. Nejprve verze pomocí místní funkce:

[!code-csharp[LocalFunctionFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Kontrast, že implementace s verzí, která používá lambda výrazy:

[!code-csharp[26_LambdaFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Místní funkce mají názvy. Lambda výrazy jsou anonymní metody, které jsou `Func` `Action` přiřazeny proměnné, které jsou nebo typy. Když deklarujete místní funkci, typy argumentů a návratový typ jsou součástí deklarace funkce. Místo toho, aby byly součástí těla výrazu lambda, jsou typy argumentů a návratový typ součástí deklarace typu proměnné výrazu lambda. Tyto dva rozdíly mohou mít za následek jasnější kód.

Místní funkce mají různá pravidla pro jednoznačné přiřazení než výrazy lambda. Místní deklarace funkce lze odkazovat z libovolného umístění kódu, kde je v oboru. Výraz lambda musí být přiřazen proměnné delegáta před tím, než k němu bude přístupná (nebo volána prostřednictvím delegáta odkazujícího na výraz lambda). Všimněte si, že verze pomocí výrazu lambda musí `nthFactorial` deklarovat a inicializovat výraz lambda před jeho definováním. Pokud tak neučiníte, dojde k `nthFactorial` chybě čas kompilace pro odkazování před jeho přiřazením. Tyto rozdíly znamenají, že rekurzivní algoritmy lze snadněji vytvořit pomocí místních funkcí. Můžete deklarovat a definovat místní funkci, která volá sama sebe. Lambda výrazy musí být deklarovány a přiřazena výchozí hodnota před jejich přenastavení na tělo, které odkazuje na stejný výraz lambda.

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

Analýza, která umožňuje ukázkovou analýzu umožňuje čtvrtý rozdíl. V závislosti na jejich použití místní funkce můžete vyhnout přidělení haldy, které jsou vždy nezbytné pro výrazy lambda. Pokud místní funkce není nikdy převedena na delegáta a žádná z proměnných zachycených místní funkcí je zachycena jinými lambdy nebo místními funkcemi, které jsou převedeny na delegáty, může se kompilátor vyhnout přidělení haldy.

Vezměme si tento asynchronní příklad:

[!code-csharp[TaskLambdaExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

Uzavření pro tento výraz lambda `index` `name` obsahuje `address`proměnné , a proměnné. V případě místních funkcí může být objekt, který `struct` implementuje uzavření typu. Tento typ struktury by byl předán odkazem na místní funkci. Tento rozdíl v implementaci by ušetřit na přidělení.

Instance nezbytné pro lambda výrazy znamená další přidělení paměti, které mohou být faktor výkonu v časově kritické cesty kódu. Místní funkce nevznikají tuto režii. Ve výše uvedeném příkladu má verze místních funkcí o 2 méně přidělení než verze výrazu lambda.

> [!NOTE]
> Místní ekvivalent funkce této metody také používá třídu pro uzavření. Zda uzavření pro místní funkce je `class` implementována jako nebo `struct` nebo je podrobnosti implementace. Místní funkce může `struct` používat vzhledem k tomu, `class`lambda bude vždy používat .

[!code-csharp[TaskLocalFunctionExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

Jednou z konečných výhod, které nejsou v této ukázce prokázány, je, že místní funkce mohou být implementovány jako iterátory pomocí `yield return` syntaxe k vytvoření posloupnosti hodnot. Příkaz `yield return` není povolen ve výrazech lambda.

Zatímco místní funkce se může zdát redundantní pro lambda výrazy, ve skutečnosti slouží různým účelům a mají různé použití. Místní funkce jsou efektivnější pro případ, pokud chcete napsat funkci, která je volána pouze z kontextu jiné metody.

## <a name="see-also"></a>Viz také

- [Metody](methods.md)
