---
title: Vysvětlení stromů výrazů
description: Další informace o stromů výrazů a jak jsou užitečné při překládání algoritmy pro externí spuštění a kontrolní kódu před jeho provedením.
ms.date: 06/20/2016
ms.assetid: bbcdd339-86eb-4ae5-9911-4c214a39a92d
ms.openlocfilehash: 3bad826bb58ff361688d3e13497343661e7edbd3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646591"
---
# <a name="expression-trees-explained"></a>Vysvětlení stromů výrazů

[Předchozí – přehled](expression-trees.md)

Strom výrazu je datová struktura, která definuje kódu. Jsou založené na stejné struktury, které kompilátor používá k analýze kódu a generovat kompilovaný výstup. Při čtení kroky v tomto kurzu si povšimněte hodně podobnosti mezi stromů výrazů a typy používané v rozhraní Roslyn API k vytvoření [analyzátory a CodeFixes](https://github.com/dotnet/roslyn-analyzers).
(Analyzátory a CodeFixes jsou balíčky NuGet, které provádějí statickou analýzu kódu a můžete navrhnout možné opravy pro vývojáře.) Koncepty jsou podobné a konečný výsledek je datová struktura, která umožňuje zkoumání zdrojový kód srozumitelným způsobem. Stromy výrazů jsou však založena na zcela jinou sadu tříd a rozhraní API než rozhraní Roslyn API.

Podívejme se na jednoduchý příklad.
Tady je řádek kódu:

```csharp
var sum = 1 + 2;
```

Pokud byste chtěli analyzovat to jako strom výrazu, stromu obsahuje několik uzlů.
Nejkrajnější uzel je deklarace proměnné příkazu přiřazení (`var sum = 1 + 2;`) nejkrajnější uzlu obsahuje několik podřízených uzlů: deklaraci proměnné, operátor přiřazení a výraz představující pravé straně znaménka rovná se. Výraz je dále rozdělená na výrazy, které představují operaci sčítání a levé a pravé operandy sčítání.

Pojďme k podrobnostem o něco více výrazů, které tvoří pravé straně znaménka rovná se.
Výraz je `1 + 2`. To je binární výraz. Přesněji řečeno je binární Přidání výrazu. Binární Přidání výrazu má dva podřízené prvky představující levé a pravé uzly Přidání výrazu. Oba uzly tady, jsou konstantní výrazy: Levý operand je hodnota `1`, a pravého operandu je hodnota `2`.

Vizuálně je celý příkaz větve: Můžete spustit v kořenovém uzlu a cestovat na každý uzel ve stromu zobrazíte kód, který vytvoří příkaz:

- Deklarace proměnné příkazu přiřazení (`var sum = 1 + 2;`)
  * Deklarace implicitní typ proměnné (`var sum`)
    - Implicitní var – klíčové slovo (`var`)
    - Název proměnné deklarace (`sum`)
  * Operátor přiřazení (`=`)
  * Binární Přidání výrazu (`1 + 2`)
    - Levý operand (`1`)
    - Operátor sčítání (`+`)
    - Pravý operand (`2`)

To může vypadat složité, ale je to velmi efektivní. Následující stejný postup můžete rovněž rozložit mnohem složitější výrazy. Vezměte v úvahu tento výraz:

```csharp
var finalAnswer = this.SecretSauceFunction(
    currentState.createInterimResult(), currentState.createSecondValue(1, 2),
    decisionServer.considerFinalOptions("hello")) +
    MoreSecretSauce('A', DateTime.Now, true);
```

Výraz výše je také deklaraci proměnné s přiřazení.
V tomto případě se pravé straně přiřazení mnohem složitější stromu.
Nechystám rozložit tento výraz, ale zvažte, co může být různých uzlech. Jsou volání metod, pomocí aktuálního objektu jako příjemce, který má explicitní `this` příjemce, ten, který se nepodporuje. Existují další příjemce objekty pomocí volání metody, jsou konstantní argumenty různých typů. A nakonec je přidání binární operátor. V závislosti na návratový typ `SecretSauceFunction()` nebo `MoreSecretSauce()`, přidání binární operátor může být volání metody operátor přepsané sčítání, řešení pro volání statické metody operátoru sčítání binární definovaný pro třídu.

Bez ohledu na tato vnímaná složitost výše výraz vytvoří stromové struktuře, která se dá Navigovat stejně snadno jako první ukázku. Můžete zachovat jejich podřízené uzly zobrazíte listové uzly ve výrazu. Nadřazené uzly budou mít odkazy na jejich podřízené položky a každý uzel má vlastnost, která popisuje, jaký druh uzlu je.

Struktura stromu výrazů je velmi konzistentní vzhledem k aplikacím. Když jste se naučili základy, můžete porozumět i nejsložitější kódu, když je datum vyjádřeno jako strom výrazu. Elegance datové struktury vysvětluje, jak C# kompilátoru můžete analyzovat nejvíce komplexní C# programy a vytvoření správné výstupu ze složité zdrojového kódu.

Jakmile byste se seznámit se strukturou stromů výrazů, zjistíte, že znalostní báze, který jste získali rychle umožňuje pracovat s mnoha dalších a dalších pokročilých scénářích. Je Neuvěřitelná napájení na stromy výrazů.

Kromě překladu algoritmy s cílem provést v jiných prostředích, lze pomocí stromů výrazů usnadňují zápis algoritmy, které Kontrola kódu před jeho provedením. Můžete napsat metodu, jejíž argumenty jsou výrazy a zkontrolujte tyto výrazy před spuštěním kódu. Strom výrazu je úplné reprezentace kód: hodnoty všechny dílčí výraz se zobrazí.
Můžete zobrazit názvy metod a vlastností. Zobrazí se hodnota libovolné konstantní výrazy.
Můžete také převést na strom výrazu delegát spustitelný soubor a spusťte kód.

Rozhraní API pro stromy výrazů umožňují vytvářet stromové struktury, které představují téměř libovolný platný kód konstrukce. Nicméně z důvodu zjednodušení stejně jednoduché, jako je to možné, některé C# idiomy nelze vytvořit ve stromu výrazu. Jedním z příkladů je asynchronní výrazy (pomocí `async` a `await` klíčových slov). Pokud vaše potřeby vyžadují asynchronní algoritmy, je třeba k manipulaci s `Task` objekty přímo, namísto závisí na podpoře kompilátoru. Další je při vytváření smyčky. Obvykle vytvoříte pomocí těchto `for`, `foreach`, `while` nebo `do` smyčky. Jak uvidíte [dále v této sérii](expression-trees-building.md), rozhraní API pro stromy výrazů podporují výrazu jedinou smyčku s `break` a `continue` výrazy, které řídí s opakováním smyčky.

Jedna věc, co nelze provést, je změnit strom výrazu.  Stromy výrazů jsou neměnné datové struktury. Pokud chcete na strom výrazu (změnit), musíte vytvořit nového stromu, který je kopií původního, ale s požadované změny.

[Další – Typy architektur podporující stromy výrazů](expression-classes.md)
