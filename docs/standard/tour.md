---
title: Prohlídka technologie .NET
description: Průvodce prostřednictvím některé viditelného funkce .NET.
author: cartermp
ms.author: wiwagn
ms.date: 05/22/2017
ms.technology: dotnet-standard
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
ms.openlocfilehash: f9b4e3d885725afc4181256e02e3b174318e3ece
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931550"
---
# <a name="tour-of-net"></a>Prohlídka technologie .NET

.NET je platforma pro vývoj pro obecné účely. Má několik klíčových funkcí, jako třeba podporu pro více programovacích jazyků, asynchronní a souběžné programovacích modelů a nativní interoperabilita umožňující širokou škálu scénářů napříč různými platformami.

Tento článek nabízí prohlídku s průvodcem prostřednictvím některé z klíčových funkcí rozhraní .NET. Zobrazit [Architekturálních komponentách .NET](components.md) tématu, dozvíte se o architektuře části .NET a co slouží pro.

## <a name="how-to-run-the-code-samples"></a>Spuštění ukázky kódu

Zjistěte, jak nastavit vývojové prostředí ke spuštění ukázky kódu, najdete v článku [Začínáme](get-started.md) tématu. Zkopírujte a vložte do vašeho prostředí ke spuštění je ukázky kódu z této stránky. 

## <a name="programming-languages"></a>Programovací jazyky

.NET podporuje více programovacích jazyků. Implementace .NET implementovat [společné jazykové infrastruktury (CLI)](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/), které mimo jiné určuje nezávislým na jazyku modulu runtime a jazyk interoperability. To znamená, že zvolíte kterémkoli jazyce platformy .NET k vytváření aplikací a služeb na rozhraní .NET.

Microsoft aktivně vyvíjí a podporuje tři různé jazyky .NET: C#, F # a Visual Basic (VB). 

* C# je jednoduchý, výkonný, typově bezpečný a objektově orientované, při zachování expresivity a elegance jazyků stylu. Každý, kdo zná podobné jazyky C a zjistí, několik problémů s přizpůsobením jazyka C#. Podívejte se [průvodce v C#](../csharp/index.md) Další informace o jazyce C#.

* F # je multiplatformní, funkcionální programovací jazyk, který podporuje také tradičního objektově orientované a imperativní programování. Podívejte se [Průvodce jazykem F #](../fsharp/index.md) Další informace o jazyce F #.

* Visual Basic je snadné jazykové informace, které umožňují vytvářet různé aplikace, které běží na rozhraní .NET. Mezi jazyky .NET syntaxe jazyka Visual Basic se nejvíc blíží běžné lidské jazyka, často usnadnění pro osoby, nový přístup k vývoji softwaru.

## <a name="automatic-memory-management"></a>Automatická správa paměti

Používá .NET [uvolňování paměti (GC)](garbagecollection/index.md) poskytnout Automatická správa paměti pro programy. Uvolňování paměti pracuje opožděné přístup ke správě paměti přednost propustnost aplikace okamžitě kolekce paměti. Další informace o uvolňování paměti .NET, přečtěte si [základy kolekce paměti (GC)](garbagecollection/fundamentals.md).

Následující dva řádky obou přidělení paměti:

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L1-L2)]

Neexistuje žádné obdobná – klíčové slovo pro zrušení přidělení částí paměti, jak vyhovělo dojde automaticky při uvolňování paměti prostřednictvím jeho plánovaného spuštění.

Uvolňování paměti je jedna ze služeb, které pomáhají zajistit *bezpečnost paměti*. Program je bezpečné, pokud přistupuje k paměti pouze přidělené paměti. Pro instanci modul runtime zaručuje, že aplikace nebude připojit volné paměti za hranice pole.

V následujícím příkladu, modul runtime vyvolá `InvalidIndexException` výjimky k vynucení bezpečnost paměti:

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

## <a name="working-with-unmanaged-resources"></a>Práce s nespravovanými prostředky

Některé objekty odkaz *nespravovaných prostředků*. Nespravované prostředky jsou prostředky, které nejsou spravovány automaticky modul .NET runtime. Například popisovač souboru je nespravovaný prostředek. A <xref:System.IO.FileStream> spravovaných objektů, ale odkazuje na popisovač souboru, který nespravované. Až budete mít pomocí <xref:System.IO.FileStream>, budete muset uvolnění popisovače souboru.

V rozhraní .NET, objekty, které odkazují na nespravované prostředky implementovat <xref:System.IDisposable> rozhraní. Po dokončení používání objektu, volání objektu <xref:System.IDisposable.Dispose> metodu, která je zodpovědná za uvolnění všech nespravovaných prostředků. Jazyky .NET poskytují pohodlnou `using` syntaxe pro objekty, jak je znázorněno v následujícím příkladu:

[!code-csharp[UnmanagedResources](../../samples/csharp/snippets/tour/UnmanagedResources.csx#L1-L6)]

Jednou `using` blok dokončení, modulu runtime .NET automaticky volá `stream` objektu <xref:System.IDisposable.Dispose> metodu, která uvolní popisovač souboru. Modul runtime také to dělá proto pokud výjimky způsobí, že ovládací prvek opustit blok.

Další podrobnosti naleznete v následujících tématech:

* Pro jazyk C#, najdete v článku [using – příkaz (referenční dokumentace jazyka C#)](../csharp/language-reference/keywords/using-statement.md) tématu.
* F #, najdete v části [Správa prostředků: klíčové slovo use](../fsharp/language-reference/resource-management-the-use-keyword.md).
* VB, najdete v článku [pomocí – příkaz (Visual Basic)](../visual-basic/language-reference/statements/using-statement.md) tématu.

## <a name="type-safety"></a>Bezpečnost typů

Objekt je instance určitého typu. Jsou povoleny pro daný objekt pouze operace jeho typu. A `Dog` typ může mít `Jump` a `WagTail` metody, ale ne `SumTotal` metody. Program jen volá metody, které patří do daného typu. Všechna ostatní volání za následek chybu kompilace nebo výjimce za běhu (v případě použití dynamické funkce nebo `object`).

Jazyky rozhraní .NET jsou objektově orientované s hierarchiemi základní a odvozené třídy. Modul runtime rozhraní .NET umožňuje pouze objekt přetypování a volání, které odpovídají hierarchii objektů. Mějte na paměti, že každý typ definovaný v kterémkoli jazyce platformy .NET je odvozena od základní třídy <xref:System.Object> typu.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L19-L23)]

Bezpečnost typů slouží také k podpoře vynucení zapouzdření zaručením věrnost klíčová slova přistupujícího objektu. Přístupový objekt klíčová slova jsou artefakty, které řídí přístup k členům daného typu jiným kódem. Ty se obvykle používají pro různé druhy dat v rámci typu, které se používají ke správě své chování.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L3-L3)]

C#, VB a F # podporují místní *odvození typu*. Odvození typu znamená, že kompilátor odvodí typ výrazu na levé straně z výrazu na pravé straně. To neznamená, že je bezpečnost typů narušený, případně jim vyhnout. Výsledný typ nemá silný typ se vším, který zahrnuje. Z předchozího příkladu `dog` je přepsán zavést odvození typu proměnné a zbytek v příkladu je beze změny:

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L28-L34)]

F # obsahuje i další typ odvození funkce než pro odvození typu metoda – místní, v C# a VB. Další informace najdete v tématu [odvození typu](../fsharp/language-reference/type-inference.md).

## <a name="delegates-and-lambdas"></a>Delegáty a výrazy lambda

Delegát je reprezentován podpis metody. Jakoukoli metodou s podpis delegátu lze přiřadit a je spuštěn, když je vyvolán delegát.

Delegáti jsou ukazatelům funkcí jazyka C++ s tím rozdílem, že jsou to typově bezpečné. Jsou to druh odpojené metody v rámci systému typů CLR. Běžné metody jsou připojeny k třídy a jsou pouze přímo volat statickou nebo volání metody instance konvence.

V rozhraní .NET se delegáti běžně používají v obslužných rutinách událostí, při definování asynchronních operací a v lambda výrazech, které jsou základním kamenem LINQ. Další informace najdete v [delegáty a výrazy lambda](delegates-lambdas.md) tématu.

## <a name="generics"></a>Obecné typy

Obecné typy umožňují programátorovi, aby zavést *parametr typu* při navrhování jejich třídy, které umožňuje určit přesný typ, který má použít místo parametru typu kódu klienta (uživatelé typu).

Obecné typy byly přidány umožňující programátorům implementovat obecných datových struktur. Před jejich přijetí v pořadí pro typ, jako `List` typ je obecný, by musel pracovat s prvky, které byly typu `object`. To mělo různých výkonu a sémantické problémy, spolu s možné drobným běhové chyby. Většina notorious ten je datová struktura obsahuje například celá čísla a řetězce a `InvalidCastException` je vyvolána na práci s členy v seznamu.

Následující příklad ukazuje základní program spuštěný pomocí instance <xref:System.Collections.Generic.List%601> typy:

[!code-csharp[GenericsShort](../../samples/csharp/snippets/tour/GenericsShort.csx)]

Další informace najdete v tématu [obecné typy (Obecné) přehled](generics.md) tématu.

## <a name="async-programming"></a>Asynchronní programování

Asynchronní programování je prvotřídní koncept v .NET s asynchronní podpory v modulu runtime, knihoven rozhraní framework, a vytvoří jazyk .NET. Interně jsou založené na objekty (například `Task`), který využít operačního systému jako efektivně provádět vstupně-výstupní úlohy.

Další informace o asynchronním programování v rozhraní .NET, začínat [asynchronní přehled](async.md) tématu.

## <a name="language-integrated-query-linq"></a>Language Integrated Query (LINQ)

LINQ je výkonnou sadu funkcí pro C# a VB, které umožňují napsat jednoduchý a deklarativní kód pro provozování na datech. Data mohou být v mnoha formách (například objektů v paměti, databázi SQL nebo dokument XML), ale kód LINQ, který napíšete obvykle není ve zdroji dat lišit.

Další informace a některé ukázky, najdete v článku [LINQ (Language Integrated Query)](using-linq.md) tématu.

## <a name="native-interoperability"></a>Nativní interoperabilita

Každý operační systém zahrnuje aplikaci programovací rozhraní (API), která poskytuje služby systému. .NET poskytuje několik způsobů, jak volat tato rozhraní API.

Hlavní způsob, jak provést nativní Interoperabilita je prostřednictvím "vyvolání platformy" nebo P/Invoke zkráceně, který není podporovaný napříč platformami operačních systémů Linux a Windows. Jen pro Windows způsob, jak to nativní interoperabilita se označuje jako "COM interop", který se používá pro práci s [komponenty modelu COM](/cpp/atl/introduction-to-com) ve spravovaném kódu. Je nástavbou P/Invoke infrastruktury, ale funguje to trochu různými způsoby.

Podobně stojí většina vzájemná funkční spolupráce podpora pro Mono (a tedy Xamarinu pro) pro Javu a Objective-C, to znamená, že použít stejné zásady.

Další informace o nativní interoperabilita v [nativní interoperabilita](native-interop.md) tématu.

## <a name="unsafe-code"></a>Nezabezpečený kód

V závislosti na podpoře jazyka CLR vám umožní přístup k nativním paměti a provedení aritmetické operace ukazatele přes `unsafe` kódu. Tyto operace jsou potřeba určité algoritmy a vzájemná funkční spolupráce systému. I když výkonné, použití nezabezpečeného kódu se nedoporučuje, pokud je potřeba komunikace pomocí rozhraní API systému nebo implementovat nejúčinnější algoritmus. Nezabezpečený kód nelze spustit stejným způsobem jako v různých prostředích a také dojde ke ztrátě výhod systému uvolňování paměti a bezpečnost typů. Doporučujeme omezit a centralizovat co nejvíc nezabezpečený kód a důkladně otestujte, že kód.

V následujícím příkladu je upravená verze `ToString()` metodu z `StringBuilder` třídy. Ukazuje, jak pomocí `unsafe` kódu můžete efektivně implementovat algoritmus tak bloky paměti přímo:

[!code-csharp[Unsafe](../../samples/csharp/snippets/tour/Unsafe.csx)]

## <a name="next-steps"></a>Další kroky

Pokud vás zajímá prohlídku funkcí jazyka C#, přečtěte si [Tour z jazyka C#](../csharp/tour-of-csharp/index.md).

Pokud vás zajímá prohlídku funkcí F #, přečtěte si téma [Tour F #](../fsharp/tour.md).

Pokud chcete začít s psaním kódu vlastní, navštivte [Začínáme](get-started.md).

Další informace o důležité součásti aplikace .NET, přečtěte si [Architekturálních komponentách .NET](components.md).
