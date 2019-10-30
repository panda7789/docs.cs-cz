---
title: Vysvětlení stromů výrazů
description: Přečtěte si o stromech výrazů a o tom, jak jsou užitečné při překladu algoritmů pro externí spuštění a kontrolu kódu před jeho provedením.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: bbcdd339-86eb-4ae5-9911-4c214a39a92d
ms.openlocfilehash: 12093e9c9246c87cc5ea3aedaca6ba34acacce4d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036996"
---
# <a name="expression-trees-explained"></a>Vysvětlení stromů výrazů

[Předchozí – přehled](expression-trees.md)

Strom výrazu je datová struktura, která definuje kód. Jsou založené na stejných strukturách, které kompilátor používá k analýze kódu a generování zkompilovaného výstupu. Při čtení v tomto kurzu si všimnete trochu podobnosti mezi stromy výrazů a typy používanými v rozhraních API Roslyn k vytváření [analyzátorů a CodeFixes](https://github.com/dotnet/roslyn-analyzers).
(Analyzátory a CodeFixes jsou balíčky NuGet, které provádějí statickou analýzu kódu a můžou navrhovat možné opravy pro vývojáře.) Koncepty jsou podobné a konečný výsledek je datová struktura, která umožňuje srozumitelným způsobem vyzkoušení zdrojového kódu. Stromy výrazů jsou však založeny na zcela jiné sadě tříd a rozhraní API než rozhraní API Roslyn.

Pojďme se podívat na jednoduchý příklad.
Zde je řádek kódu:

```csharp
var sum = 1 + 2;
```

Pokud jste ho mohli analyzovat jako strom výrazu, strom obsahuje několik uzlů.
Nejvzdálenější uzel je příkaz deklarace proměnné s přiřazením (`var sum = 1 + 2;`), který má nejvzdálenější uzel několik podřízených uzlů: deklaraci proměnné, operátor přiřazení a výraz představující pravou stranu znaménka rovná se. Tento výraz je dále rozdělen na výrazy, které reprezentují operaci sčítání a levý a pravý operand přidání.

Pojďme přejít k podrobnostem o výrazech, které tvoří pravou stranu znaménka rovná se.
Výraz je `1 + 2`. To je binární výraz. Konkrétně se jedná o binární výraz sčítání. Výraz výrazu Binary má dva podřízené prvky, reprezentující levý a pravý uzel výrazu sčítání. Tady jsou oba uzly konstantní výrazy: levý operand je hodnota `1`a pravý operand je hodnota `2`.

Vizuálně je celý příkaz stromovou strukturou: můžete začít na kořenovém uzlu a procházet každý uzel stromu a zobrazit kód, který tvoří příkaz:

- Proměnná deklarace příkazu s přiřazením (`var sum = 1 + 2;`)
  - Deklarace implicitního typu proměnné (`var sum`)
    - Implicitní klíčové slovo var (`var`)
    - Deklarace proměnné názvu (`sum`)
  - Operátor přiřazení (`=`)
  - Výraz binárního sčítání (`1 + 2`)
    - Levý operand (`1`)
    - Operátor sčítání (`+`)
    - Pravý operand (`2`)

To může vypadat komplikované, ale je velmi výkonné. Po stejném procesu můžete rozložit mnohem složitější výrazy. Vezměte v úvahu tento výraz:

```csharp
var finalAnswer = this.SecretSauceFunction(
    currentState.createInterimResult(), currentState.createSecondValue(1, 2),
    decisionServer.considerFinalOptions("hello")) +
    MoreSecretSauce('A', DateTime.Now, true);
```

Výše uvedený výraz je také deklarace proměnné s přiřazením.
V této instanci je pravá strana přiřazení mnohem složitější strom.
Tento výraz nebudeme rozložit, ale zvažte, co můžou být jednotlivé uzly. Existují volání metody s použitím aktuálního objektu jako přijímače, který má explicitní `this` přijímač, což není. Existují volání metod pomocí jiných objektů přijímače, existují konstantní argumenty různých typů. A nakonec je k dispozici binární operátor sčítání. V závislosti na návratovém typu `SecretSauceFunction()` nebo `MoreSecretSauce()`může být daný binární operátor sčítání metodou volání přepsaného operátoru sčítání a překládá se na statické volání metody do binárního operátoru sčítání definovaného pro třídu.

Navzdory této vnímané složitosti výše uvedený výraz vytvoří stromovou strukturu, kterou lze snadno přejít jako první vzorek. Chcete-li ve výrazu najít uzly typu list, můžete ve výrazu zůstat přecházení podřízených uzlů. Nadřazené uzly budou mít odkazy na své podřízené položky a každý uzel má vlastnost, která popisuje, jaký typ uzlu je.

Struktura stromu výrazů je velmi konzistentní. Jakmile se naučíte základy, můžete pochopit i nejsložitější kód, když je reprezentován jako strom výrazu. Elegance v datové struktuře vysvětluje, jak může C# kompilátor analyzovat nejvíc komplexní C# programy a vytvořit vhodný výstup z tohoto složitého zdrojového kódu.

Jakmile se seznámíte se strukturou stromů výrazů, zjistíte, že znalostní báze vám pomůže rychle pracovat s mnoha dalšími a pokročilejšími scénáři. Ve stromech výrazů je nedostupné napájení.

Kromě překladu algoritmů pro spuštění v jiných prostředích můžete použít stromy výrazů, aby bylo snazší psát algoritmy, které kontrolují kód před jeho spuštěním. Můžete napsat metodu, jejíž argumenty jsou výrazy, a poté tyto výrazy před spuštěním kódu prostudovat. Strom výrazu je úplná reprezentace kódu: můžete zobrazit hodnoty libovolného dílčího výrazu.
Můžete vidět názvy metod a vlastností. Můžete zobrazit hodnotu libovolných konstantních výrazů.
Strom výrazu lze také převést na delegáta spustitelného souboru a spustit kód.

Rozhraní API pro stromy výrazů umožňují vytvářet stromy, které reprezentují téměř jakoukoli platnou konstrukci kódu. Pokud ale chcete co nejjednodušším způsobem zjednodušit, C# některé idiomy nejde ve stromové struktuře výrazu vytvořit. Jedním z příkladů jsou asynchronní výrazy (pomocí klíčových slov `async` a `await`). Pokud vaše potřeby vyžadují asynchronní algoritmy, je nutné manipulovat přímo s `Task` objekty namísto spoléhání na podporu kompilátoru. Další je vytváření smyček. Obvykle je vytvoříte pomocí `for`, `foreach`, `while` nebo `do` cyklů. Jak vidíte [později v této sérii](expression-trees-building.md), rozhraní API pro stromy výrazů podporují výraz s jednou smyčkou, s `break` a `continue` výrazy, které řídí opakování smyčky.

Jedna z věcí, kterou nemůžete udělat, je změnit strom výrazu.  Stromy výrazů jsou neměnné datové struktury. Chcete-li postupovat (změnit) strom výrazu, je nutné vytvořit nový strom, který je kopií původního objektu, ale s požadovanými změnami.

[Typy dalších--architektury podporující stromy výrazů](expression-classes.md)
