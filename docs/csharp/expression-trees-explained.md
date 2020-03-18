---
title: Vysvětlení stromů výrazů
description: Zjistěte o stromech výrazů a o tom, jak jsou užitečné při překladu algoritmů pro externí spuštění a kontrolu kódu před jeho spuštěním.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: bbcdd339-86eb-4ae5-9911-4c214a39a92d
ms.openlocfilehash: 12093e9c9246c87cc5ea3aedaca6ba34acacce4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73036996"
---
# <a name="expression-trees-explained"></a>Vysvětlení stromů výrazů

[Předchozí -- Přehled](expression-trees.md)

Strom výrazů je datová struktura, která definuje kód. Jsou založeny na stejné struktury, které kompilátor používá k analýze kódu a generovat zkompilovaný výstup. Při čtení tohoto kurzu si všimnete poměrně dost podobnosti mezi stromy výrazů a typy používanými v roslynských apich k sestavení [analyzátorů a oprav kódu](https://github.com/dotnet/roslyn-analyzers).
(Analyzátory a codefixes jsou balíčky NuGet, které provádějí statickou analýzu kódu a mohou navrhnout potenciální opravy pro vývojáře.) Koncepty jsou podobné a konečným výsledkem je datová struktura, která umožňuje smysluplnou kontrolu zdrojového kódu. Stromy výrazů jsou však založeny na zcela jinou sadu tříd a api než Roslyn API.

Podívejme se na jednoduchý příklad.
Tady je řádek kódu:

```csharp
var sum = 1 + 2;
```

Pokud byste to měli analyzovat jako strom výrazů, strom obsahuje několik uzlů.
Nejvzdálenější uzel je deklarace proměnné s`var sum = 1 + 2;`přiřazením ( ) Tento nejvzdálenější uzel obsahuje několik podřízených uzlů: deklaraci proměnné, operátor přiřazení a výraz představující pravou stranu znaménko rovná se. Tento výraz je dále rozdělen na výrazy, které představují operaci sčítání a levé a pravé operandy přidání.

Podívejme se trochu dále do výrazů, které tvoří pravou stranu znaménko rovná se.
Výraz je `1 + 2`. To je binární výraz. Přesněji řečeno, je to binární doplněk výraz. Binární doplněk výraz má dvě podřízené objekty, představující levé a pravé uzly výrazu sčítání. Zde jsou oba uzly konstantní výrazy: Levý `1`operand je hodnota a `2`pravý operand je hodnota .

Vizuálně je celý příkaz strom: Můžete začít u kořenového uzlu a cestovat do každého uzlu ve stromu, abyste viděli kód, který tvoří příkaz:

- Prohlášení proměnné s`var sum = 1 + 2;`přiřazením ( )
  - Implicitní deklarace`var sum`typu proměnné ( )
    - Implicitní klíčové`var`slovo var ( )
    - Deklarace názvu`sum`proměnné ( )
  - Operátor přiřazení`=`( )
  - Binární přídavek`1 + 2`výraz ( )
    - Levý operand`1`( )
    - Operátor sčítání`+`( )
    - Pravý operand`2`( )

To může vypadat komplikovaně, ale je to velmi silné. Stejným postupem můžete rozložit mnohem složitější výrazy. Zvažte tento výraz:

```csharp
var finalAnswer = this.SecretSauceFunction(
    currentState.createInterimResult(), currentState.createSecondValue(1, 2),
    decisionServer.considerFinalOptions("hello")) +
    MoreSecretSauce('A', DateTime.Now, true);
```

Výše uvedený výraz je také deklarace proměnné s přiřazením.
V tomto případě je pravá strana přiřazení mnohem složitější strom.
Nebudu rozkládat tento výraz, ale zvážit, jaké by mohly být různé uzly. Existují volání metody pomocí aktuálního objektu jako příjemce, ten, který má explicitní `this` příjemce, ten, který nemá. Existují volání metody pomocí jiných objektů příjemce, existují konstantní argumenty různých typů. A konečně, tam je binární sčítání operátor. V závislosti na `SecretSauceFunction()` návratový typ nebo `MoreSecretSauce()`, že binární sčítání operátor může být volání metody potlačené sčítání operátor, řešení statické metody volání binární sčítání operátor definované pro třídu.

Navzdory této složitosti, výše uvedený výraz vytvoří stromovou strukturu, která může být navigována stejně snadno jako první vzorek. Můžete pokračovat v procházení podřízených uzlů najít listové uzly ve výrazu. Nadřazené uzly budou mít odkazy na své podřízené položky a každý uzel má vlastnost, která popisuje, jaký druh uzlu je.

Struktura stromu výrazů je velmi konzistentní. Jakmile se naučíte základy, můžete pochopit i nejsložitější kód, když je reprezentován jako strom výrazů. Elegance v datové struktuře vysvětluje, jak kompilátor Jazyka C# můžete analyzovat nejsložitější c# programy a vytvořit správný výstup z tohoto složitého zdrojového kódu.

Jakmile se seznámíte se strukturou stromů výrazů, zjistíte, že znalosti, které jste získali rychle, vám umožní pracovat s mnoha dalšími a pokročilejšími scénáři. Tam je neuvěřitelná síla výrazu stromů.

Kromě překladu algoritmů pro spuštění v jiných prostředích lze stromy výrazů usnadnit zápis algoritmů, které kontrolují kód před jeho spuštěním. Můžete napsat metodu, jejíž argumenty jsou výrazy a potom zkontrolujte tyto výrazy před spuštěním kódu. Strom výrazů je úplnou reprezentací kódu: můžete zobrazit hodnoty libovolného dílčího výrazu.
Můžete zobrazit názvy metod a vlastností. Můžete zobrazit hodnotu všech konstantních výrazů.
Můžete také převést strom výrazů na spustitelného delegáta a spustit kód.

Api pro stromy výrazů umožňují vytvářet stromy, které představují téměř všechny platné konstrukce kódu. Chcete-li však zachovat věci co nejjednodušší, některé idiomy jazyka C# nelze vytvořit ve stromu výrazů. Jedním z příkladů jsou asynchronní `async` výrazy (pomocí `await` a klíčová slova). Pokud vaše potřeby vyžadují asynchronní algoritmy, budete `Task` muset manipulovat s objekty přímo, spíše než spoléhat na podporu kompilátoru. Dalším je vytváření smyček. Obvykle je vytvoříte pomocí `for` `foreach`, `while` `do` , nebo smyčky. Jak uvidíte [dále v této řadě](expression-trees-building.md), api pro stromy výrazů podporují výraz jedné smyčky, s `break` výrazy a `continue` výrazy, které řídí opakování smyčky.

Jedna věc, kterou nemůžete udělat, je upravit strom výrazů.  Výraz stromy jsou neměnné datové struktury. Pokud chcete zmutovat (změnit) strom výrazů, musíte vytvořit nový strom, který je kopií originálu, ale s požadovanými změnami.

[Další -- Typy architektury podporující stromy výrazů](expression-classes.md)
