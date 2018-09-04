---
title: Porovnávání vzorů – průvodce v C#
description: Další informace o vzoru porovnávání výrazů v jazyce C#
ms.date: 01/24/2017
ms.assetid: 1e575c32-2e2b-4425-9dca-7d118f3ed15b
ms.openlocfilehash: fa327dafe3f924d22b5f0d459eb0b6c7ba60a684
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43522023"
---
# <a name="pattern-matching"></a>Porovnávání vzorů #

Vzory testování, že hodnota patří k určitým *tvar*a můžete *extrahovat* informace z hodnotu, pokud má odpovídající obrazce. Porovnávání vzorů poskytuje stručnější syntaxi pro algoritmy, které už máte ještě dnes. Jste již vytvořili porovnávání vzorů pomocí syntaxe pro stávající algoritmy. Při psaní `if` nebo `switch` příkazy, které testují hodnoty. Když tyto příkazy odpovídají, potom extrahovat a používat informace z této hodnoty. Nové prvky syntaxe jsou rozšíření pro příkazy, které jste už obeznámení s: `is` a `switch`. Tyto nové přípony kombinovat testování hodnotu a extrakci těchto informací.

V tomto tématu se podíváme na novou syntaxi až vám ukážeme, jak umožňuje čitelný a stručné kódu. Porovnávání vzorů umožňuje idiomy kde data a kód jsou oddělené, na rozdíl od objektově orientované vzory, kde data a metody, které s nimi manipulovat jsou úzce svázány.

Pro ilustraci, tyto nové idiomy, budeme pracovat s struktury, které představují geometrické tvary pomocí porovnávání vzorů příkazy. Máte pravděpodobně zkušenosti s vytvářením hierarchií tříd a vytváření [virtuální metody a přepsané metody](methods.md#inherited) k přizpůsobení chování objektu na základě modulu runtime typu objektu.

Tyto metody nejsou pro data, která neodpovídá struktuře hierarchie tříd je to možné. Pokud data a metody jsou oddělené, je potřeba další nástroje. Nové *porovnávání vzorů* konstrukce povolit přehlednější syntaxe sloužící ke zkoumání dat a manipulaci s řízení toku na základě těchto dat všechny podmínky. Již píšete `if` příkazy a `switch` , které testují hodnota proměnné. Při psaní `is` příkazy, které typ proměnné testu. *Porovnávání vzorů* přidává nové funkce pro tyto příkazy.

V tomto tématu budete vytvářet metodu, která vypočítá oblasti jiné geometrické tvary. Ale můžete udělat bez nutnosti uchýlit se k objektově orientované techniky a vytvoření hierarchie tříd u různých tvarů.
Budete používat *porovnávání vzorů* místo.
Při procházení této ukázce, kontrast tohoto kódu s jakým způsobem bude strukturovaná jako hierarchii objektů. Když data musíte dotazování a manipulaci s není hierarchie tříd, porovnávání vzorů umožňuje velmi elegantní návrhy.

Namísto počínaje definici abstraktní tvar a přidávání odlišném tvaru konkrétních tříd, začneme místo toho jednoduchou datovou pouze definice pro každý geometrické tvary:

[!code-csharp[ShapeDefinitions](../../samples/csharp/PatternMatching/Shapes.cs#01_ShapeDefinitions "Shape definitions")]

Z těchto struktur napište metodu, která vypočítá oblasti nějaké obrazce.

## <a name="the-is-type-pattern-expression"></a>`is` Zadejte výraz vzoru

Před C# 7.0, je třeba, otestujte všechny typy v řadě `if` a `is` příkazy:

[!code-csharp[ClassicIsExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#02_ClassicIsExpression "Classic type pattern using is")]

Je výše uvedený kód výrazu classic *vzor typu*: testujete proměnnou k určení jeho typu a různé akce na základě tohoto typu.

Tento kód bude jednodušší pomocí rozšíření `is` výrazu přiřazení proměnných Pokud test proběhne úspěšně:

[!code-csharp[IsPatternExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#03_IsPatternExpression "is pattern expression")]

V této verzi aktualizované `is` výraz testuje proměnné i přiřadí ji nové proměnné typu správné. Také, Všimněte si, že tato verze zahrnuje `Rectangle` typ, který je `struct`. Nové `is` výraz pracuje s typy hodnot a typy odkazů.

Jazyk pravidel pro vzor odpovídající výrazy snáze vyhnete zneužití výsledky odpovídající výraz. V příkladu výše, proměnné `s`, `c`, a `r` pouze v určitém rozsahu a jednoznačně přiřazena při výrazy porovnání odpovídající vzoru `true` výsledky. Pokud se pokusíte použít buď proměnnou na jiné místo, vygeneruje kód chyby kompilátoru.

Podívejme se na obě tato pravidla podrobně, počínaje oboru. Proměnná `c` je v oboru pouze v `else` větev první `if` příkazu. Proměnná `s` je v oboru v metodě `ComputeAreaModernIs`. Důvodem je, že každá větev `if` příkaz vytváří samostatný obor pro proměnné. Ale `if` příkaz sama tak není. To znamená, že proměnné deklarované v `if` jsou ve stejném oboru jako `if` – příkaz (metody v tomto případě.) Toto chování není specifická pro porovnávání vzorů, ale je definované chování proměnné obory a `if` a `else` příkazy.

Proměnné `c` a `s` jsou přiřazeny při funkcím `if` tvrzení jsou pravdivá kvůli jednoznačně přiřazené při true mechanismus.

> [!TIP]
> Ukázky v tomto tématu použijte doporučenou konstrukce, kde je porovnávání `is` výraz jednoznačně přiřadí proměnné shody v `true` větev `if` příkazu.
> Logika může obrátit vyslovením `if (!(shape is Square s))` a proměnná `s` by být přiřazen pouze v `false` větve. Když je platný C#, se nedoporučuje, protože je pro postupujte podle logiky více matoucí.

Tato pravidla znamená, že jste nepravděpodobné, že omylem přístupu výsledek výrazu shoda vzoru v případě, že tento vzor nebyla splněna.

## <a name="using-pattern-matching-switch-statements"></a>Použití porovnávání vzorů `switch` příkazy

Když čas proběhne, budete možná potřebovat k podpoře jiných typů tvaru. Roste počet podmínek, které testujete, zjistíte to pomocí `is` vzoru porovnávání výrazů může být náročné. Kromě nutnosti `if` příkazy pro každý typ, který chcete zkontrolovat, `is` výrazy jsou omezené na testování, pokud je vstup odpovídá jednoho typu. V takovém případě zjistíte, která `switch` vzor odpovídající výrazy bude vhodnější volbou. 

Tradiční `switch` příkaz byl výraz vzoru: podporované konstantní vzorek.
Můžete porovnat proměnnou pro libovolná konstanta použita ve `case` – příkaz:

[!code-csharp[ClassicSwitch](../../samples/csharp/PatternMatching/GeometricUtilities.cs#04_ClassicSwitch "Classic switch statement")]

Pouze vzoru podporovanému službou `switch` příkaz byl konstantní vzorek. Byla dále omezená na číselné typy a `string` typu.
Tato omezení se odebraly a teď můžete psát `switch` zahrne příkaz using vzor typu:

[!code-csharp[Switch Type Pattern](../../samples/csharp/PatternMatching/GeometricUtilities.cs#05_SwitchTypePattern "Compute with `switch` expression")]

Porovnávání vzorů `switch` příkaz používá známou syntaxi pro vývojáře, kteří používali tradiční C-style `switch` příkazu. Každý `case` je vyhodnocen a spuštění kódu pod podmínkou, že odpovídá je vstupní proměnná. Spuštění kódu se nedá "předat" z jeden výraz case na další. syntaxe `case` příkazu vyžaduje každý `case` končit `break`, `return`, nebo `goto`.

> [!NOTE]
> `goto` Příkazy pro přechod na jiný popisek jsou platné pouze pro konstantní vzorek (příkazu classic switch).

Existují důležité nová pravidla, kterými se řídí `switch` příkazu. Omezení typu proměnné v `switch` výraz byly odebrány.
Jakýkoli typ, jako například `object` v tomto příkladu může být použit. Výrazy case, už nejsou omezeny na konstantní hodnoty. Odebírá se těmto omezením znamená, že tuto změnu pořadí `switch` oddíly se může změnit chování programu.

Když omezeno na konstantní hodnoty, ne více než jedna `case` popisek může odpovídat hodnotě `switch` výraz. Kombinovat s pravidlem, které každý `switch` části nesmí být předáno do další části a ho a potom, `switch` oddíly může být změnit jejich uspořádání v libovolném pořadí bez ovlivnění chování.
Nyní, s více zobecnit `switch` výrazy, záleží na pořadí jednotlivých oddílů. `switch` Výrazy jsou vyhodnocovány v pořadí textové. Vykonávání se přenese na první `switch` popisek, který odpovídá `switch` výrazu.  
Všimněte si, že `default` případu se spustí pouze pokud žádné popisky případů odpovídají. `default` Případu se vyhodnocují jako poslední, bez ohledu na jeho textové pořadí. Pokud není žádné `default` případ a žádný z nich `case` příkazy shodují, provádění pokračuje na příkazu za `switch` příkaz. Žádná z `case` popisky kód je spuštěn.

## <a name="when-clauses-in-case-expressions"></a>`when` Klauzule v `case` výrazy

Můžete provést zvláštní případy, které mají 0 oblasti s použitím tvarů `when` klauzuli `case` popisek. Čtverec o délce na straně 0 nebo kruhu s poloměrem 0 má 0 oblasti. Určíte, že při použití podmínky `when` klauzuli `case` popisku:  

[!code-csharp[ComputeDegenerateShapes](../../samples/csharp/PatternMatching/GeometricUtilities.cs#07_ComputeDegenerateShapes "Compute shapes with 0 area")]

Tato změna ukazuje několik důležitých bodů o nové syntaxe. Nejprve je potřeba více `case` popisky můžete použít k jednomu `switch` oddílu. Spuštění tohoto bloku příkazů Pokud některý z nich je `true`. V takovém případě pokud `switch` výraz je kruh nebo čtverec s 0 oblastí, metoda vrátí – konstanta 0.

V tomto příkladu zavádí dvě různé proměnné ve dvou `case` popisky pro první `switch` bloku. Všimněte si, že příkazy v tomto `switch` bloku nepoužívejte buď proměnné `c` (pro kruhu) nebo `s` (pro druhou mocninu).
Ani jeden z těchto proměnných je jednoznačně přiřazena v tomto `switch` bloku.
Pokud některý z těchto případů shodují, se přiřadí jasně jedna z proměnných.
Je však možné předat *který* byla přiřazena v době kompilace, protože obou případech může odpovídat za běhu. Z tohoto důvodu většinou při použití více `case` popisky pro stejný blok, nezpůsobí novou proměnnou `case` příkazu, nebo bude používat pouze proměnné v `when` klauzule.

Přidání tvarů s 0 oblastí přidáme několik dalších typů obrazce: obdélníku a trojúhelník:

[!code-csharp[AddRectangleAndTriangle](../../samples/csharp/PatternMatching/GeometricUtilities.cs#09_AddRectangleAndTriangle "Add rectangle and triangle")]

 Tato sada změn přidá `case` popisků degenerovanou případech popisky a bloky pro každé nové obrazce. 

Nakonec můžete přidat `null` případu k zajištění, argument je `null`:

[!code-csharp[NullCase](../../samples/csharp/PatternMatching/GeometricUtilities.cs#10_NullCase "Add null case")]

Zvláštní chování `null` vzor je zajímavé protože konstanty `null` ve vzoru nemá typ, ale je možné převést na kterýkoli typ odkazu nebo typ připouštějící hodnotu Null. Místo převést `null` na libovolný typ, který definuje jazyk `null` hodnoty nebudou odpovídat libovolný typ vzor, bez ohledu na kompilaci typu proměnné. Díky tomuto chování nové `switch` na základě typu vzor konzistentní s `is` – příkaz: `is` příkazy vždy vrátit `false` Pokud je hodnotou kontroluje `null`. Je také jednodušší: Po zaškrtnutí typ nepotřebujete další kontrolu hodnot null. Uvidíte, že ze skutečnosti, že neexistují žádné null zkontroluje v žádném případě bloků výše uvedené ukázky: nejsou potřebné, protože odpovídající vzoru typ záruky nenulová hodnota.

## <a name="var-declarations-in-case-expressions"></a>`var` deklarace v `case` výrazy

Po zavedení služby `var` jako jeden z výrazů shoda zavádí nová pravidla pro shodu vzoru.

První pravidlo je, že `var` normální typ odvozených pravidel, následuje po deklaraci: typ je odvozen být statického typu výrazu přepínače. Z tohoto pravidla vždy odpovídá typu.

Druhé pravidlo je, že `var` deklarace nemá kontrolu hodnot null, které zahrnují další vzorek výrazy typu. To znamená, že proměnná může mít hodnotu null a v takovém případě je nutné kontrolu hodnot null.

Znamenají, že tyto dvě pravidla v mnoha případech `var` deklarace v `case` výraz odpovídá za stejných podmínek jako `default` výrazu.
Protože libovolné nevýchozí případ je upřednostňována před `default` případech `default` případu se nikdy neprovede.

> [!NOTE]
> Kompilátor negeneruje upozornění v případech, kde `default` případ byl zapsán ale se nikdy neprovede. To je konzistentní s aktuálním `switch` chování příkazu, ve kterém byly vypsali všechny možné případy.

Třetí pravidlo představuje používá kde `var` případě může být užitečné. Představte si, že provádíte porovnávání, pokud je vstupní řetězec a hledáte známého příkazu hodnoty. Můžete například napsat vypadat:

[!code-csharp[VarCaseExpression](../../samples/csharp/PatternMatching/Program.cs#VarCaseExpression "use a var case expression to filter white space")]

`var` Malá a velká shody `null`, prázdný řetězec nebo libovolný řetězec, který obsahuje pouze prázdné znaky. Všimněte si, že předchozí kód používá `?.` operátor Ujistěte se, že se nevyvolá omylem <xref:System.NullReferenceException>. `default` Případ zpracovává libovolné řetězcové hodnoty, které nebudou srozumitelné pro tento příkaz analyzátor.

Toto je jeden příklad, kde můžete chtít zvážit `var` malá a velká výraz, který se liší od `default` výrazu.

## <a name="conclusions"></a>Závěry

*Vzor odpovídající konstrukce* vám umožní snadno spravovat tok řízení mezi různé proměnné a typy, které spolu nesouvisí podle hierarchie dědičnosti. Můžete také řídit logiku na proměnnou používat jakoukoli podmínku, kterou testujete. Umožňuje vzory a idiomy, které budete potřebovat více často, jak vytvářet více distribuovaných aplikací, kde jsou oddělené data a metody, které zpracovávají data. Všimněte si, že tvar struktury používané v tomto příkladu neobsahují žádné metody pouze vlastnosti jen pro čtení.
Porovnávání vzorů spolupracuje s libovolného datového typu. Zápis výrazů, které prověřit objekt a rozhodování řízení toku na základě těchto podmínek.

Porovnat kód od této ukázky s návrhem, které by od vytvoření hierarchie tříd pro abstraktní následují `Shape` a konkrétní odvozený obrazce, každý s vlastní implementaci virtuální metody pro výpočet. Budete často zjistíte, že odpovídající výrazy vzorek může být velmi užitečným nástrojem při práci s daty a chcete aspekty chování nezávislá na infrastruktuře úložiště dat nemuseli dělat starosti.

