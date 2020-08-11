---
title: Prohlídka Průvodce C# – C#
description: Novinka v jazyce C#? Seznamte se se základy jazyka.
ms.date: 08/06/2020
ms.openlocfilehash: 42c4ff59a520a1b99bbb2fb01d79d8902e16bdd5
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063546"
---
# <a name="a-tour-of-the-c-language"></a>Prohlídka jazyka C#

C# (vyslovit "viz Sharp") je moderní, objektově orientovaný programovací jazyk, který je typově bezpečný. Jazyk C# má své kořeny v řadě jazyků C a bude okamžitě známý programátorům jazyka C, C++, Java a JavaScriptu. Tato prohlídka poskytuje přehled hlavních součástí jazyka v C# 8 a starších verzích. Pokud chcete prozkoumat jazyk pomocí interaktivních příkladů, vyzkoušejte kurz [Úvod do C#](../tutorials/intro-to-csharp/index.md) .

C# je objektově orientovaný programovací jazyk ***orientovaný na součásti*** . Jazyk c# poskytuje jazykové konstrukce pro přímou podporu těchto konceptů, což C# přirozený jazyk pro vytváření a používání softwarových komponent. Vzhledem k tomu, že v jazyce C# byly přidány funkce pro podporu nových úloh a vznikajících postupů pro návrh softwaru.

Několik funkcí C# pomáhá při konstrukci robustních a odolných aplikací. [***Uvolňování***](../../standard/garbage-collection/index.md) paměti automaticky uvolňuje paměť, kterou zabírá nedosažitelné nepoužívané objekty. [***Zpracování výjimek***](../programming-guide/exceptions/index.md) poskytuje strukturovaný a rozšiřitelný přístup k detekci a obnovení chyb. [***Výrazy lambda***](../programming-guide/statements-expressions-operators/lambda-expressions.md) podporují funkční programovací techniky. [***Syntaxe dotazu***](../linq/index.md) vytváří společný vzor pro práci s daty z libovolného zdroje. Jazyková podpora pro [***asynchronní operace***](../programming-guide/concepts/async/index.md) poskytuje syntaxi pro vytváření distribuovaných systémů. [***Porovnávání vzorů***](..//pattern-matching.md) poskytuje syntaxi pro snadné oddělení dat z algoritmů v moderních distribuovaných systémech. Jazyk C# má [***sjednocený systém typů***](../programming-guide/types/index.md). Všechny typy C#, včetně primitivních typů, jako jsou `int` a `double` , dědí z jednoho kořenového `object` typu. Všechny typy sdílejí sadu běžných operací. Hodnoty libovolného typu mohou být uloženy, přepravovány a provozovány konzistentním způsobem. Jazyk C# navíc podporuje uživatelsky definované typy odkazů i typy hodnot. Jazyk C# umožňuje dynamické přidělování objektů a vloženého úložiště lehkých struktur.

Jazyk C# zvýrazňuje ***správu verzí*** , aby bylo zajištěno, že programy a knihovny se budou v průběhu času vyvíjejí kompatibilním způsobem. Aspekty návrhu jazyka C#, které byly přímo ovlivněny aspekty správy verzí, zahrnují samostatné `virtual` a `override` modifikátory, pravidla pro řešení přetížení metod a podporu explicitních deklarací členů rozhraní.

## <a name="hello-world"></a>Hello World

Program "Hello, World" se tradičně používá k zavedení programovacího jazyka. Tady je v jazyce C#:

:::code language="csharp" interactive="try-dotnet" source="./snippets/shared/HelloWorld.cs":::

Program "Hello, World" začíná `using` direktivou, která odkazuje na `System` obor názvů. Obory názvů poskytují hierarchický způsob uspořádání programů a knihoven v jazyce C#. Obory názvů obsahují typy a jiné obory názvů, například `System` obor názvů obsahuje počet typů, jako je například `Console` Třída odkazovaná v programu, a řadu dalších oborů názvů, například `IO` a `Collections` . `using`Direktiva, která odkazuje na daný obor názvů, umožňuje nekvalifikované použití typů, které jsou členy tohoto oboru názvů. Z důvodu `using` direktivy může program použít `Console.WriteLine` jako zkrácený pro `System.Console.WriteLine` .

`Hello`Třída deklarovaná programem "Hello, World" má jednoho člena, metodu s názvem `Main` . `Main`Metoda je deklarována s `static` modifikátorem. I když metody instance mohou odkazovat na konkrétní ohraničující objekt instance pomocí klíčového slova `this` , statické metody pracují bez odkazů na konkrétní objekt. Podle konvence, statická metoda s názvem `Main` slouží jako vstupní bod programu v jazyce C#.

Výstup programu je vytvořen `WriteLine` metodou `Console` třídy v `System` oboru názvů. Tuto třídu poskytují standardní knihovny tříd, které jsou ve výchozím nastavení automaticky odkazovány kompilátorem.

## <a name="types-and-variables"></a>Typy a proměnné

V jazyce C# existují dva druhy typů: *typy hodnot* a *typy odkazů*. Proměnné typů hodnot přímo obsahují svá data, zatímco proměnné typu odkazu ukládají odkazy na jejich data, přičemž ta se označují jako objekty. U typů odkazů je možné, že dvě proměnné odkazují na stejný objekt a mohou operace na jedné proměnné ovlivnit objekt, na který je odkazováno jinou proměnnou. S typy hodnot mají proměnné, které mají svou vlastní kopii dat, a není možné, že operace na jednom mají vliv na ostatní (s výjimkou `ref` `out` proměnných parametrů a).

***Identifikátor*** je název proměnné. Identifikátor je posloupnost znaků Unicode bez mezer. Identifikátorem může být rezervované slovo jazyka C#, pokud je předpona `@` . To může být užitečné při interakci s ostatními jazyky.

Typy hodnot jazyka C# jsou dále rozděleny na *jednoduché typy*, *výčtové typy*, *typy struktury*a *typy s možnou hodnotou null*. Referenční typy jazyka C# jsou dále rozděleny do *typů tříd*, *typů rozhraní*, *typů polí*a *typů delegátů*.

Následující přehled poskytuje přehled systému typů jazyka C#.

- [Typy hodnot](../language-reference/builtin-types/value-types.md)
  - [Jednoduché typy](../language-reference/builtin-types/value-types.md#built-in-value-types)
    - [Podepsané integrály](../language-reference/builtin-types/integral-numeric-types.md): `sbyte` , `short` , `int` ,`long`
    - [Unsigned integrál](../language-reference/builtin-types/integral-numeric-types.md): `byte` , `ushort` , `uint` ,`ulong`
    - [Znaky Unicode](/dotnet/standard/base-types/character-encoding-introduction): `char` , které představují jednotku kódu UTF-16
    - [Binární bod IEEE s plovoucí desetinnou](../language-reference/builtin-types/floating-point-numeric-types.md)čárkou: `float` ,`double`
    - [Desetinná čárka s vysokou přesností](../language-reference/builtin-types/floating-point-numeric-types.md):`decimal`
    - Boolean: `bool` , která představuje logické hodnoty – hodnoty, které jsou buď `true` nebo`false`
  - [Výčtové typy](../language-reference/builtin-types/enum.md)
    - Uživatelem definované typy formuláře `enum E {...}` . `enum`Typ je odlišný typ s pojmenovanými konstantami. Každý `enum` typ má nadřízený typ, který musí být jedním z osmi integrálních typů. Sada hodnot `enum` typu je stejná jako sada hodnot základního typu.
  - [Typy struktury](../language-reference/builtin-types/struct.md)
    - Uživatelem definované typy formuláře`struct S {...}`
  - [Typy hodnot s povolenou hodnotou Null](../language-reference/builtin-types/nullable-value-types.md)
    - Rozšíření všech ostatních typů hodnot s `null` hodnotou
  - [Typy hodnot řazené kolekce členů](../tuples.md)
    - Uživatelem definované typy formuláře`(T1, T2, ...)`
- [Odkazové typy](../language-reference/keywords/reference-types.md)
  - [Typy tříd](../language-reference/keywords/class.md)
    - Nejvyšší základní třída všech ostatních typů:`object`
    - [Řetězce Unicode](/dotnet/standard/base-types/character-encoding-introduction): `string` , které představují posloupnost jednotek kódu UTF-16
    - Uživatelem definované typy formuláře`class C {...}`
  - [Typy rozhraní](../language-reference/keywords/interface.md)
    - Uživatelem definované typy formuláře`interface I {...}`
  - [Typy polí](../programming-guide/arrays/index.md)
    - Jednoduché a multidimenzionální a zubaté, například, `int[]` `int[,]` a`int[][]`
  - [Typy delegátů](../language-reference/keywords/delegate.md)
    - Uživatelem definované typy formuláře`delegate int D(...)`

Programy v jazyce C# používají *deklarace typů* k vytváření nových typů. Deklarace typu Určuje název a členy nového typu. Pět kategorií typů v jazyce C# je uživatelsky definované: typy tříd, typy struktury, typy rozhraní, výčtové typy a typy delegátů.

- `class`Typ definuje datovou strukturu obsahující datové členy (pole) a členy funkce (metody, vlastnosti a další). Typy tříd podporují jednu dědičnost a polymorfismus, mechanismy, které mohou odvozené třídy roztáhnout a specializovat základní třídy.
- `struct`Typ je podobný typu třídy v tom, že představuje strukturu s datovými členy a členy funkce. Nicméně na rozdíl od tříd, struktury jsou typy hodnot a obvykle nevyžadují přidělení haldy. Typy struktury nepodporují uživatelem zadanou dědičnost a všechny typy struktury implicitně dědí z typu `object` .
- `interface`Typ definuje kontrakt jako pojmenovanou sadu veřejných členů. `class`Nebo `struct` , který implementuje, `interface` musí poskytnout implementace členů rozhraní. `interface`Může dědit z více základních rozhraní a `class` nebo `struct` může implementovat více rozhraní.
- `delegate`Typ představuje odkazy na metody s konkrétním seznamem parametrů a návratovým typem. Delegáti umožňují zacházet s metodami jako s entitami, které lze přiřadit proměnným a předávat jako parametry. Delegáti jsou analogické jako typy funkcí poskytované funkčními jazyky. Jsou také podobné konceptu ukazatelů funkcí nalezených v některých jiných jazycích. Na rozdíl od ukazatelů na funkce jsou delegáti objektově orientovaný a typově bezpečný.

`class`Typy, `struct` , `interface` a `delegate` podporují obecné typy, na jejichž základě lze parametry používat s jinými typy.

Jazyk C# podporuje jedno a multidimenzionální pole libovolného typu. Na rozdíl od typů uvedených výše nemusí být typy polí deklarovány dříve, než mohou být použity. Místo toho jsou typy polí konstruovány pomocí názvu typu s hranatými závorkami. Například je jednorozměrné pole `int[]` `int` , `int[,]` je dvourozměrné pole a je jednorozměrné pole jednorozměrného pole `int` `int[][]` nebo "zubaté" pole typu) `int` .

Typy s možnou hodnotou null nevyžadují samostatnou definici. Pro každý typ, který nepovoluje hodnotu null `T` , existuje odpovídající typ s možnou hodnotou null `T?` , který může obsahovat další hodnotu, `null` . Například `int?` je typ, který může obsahovat libovolné 32 celé číslo nebo hodnotu `null` a `string?` je typ, který může obsahovat libovolnou `string` hodnotu nebo `null` .

Systém typů jazyka C# je sjednocením, aby hodnota libovolného typu mohla být považována za `object` . Každý typ v jazyce C# přímo nebo nepřímo je odvozen z `object` typu třídy a `object` je nejvyšší základní třídou všech typů. Hodnoty typů odkazů se považují za objekty pouhým zobrazením hodnot jako typu `object` . Hodnoty typů hodnot se považují za objekty prováděním operací *zabalení* a *rozbalení*. V následujícím příkladu `int` je hodnota převedena na `object` a zpět na `int` .

:::code language="csharp" source="./snippets/shared/Program.cs" ID="boxing" :::

Při přiřazení hodnoty typu hodnoty k `object` odkazu je "pole" přiděleno pro uchování hodnoty. Toto pole je instancí typu odkazu a hodnota je zkopírována do tohoto pole. Naopak, pokud `object` je odkaz přetypování na typ hodnoty, je provedena kontrolu, že odkazovaná `object` je pole správného typu hodnoty. Pokud je ověření úspěšné, je hodnota v poli zkopírována na typ hodnoty.

Sjednocený Typový systém v jazyce C# znamená, že typy hodnot jsou považovány za `object` odkazy na vyžádání. Z důvodu sjednocení, knihovny pro obecné účely, které používají typ, `object` lze použít se všemi typy odvozenými z `object` , včetně typů odkazů a typů hodnot.

V jazyce C# existuje několik druhů *proměnných* , včetně polí, prvků pole, místních proměnných a parametrů. Proměnné reprezentují umístění úložiště. Každá proměnná má typ, který určuje, jaké hodnoty mohou být uloženy v proměnné, jak je znázorněno níže.

- Typ hodnoty, která není null
  - Hodnota, která má přesný typ
- Typ hodnoty s možnou hodnotou null
  - `null`Hodnota nebo hodnota daného přesného typu
- object
  - `null`Odkaz, odkaz na objekt libovolného typu odkazu, nebo odkaz na zabalenou hodnotu libovolného typu hodnoty
- Typ třídy
  - `null`Odkaz, odkaz na instanci tohoto typu třídy nebo odkaz na instanci třídy odvozené z tohoto typu třídy
- Typ rozhraní
  - `null`Odkaz, odkaz na instanci typu třídy, která implementuje tento typ rozhraní, nebo odkaz na zabalenou hodnotu typu hodnoty, který implementuje tento typ rozhraní
- Typ pole
  - `null`Odkaz, odkaz na instanci tohoto typu pole nebo odkaz na instanci kompatibilního typu pole
- Typ delegáta
  - `null`Odkaz nebo odkaz na instanci kompatibilního typu delegáta

## <a name="program-structure"></a>Struktura programu

Klíčovou organizační koncepcí v jazyce C# jsou [***programy***](../programming-guide/inside-a-program/index.md), [***obory názvů***](../programming-guide/namespaces/index.md), [***typy***](../programming-guide/types/index.md), [***členy***](../programming-guide/classes-and-structs/members.md)a [***sestavení***](../../standard/assembly/index.md). Programy deklarují typy, které obsahují členy a mohou být uspořádány do oborů názvů. Příklady typů jsou třídy, struktury a rozhraní. Příklady členů jsou pole, metody, vlastnosti a události. Když jsou programy C# kompilovány, jsou fyzicky zabaleny do sestavení. Sestavení mají obvykle příponu souboru `.exe` nebo v `.dll` závislosti na tom, zda implementují ***aplikace*** nebo ***knihovny***, v uvedeném pořadí.

Jako malý příklad zvažte sestavení, které obsahuje následující kód:

:::code language="csharp" source="./snippets/shared/AcmeStack.cs":::

Plně kvalifikovaný název této třídy je `Acme.Collections.Stack` . Třída obsahuje několik členů: pole s názvem `top` , dvě metody pojmenované `Push` a a `Pop` vnořená třída s názvem `Entry` . `Entry`Třída dále obsahuje tři členy: pole s názvem `next` , pole s názvem `data` a konstruktor. `Stack`Je *Obecná* třída. Má jeden parametr typu, `T` který je nahrazen konkrétním typem, když je použit.

> [!NOTE]
> *Zásobník* je kolekce "first in-last-out" (filo). Do horní části zásobníku jsou přidány nové prvky. Když je prvek odebrán, je odebrán z horní části zásobníku.

Sestavení obsahují spustitelný kód ve formě instrukcí pro převodní jazyk (IL) a symbolické informace ve formě metadat. Předtím, než se spustí, kompilátor JIT (just-in-time) prostředí .NET Common Language Runtime převede kód IL v sestavení na kód specifický pro procesor.

Vzhledem k tomu, že sestavení je samo-popisující jednotku funkcí obsahující kód i metadata, není nutné `#include` direktivy a hlavičkové soubory v jazyce C#. Veřejné typy a členy obsažené v konkrétním sestavení jsou zpřístupněny v programu v jazyce C# pouhým odkazováním na toto sestavení při kompilování programu. Například tento program používá `Acme.Collections.Stack` třídu ze `acme.dll` sestavení:

:::code language="csharp" source="./snippets/shared/StackUsage.cs":::

Pro zkompilování tohoto programu byste se museli *odkazovat* na sestavení obsahující třídu zásobníku definovanou v předchozím příkladu.

Programy v jazyce C# mohou být uloženy v několika zdrojových souborech. Při kompilaci programu v jazyce C# jsou všechny zdrojové soubory zpracovávány společně a zdrojové soubory mohou volně odkazovat na sebe. V koncepčním případě je to, že všechny zdrojové soubory byly před zpracováním sloučeny do jednoho velkého souboru. Předávací deklarace nejsou v jazyce C# nikdy potřeba, protože s malým počtem výjimek je pořadí deklarací nedůležité. C# neomezuje zdrojový soubor na deklaraci pouze jednoho veřejného typu, ani nevyžaduje název zdrojového souboru, aby odpovídal typu deklarovanému ve zdrojovém souboru.

Další články v této prohlídce vysvětlují tyto organizační bloky.

>[!div class="step-by-step"]
>[Další](types.md)
