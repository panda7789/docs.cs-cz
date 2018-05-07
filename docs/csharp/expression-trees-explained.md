---
title: Stromy výrazů vysvětlené
description: Další informace o stromů výrazů a jak jsou užitečné při překládání algoritmy pro externí provádění a provádějící kontrolu kódu před jeho provedením.
ms.date: 06/20/2016
ms.assetid: bbcdd339-86eb-4ae5-9911-4c214a39a92d
ms.openlocfilehash: 97cba9e5ec388729d23fb2689dfc1842a42af9b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="expression-trees-explained"></a>Stromy výrazů vysvětlené

[Předchozí – přehled](expression-trees.md)

Strom výrazu je datová struktura, která definuje kódu. Jsou založené na stejné struktury, které kompilátor používá k analýze kódu a generovat kompilovaný výstup. Při procházení tohoto kurzu si všimnete s bit podobnosti mezi stromů výrazů a typy sloužící k vytvoření rozhraní API Roslyn [analyzátory a CodeFixes](https://github.com/dotnet/roslyn-analyzers).
(Analyzátory a CodeFixes jsou balíčky NuGet, které statické analýzám na kód a můžete navrhnout potenciální opravy pro Vývojář). Koncepty jsou podobné a konečný výsledek je datová struktura, která umožňuje prozkoumání zdrojového kódu smysluplný způsobem. Stromy výrazů jsou však založené na sadu uvidíte úplně jiné třídy a rozhraní API než Roslyn rozhraní API.
    
Podívejme se na jednoduchý příklad.
Zde je řádek kódu:
```csharp
var sum = 1 + 2;
```
Pokud byste chtěli analyzovat to jako strom výrazu, stromu obsahuje několik uzlů.
Nejkrajnější uzel je příkaz deklarace proměnné s přiřazení (`var sum = 1 + 2;`) tento nejkrajnější uzel obsahuje několik podřízené uzly: deklarace proměnné, operátor přiřazení a výraz představující symbolem rovná se pravé straně. Výraz je další rozděleno na výrazy, které představují operace sčítání a levé a pravé operandy přidání.

Umožňuje rozbalit soubor trochu více výrazů, které tvoří na pravé straně symbolem rovná se.
Výraz `1 + 2`. Které je výraz binární. Přesněji řečeno je přidání binárního výrazu. Výraz binární přidání má dva podřízené objekty představující levé a pravé uzly přidání výraz. Zde jsou oba uzly konstantní výrazy: levý operand je hodnota `1`, a pravý operand je hodnota `2`.

Vizuální, je celý příkaz stromu: můžete spustit na kořenový uzel a cestovat na každý uzel ve stromu zobrazíte kód, který tvoří příkaz:

- Příkaz deklarace proměnné s přiřazení (`var sum = 1 + 2;`)
    * Deklarace typu implicitní proměnné (`var sum`)
        - Implicitní var – klíčové slovo (`var`)
        - Název proměnné deklarace (`sum`)
    * Operátor přiřazení (`=`)
    * Binární přidání výraz (`1 + 2`)
        - Levý operand (`1`)
        - Operátor sčítání (`+`)
        - Pravý operand (`2`)

To může vypadat složité, ale je velmi efektivní. Následující stejný postup můžete rozložit mnohem složitější výrazy. Vezměte v úvahu tento výraz:
```csharp
var finalAnswer = this.SecretSauceFunction(
    currentState.createInterimResult(), currentState.createSecondValue(1, 2),
    decisionServer.considerFinalOptions("hello")) +
    MoreSecretSauce('A', DateTime.Now, true);
```

Výraz výše je také deklarace proměnné s přiřazení.
V tomto případě je pravá strana přiřazení mnohem složitější stromu.
Není, který bude rozložit tento výraz, ale zvažte, které mohou být různé uzly. Existují pomocí aktuálního objektu jako přijímač, ten, který má explicitního volání metod `this` příjemce, který nemá. Jsou volání metod pomocí jiné objekty příjemce, konstantní argumenty různých typů. A nakonec je přidání binární operátor. V závislosti na návratový typ `SecretSauceFunction()` nebo `MoreSecretSauce()`, že operátor sčítání binární může být volání metody přepsaného přidání operátoru řešení pro volání statickou metodu operátor binární sčítání definovaný pro třídu.

Výraz výše i přes tento dosahovaný složitost vytvoří stromová struktura, která lze procházet jako snadno jako první ukázka. Můžete ponechat procházení podřízené uzly najít uzlů listu ve výrazu. Nadřazené uzly budou mít odkazy na jejich podřízené a každý uzel má vlastnost, která popisuje, jaký druh uzlu je.

Struktura stromu výrazů je velmi konzistentní. Jakmile jste se naučili základy, můžete i těch nejsložitějších kód pochopit, když je reprezentována jako strom výrazu se nezdařilo. Eleganci ve struktuře dat vysvětluje, jak analyzovat těch nejsložitějších programy C# a vytvořit správné výstup z tohoto složitá zdrojového kódu kompilátor jazyka C#.

Jakmile jste se seznámili s strukturu stromů výrazů, zjistíte, že znalostní báze, kterou získáte rychle umožňuje pracovat s mnoha více pokročilé scénáře. Je neuvěřitelné efektivitě k stromů výrazů.

Kromě překladu algoritmy s cílem provést v jiných prostředích, stromy výrazů slouží k usnadnění zápisu algoritmy, které Kontrola kódu před jeho provedením. Můžete napíše metoda, jejíž argumenty jsou výrazy a zkontrolujte tyto výrazy před provedením kód. Strom výrazu je úplná reprezentace kód: uvidíte hodnoty žádné dílčí výrazu.
Můžete zobrazit názvy metod a vlastností. Zobrazí se hodnota žádné konstantní výrazy.
Také můžete převést strom výrazu delegáta spustitelný soubor a spouštění kódu.

Rozhraní API pro stromy výrazů umožňují vytvářet stromy, které představují téměř všechny konstrukce platný kód. Z důvodu zjednodušení co nejjednodušší, ale nelze některé idioms C# vytvořit v strom výrazu se nezdařilo. Jedním z příkladů je asynchronní výrazy (pomocí `async` a `await` klíčová slova). Pokud vaše potřeby vyžadují asynchronní algoritmy, potřebujete upravit `Task` objekty přímo, nikoli spoléhají na podporu kompilátoru. Další je při vytváření smyčky. Obvykle vytvoříte tak, že pomocí `for`, `foreach`, `while` nebo `do` smyčky. Jak uvidíte [dál v této série](expression-trees-building.md), rozhraní API pro stromy výrazů podporovat výraz jedinou smyčku `break` a `continue` výrazů, které určují, že opakování ve smyčce opakování.

Jednou z věcí, které nelze provést je upravit strom výrazu se nezdařilo.  Stromy výrazů jsou neměnné datové struktury. Pokud chcete mutovat (změnit) výrazu stromu, je nutné vytvořit novou větev, který je kopií původního, ale s požadované změny. 

[Další – Framework typy podpůrné stromů výrazů](expression-classes.md)
