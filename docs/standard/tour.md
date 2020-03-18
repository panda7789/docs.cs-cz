---
title: Prohlídka technologie .NET
description: Prohlídka s průvodcem některými z prominentních rysů rozhraní .NET.
author: cartermp
ms.author: wiwagn
ms.date: 05/22/2017
ms.technology: dotnet-standard
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
ms.openlocfilehash: 61d4792b1f1b92dd59442ee38810da96c6cf63bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241140"
---
# <a name="tour-of-net"></a>Prohlídka technologie .NET

.NET je univerzální vývojová platforma. Má několik klíčových funkcí, jako je například podpora pro více programovacích jazyků, asynchronní a souběžné programovací modely a nativní interoperabilita, které umožňují širokou škálu scénářů na různých platformách.

Tento článek nabízí prohlídku s průvodcem některé klíčové funkce rozhraní .NET. Informace o architektonických dílech rozhraní .NET a o tom, k čemu se používají, najdete v tématu [.NET Architectural Components.](components.md)

## <a name="how-to-run-the-code-samples"></a>Jak spustit ukázky kódu

Informace o tom, jak nastavit vývojové prostředí pro spuštění ukázek kódu, najdete v tématu [Začínáme.](get-started.md) Zkopírujte a vložte ukázky kódu z této stránky do vašeho prostředí, abyste je provedli.

## <a name="programming-languages"></a>Programovací jazyky

Rozhraní .NET podporuje více programovacích jazyků. Implementace .NET [implementují common language infrastructure (CLI),](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/)která mimo jiné určuje jazykově nezávislou dobu runtime a jazykovou interoperabilitu. To znamená, že můžete zvolit libovolný jazyk .NET pro vytváření aplikací a služeb v rozhraní .NET.

Společnost Microsoft aktivně vyvíjí a podporuje tři jazyky .NET: C#, F# a Visual Basic.

* C# je jednoduchý, výkonný, typově bezpečný a objektově orientovaný, při zachování expresivity a elegance jazyků ve stylu C. Každý, kdo zná Jazyk C a podobné jazyky najde několik problémů při přizpůsobování c#. Další informace o c# najdete v [příručce C#.](../csharp/index.yml)

* F# je multiplatformní, funkční první programovací jazyk, který také podporuje tradiční objektově orientované a imperativní programování. Další informace o [f#.](../fsharp/index.yml)

* Visual Basic je snadný jazyk se dozvíte, že používáte k vytvoření různých aplikací, které běží na rozhraní .NET. Mezi jazyky .NET je syntaxe jazyka Visual Basic nejblíže běžnému lidskému jazyku, což často usnadňuje lidem, kteří jsou pro vývoj softwaru noví.

## <a name="automatic-memory-management"></a>Automatická správa paměti

Rozhraní .NET používá [uvolňování paměti (GC)](garbage-collection/index.md) k zajištění automatické správy paměti pro programy. Gc pracuje na opožděný přístup ke správě paměti, upřednostňuje propustnost aplikace na okamžité shromažďování paměti. Další informace o .NET GC, podívejte se na [základy uvolňování paměti (GC)](garbage-collection/fundamentals.md).

Následující dva řádky přidělují paměť:

[!code-csharp[MemoryManagement](../../samples/snippets/csharp/snippets/tour/MemoryManagement.csx#L1-L2)]

Neexistuje žádné analogové klíčové slovo pro de-allocate paměti, jako de-allocation se stane automaticky, když systém uvolňování paměti uvolní paměti prostřednictvím jeho naplánované spuštění.

Systém uvolňování paměti je jednou ze služeb, které pomáhají zajistit *bezpečnost paměti*. Program je bezpečný v paměti, pokud přistupuje pouze k přidělené paměti. Například za běhu zajišťuje, že aplikace nemá přístup k nepřidělené paměti mimo hranice pole.

V následujícím příkladu runtime vyvolá <xref:System.IndexOutOfRangeException> výjimku k vynucení bezpečnosti paměti:

[!code-csharp[MemoryManagement](../../samples/snippets/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

## <a name="working-with-unmanaged-resources"></a>Práce s nespravovanými zdroji

Některé objekty odkazují na *nespravované prostředky*. Nespravované prostředky jsou prostředky, které nejsou automaticky udržovány za běhu .NET. Popisovač souboru je například nespravovaný prostředek. Objekt <xref:System.IO.FileStream> je spravovaný objekt, ale odkazuje na popisovač souboru, který není spravován. Po dokončení používání aplikace <xref:System.IO.FileStream>je třeba uvolnit popisovač souboru.

V rozhraní .NET implementují rozhraní <xref:System.IDisposable> objekty, které odkazují na nespravované prostředky. Po dokončení používání objektu zavoláte <xref:System.IDisposable.Dispose> metodu objektu, která je zodpovědná za uvolnění všech nespravovaných prostředků. Jazyky .NET poskytují pro tyto objekty vhodný [ `using` příkaz,](../csharp/language-reference/keywords/using.md) jak je znázorněno v následujícím příkladu:

[!code-csharp[UnmanagedResources](../../samples/snippets/csharp/snippets/tour/UnmanagedResources.csx#L1-L6)]

Po `using` dokončení bloku, .NET runtime automaticky `stream` volá <xref:System.IDisposable.Dispose> metodu objektu, který uvolní popisovač souboru. Runtime také to, pokud výjimka způsobí, že ovládací prvek opustit blok.

Další podrobnosti naleznete v následujících tématech:

* Pro C# naleznete [pomocí prohlášení (C# Reference)](../csharp/language-reference/keywords/using-statement.md) téma.
* Informace o použití jazyka F# naleznete v tématu [Správa zdrojů: Klíčové slovo použití](../fsharp/language-reference/resource-management-the-use-keyword.md).
* V jazyce Visual Basic najdete [téma Using Statement (Visual Basic).](../visual-basic/language-reference/statements/using-statement.md)

## <a name="type-safety"></a>Bezpečnost typů

Objekt je instance určitého typu. Pouze operace povolené pro daný objekt jsou operace jeho typu. Typ `Dog` může `Jump` mít `WagTail` a metody, ale ne metodu. `SumTotal` Program volá pouze metody, které patří k danému typu. Všechna ostatní volání mají za následek chybu v době kompilace nebo výjimku `object`za běhu (v případě použití dynamických funkcí nebo ).

Jazyky .NET jsou objektově orientované s hierarchiemi základních a odvozených tříd. Runtime .NET umožňuje pouze přetypování objektů a volání, které jsou zarovnány s hierarchií objektů. Nezapomeňte, že každý typ definovaný v libovolném <xref:System.Object> jazyce .NET je odvozen od základního typu.

[!code-csharp[TypeSafety](../../samples/snippets/csharp/snippets/tour/TypeSafety.csx#L19-L23)]

Bezpečnost typů se také používá k vynucení zapouzdření tím, že zaručuje věrnost klíčových slov přistupujícího pole. Přistupující klíčová slova jsou artefakty, které řídí přístup k členům daného typu jiným kódem. Ty se obvykle používají pro různé druhy dat v rámci typu, které se používají ke správě jeho chování.

[!code-csharp[TypeSafety](../../samples/snippets/csharp/snippets/tour/TypeSafety.csx#L3-L3)]

C#, Visual Basic a F# podporují *odvození místního typu*. Odvození typu znamená, že kompilátor odvodí typ výrazu na levé straně z výrazu na pravé straně. To neznamená, že bezpečnost typů je přerušena nebo se mu vyhnout. Výsledný typ má silný typ se vším, co znamená. Z předchozího `dog` příkladu je přepsána zavést odvození typu a zbytek příkladu je beze změny:

[!code-csharp[TypeSafety](../../samples/snippets/csharp/snippets/tour/TypeSafety.csx#L28-L34)]

F# má ještě další možnosti odvození typu než odvození typu metody místní nalezené v jazyce C# a Visual Basic. Další informace najdete [v tématu Typ odvození](../fsharp/language-reference/type-inference.md).

## <a name="delegates-and-lambdas"></a>Delegáty a výrazy lambda

Delegát je reprezentován podpisem metody. Všechny metody s tímto podpisem lze přiřadit delegáta a je proveden při vyvolání delegáta.

Delegáti jsou jako ukazatele funkce Jazyka C++ s tím rozdílem, že jsou bezpečné pro daný typ. Jsou to druh odpojené metody v rámci clr typ systému. Pravidelné metody jsou připojeny ke třídě a jsou přímo volatelné pouze prostřednictvím statické nebo instance volání konvence.

V rozhraní .NET se delegáti běžně používají v obslužných rutinách událostí, při definování asynchronních operací a ve výrazech lambda, které jsou základním kamenem LINQ. Další informace najdete v tématu [Delegáti a lambdas.](delegates-lambdas.md)

## <a name="generics"></a>Obecné typy

Obecné typy umožňují programátorovi zavést *parametr typu* při navrhování jejich tříd, které umožňují kódu klienta (uživatelům typu) určit přesný typ, který má být používán místo parametru typu.

Generika byla přidána, aby programátorům pomohla implementovat obecné datové struktury. Před jejich příchodem, aby typ, `List` jako je typ, který má být obecný, `object`by musel pracovat s prvky, které byly typu . To mělo různé problémy s výkonem a sémantickým i s možnými jemnými chybami za běhu. Běžná chyba za běhu je, když datová struktura obsahuje například celá čísla <xref:System.InvalidCastException> a řetězce a je vyvolána při zpracování členů seznamu.

Následující ukázka ukazuje základní program spuštěný pomocí instance <xref:System.Collections.Generic.List%601> typů:

[!code-csharp[GenericsShort](../../samples/snippets/csharp/snippets/tour/GenericsShort.csx)]

Další informace naleznete v tématu [přehledu obecných typů (Generics).](generics.md)

## <a name="async-programming"></a>Asynchronní programování

Asynchronní programování je koncept první třídy v rámci rozhraní .NET s asynchronní podporou v modulu runtime, knihovnách architektury a konstrukcích jazyků .NET. Interně jsou založeny na objektech `Task`(například), které využívají výhod operačního systému k co nejefektivnějšímu provádění úloh vázaných na vstupně-výstupní služby.

Další informace o asynchronním programování v rozhraní .NET, začněte s tématem [Přehled asynchronní.](async.md)

## <a name="language-integrated-query-linq"></a>LINQ (Language Integrated Query)

LINQ je výkonná sada funkcí pro C# a Visual Basic, které umožňují psát jednoduchý, deklarativní kód pro práci s daty. Data mohou být v mnoha formách (například objekty v paměti, databáze SQL nebo dokument XML), ale kód LINQ, který píšete, se obvykle neliší podle zdroje dat.

Další informace a některé ukázky najdete v tématu [LINQ (Language Integrated Query).](using-linq.md)

## <a name="native-interoperability"></a>Nativní interoperabilita

Každý operační systém obsahuje rozhraní API (Application Programming Interface), které poskytuje systémové služby. Rozhraní .NET poskytuje několik způsobů volání těchto rozhraní API.

Hlavní způsob, jak udělat nativní interoperabilitu, je prostřednictvím "platforminvoke" nebo P / Invoke pro short, který je podporován na platformách Linux a Windows. Způsob nativní interoperability pouze pro systém Windows se označuje jako "interop modelu COM", který se používá pro práci s [komponentami modelu COM](/cpp/atl/introduction-to-com) ve spravovaném kódu. Je postaven na infrastruktuře P/Invoke, ale funguje nenápadně různými způsoby.

Většina mono (a tedy Xamarin) podpora interoperability pro Java a Objective-C jsou postaveny podobně, to znamená, že používají stejné principy.

Další informace o nativní interoperabilitě naleznete v článku [Nativní interoperabilita.](native-interop/index.md)

## <a name="unsafe-code"></a>Nebezpečný kód

V závislosti na jazykové podpoře umožňuje CLR přístup k nativní `unsafe` paměti a aritmetické ukazatele prostřednictvím kódu. Tyto operace jsou potřebné pro určité algoritmy a interoperabilitu systému. Přestože je použití nebezpečného kódu výkonné, nedoporučuje se, pokud není nutné interop s systémovými api nebo implementovat nejúčinnější algoritmus. Nebezpečný kód nemusí spustit stejným způsobem v různých prostředích a také ztrácí výhody systému uvolňování paměti a bezpečnost typů. Doporučujeme omezit a centralizovat nebezpečný kód co nejvíce a důkladně otestovat tento kód.

Následující příklad je upravená `ToString()` verze metody `StringBuilder` z třídy. Ukazuje, jak `unsafe` pomocí kódu můžete efektivně implementovat algoritmus přesunutím bloky paměti přímo:

[!code-csharp[Unsafe](../../samples/snippets/csharp/snippets/tour/Unsafe.csx)]

## <a name="next-steps"></a>Další kroky

Máte-li zájem o prohlídku funkcí jazyka C#, podívejte se na [prohlídku jazyka C#](../csharp/tour-of-csharp/index.md).

Pokud máte zájem o prohlídku funkcí F#, podívejte se [na prohlídku F#](../fsharp/tour.md).

Pokud chcete začít psát vlastní kód, navštivte [stránku Začínáme](get-started.md).

Další informace o důležitých součástech rozhraní .NET naleznete v části [.NET Architectural Components](components.md).
