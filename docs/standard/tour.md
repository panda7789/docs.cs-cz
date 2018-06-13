---
title: Přehled používání rozhraní .NET
description: Průvodce pomocí některé z hlavní funkce .NET.
author: cartermp
ms.author: wiwagn
ms.date: 05/22/2017
ms.technology: dotnet-standard
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
ms.openlocfilehash: b1925397fb7cad5e55f992feaa5be2e2d837aac8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592259"
---
# <a name="tour-of-net"></a>Přehled používání rozhraní .NET

Rozhraní .NET je platforma pro vývoj pro obecné účely. Má několik klíčových funkcí, jako je podpora pro více programovacích jazyků, asynchronní a souběžných programovací modely a nativní interoperabilita umožňující širokou škálu scénářů napříč různými platformami.

Tento článek nabízí průvodce prostřednictvím některé klíčové funkce .NET. Najdete v článku [součástí architektury .NET](components.md) tématu, dozvíte se o architektury součásti rozhraní .NET a co se používají pro.

## <a name="how-to-run-the-code-samples"></a>Postup spuštění ukázky kódu

Zjistěte, jak nastavit vývojové prostředí pro spouštění ukázky kódu, najdete v článku [Začínáme](get-started.md) tématu. Zkopírujte a vložte do vašeho prostředí je spuštění ukázky kódu z této stránky. 

## <a name="programming-languages"></a>Programovací jazyky

Rozhraní .NET podporuje více programovacích jazyků. Implementace rozhraní .NET implementovat [společné jazykové infrastruktury (CLI)](https://www.visualstudio.com/license-terms/ecma-c-common-language-infrastructure-standards/), která kromě jiných věcí určuje nezávislé na jazyku runtime a jazyk interoperability. To znamená, že zvolíte kterémkoli jazyce platformy .NET k vytváření aplikací a služeb na rozhraní .NET.

Microsoft aktivně vyvíjí a podporuje tři jazyky rozhraní .NET: C#, F # a Visual Basic (VB). 

* C# je jednoduché, výkonné, bezpečnost typů a objektově orientované, a přitom zachovat expressiveness a eleganci jazyků C-style. Každý, kdo obeznámeni s podobnou jazyky C a vyhledá několik problémy s přizpůsobením jazyka C#. Podívejte se [průvodce v C#](../csharp/index.md) Další informace o C#.

* F # je napříč platformami, funkční programovací jazyk, který taky podporuje tradiční objektově orientované a imperativní programování. Podívejte se [Průvodce F #](../fsharp/index.md) Další informace o F #.

* Visual Basic je snadno jazyk informace, že použijete k sestavení celou řadu aplikací, které běží na rozhraní .NET. Mezi jazyky rozhraní .NET je nejblíže k obyčejnou lidského jazyk často usnadnit pro osoby pro vývoj softwaru nové syntaxe jazyka Visual Basic.

## <a name="automatic-memory-management"></a>Automatická správa paměti

Používá rozhraní .NET [uvolňování paměti (GC)](garbagecollection/index.md) zajistit Automatická správa paměti pro programy. Globální Katalog funguje na opožděné přístup ke správě, paměti, upřednostňují propustnost aplikace ke kolekci okamžitou paměti. Další informace o .NET GC, podívejte se na [základy uvolnění paměti (GC)](garbagecollection/fundamentals.md).

Následující dva řádky obou přidělit paměť:

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L1-L2)]

Neexistuje žádné podobá – klíčové slovo zrušte přidělit paměť, protože deaktivace přidělení dojde automaticky při uvolňování paměti získá paměti prostřednictvím její naplánované spuštění.

Uvolňování paměti je jedna ze služeb, které pomůžou zajistit *bezpečnost paměti*. Program je bezpečné, pokud přistupuje k paměti pouze přidělené paměti. Modul runtime pro instanci zajišťuje, aby aplikace nemá přístup k volné paměti za hranice pole.

V následujícím příkladu, modul runtime vyvolá `InvalidIndexException` výjimka vynutit zabezpečení paměti:

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

## <a name="working-with-unmanaged-resources"></a>Práce s nespravovaných prostředků

Některé objekty odkaz *nespravovaných prostředků*. Nespravované prostředky jsou prostředky, které nejsou spravovány automaticky modulem runtime rozhraní .NET. Popisovač souboru je například nespravovaných prostředků. A <xref:System.IO.FileStream> spravovaných objektů, ale odkazuje na popisovače souboru, který nebude spravován. Po dokončení pomocí <xref:System.IO.FileStream>, budete potřebovat uvolnit popisovač souboru.

V rozhraní .NET, objekty, které odkazují na nespravované prostředky implementovat <xref:System.IDisposable> rozhraní. Po dokončení pomocí objektu, volání objektu <xref:System.IDisposable.Dispose> metodu, která je zodpovědná za uvolnění jakýchkoli nespravovaných prostředků. Zadejte jazyky rozhraní .NET pohodlnou `using` syntaxe pro objekty, jak je znázorněno v následujícím příkladu:

[!code-csharp[UnmanagedResources](../../samples/csharp/snippets/tour/UnmanagedResources.csx#L1-L6)]

Jednou `using` blok dokončení, modul runtime rozhraní .NET automaticky vyvolá `stream` objektu <xref:System.IDisposable.Dispose> metodu, která uvolní popisovač souboru. Modul runtime také tomu Pokud ovládací prvek chcete nechat bloku způsobí výjimku.

Další podrobnosti naleznete v následujících tématech:

* Pro jazyk C#, najdete v článku [using – příkaz (referenční dokumentace jazyka C#)](../csharp/language-reference/keywords/using-statement.md) tématu.
* F #, najdete v části [Správa prostředků: klíčové slovo use](../fsharp/language-reference/resource-management-the-use-keyword.md).
* VB, najdete v článku [pomocí – příkaz (Visual Basic)](../visual-basic/language-reference/statements/using-statement.md) tématu.

## <a name="type-safety"></a>Zabezpečení typů

Objekt je instance určitého typu. Jenom operace, které jsou povolené pro daný objekt se jeho typu. A `Dog` může mít typ `Jump` a `WagTail` metody ale ne `SumTotal` metoda. Program pouze volá metody, které patří do daného typu. Jiná volání za následek chyby kompilace nebo výjimka běhu (v případě použití dynamické funkcí nebo `object`).

Jazyky rozhraní .NET jsou objektově orientované s hierarchií základní a odvozené třídy. Modul runtime rozhraní .NET umožňuje pouze objekt přetypování a volání, které zarovnané s hierarchie objektů. Mějte na paměti, každý typ definované v kterémkoli jazyce platformy .NET, pochází z základní <xref:System.Object> typu.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L19-L23)]

Zabezpečení typů se také používá tak, aby vynutitelné zapouzdření podle zaručit přesnost klíčová slova přistupujícího objektu. Klíčová slova přistupujícího objektu se o artefakty, které řízení přístupu ke členům daného typu jiným kódem. Ty se obvykle používají pro různé typy dat v rámci typu, která se používají ke správě své chování.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L3-L3)]

C#, VB a F # podpora místní *odvození typu*. Odvození typu znamená, že kompilátor deduces typ výraz na levé straně z výrazu na pravé straně. To neznamená, že je poškozený nebo vyhnout bezpečnost typů. Výsledný typ mít s všechno silné typ, který znamená. Z předchozího příkladu `dog` a `cat` jsou přepsaná zavádět odvození typu a zbytek v příkladu se neliší:

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L28-L34)]

F # má i další možnosti odvození typu než odvození typu metoda místní nalezených v C# a VB. Další informace najdete v tématu [odvození typu](../fsharp/language-reference/type-inference.md).

## <a name="delegates-and-lambdas"></a>Delegáti a lambdas

Delegát je reprezentována podpis metody. Jakékoli metody této podpisem lze přiřadit k delegát a je proveden při vyvolání delegáta.

Delegáti jsou jako ukazatelů na funkce C++ s tím rozdílem, že jsou bezpečné typu. Jsou druh odpojené metoda v rámci systému typu CLR. Běžné metody jsou připojené k třídu a jsou pouze přímo volány prostřednictvím statické nebo volání instance konvence.

V rozhraní .NET delegáti běžně se používají v obslužné rutiny událostí, definování asynchronních operací a v lambda – výrazy, které jsou kamenem LINQ. Další informace v [Delegáti a lambdas](delegates-lambdas.md) tématu.

## <a name="generics"></a>Obecné typy

Obecné typy povolit programátorů zavádět *parametr typu* při navrhování jejich tříd, které umožňuje určit typ přesný používejte místo parametr typu kód klienta (uživatelé typu).

Obecné typy byla přidána k programátory implementovat obecné datové struktury. Před jejich přijetí v pořadí pro typ, jako `List` typ, který má být obecný, by musel pracovat s prvky, které byly typu `object`. To mělo různé výkonu a sémantické problémy, společně s chyby možné jemně za běhu. Většina notorious z k tomu je datová struktura obsahuje například celá čísla i řetězce a `InvalidCastException` je vyvolána o práci se členy v seznamu.

Následující příklad ukazuje základní program spuštěný pomocí instance <xref:System.Collections.Generic.List%601> typy:

[!code-csharp[GenericsShort](../../samples/csharp/snippets/tour/GenericsShort.csx)]

Další informace najdete v tématu [obecné typy (Obecné) – přehled](generics.md) tématu.

## <a name="async-programming"></a>Asynchronní programování

Asynchronní programování je první třídy koncept v rámci .NET asynchronní podpora v modulu runtime knihoven, a vytvoří jazyce platformy .NET. Interně založených na objekty (například `Task`), který využít výhod operačního systému na co možná nejefektivnější provádět I/čítači úlohy.

Další informace o asynchronní programování v rozhraní .NET, začínat [přehled asynchronních](async.md) tématu.

## <a name="language-integrated-query-linq"></a>Jazyk integrovaného dotazu (LINQ)

LINQ je výkonnou sadu funkcí pro C# a VB, které vám umožní napsat jednoduchý a deklarativní kód pro provoz na data. Data mohou být v mnoha formulářích (například objekty v paměti, databázi SQL nebo dokument XML), ale není zdrojem dat liší LINQ kód, který obvykle napíšete.

Další informace a zobrazit některé ukázky, najdete v článku [LINQ (Language integrovaného dotazu)](using-linq.md) tématu.

## <a name="native-interoperability"></a>Nativní interoperabilita

Každý operační systém, zahrnuje programovací rozhraní aplikace (API), která poskytuje systémových služeb. Rozhraní .NET poskytuje několik způsobů, jak volat těchto rozhraní API.

Hlavní způsob k provedení nativní Interoperabilita je prostřednictvím "vyvolání platformy" nebo P/Invoke pro zkrácení, která je podporována mezi platformami, Linux a Windows. Pouze pro systém Windows způsob, jakým způsobem nativní interoperabilita se označuje jako "COM interoperabilita", který se používá pro práci s [COM – součásti](/cpp/atl/introduction-to-com) ve spravovaném kódu. Je postavená na infrastruktuře P/Invoke, ale funguje trochu různými způsoby.

Většina na Mono (a proto je Xamarin) podpory interoperability Java a jazyka Objective-C jsou vytvořeny podobně, to znamená, že použít stejné zásady.

Další informace o nativní interoperabilita v [nativní interoperabilita](native-interop.md) tématu.

## <a name="unsafe-code"></a>Nezabezpečený kód

V závislosti na podpoře jazyka modulu CLR vám umožní přístup k paměti nativní a provést aritmetika ukazatele prostřednictvím `unsafe` kódu. Tyto operace jsou potřebné pro určité algoritmů a interoperability systému. I když výkonné, použití nezabezpečený kód se nedoporučuje, pokud je potřeba Interoperabilita s rozhraní API systému nebo implementovat algoritmus maximální efektivitou. Nezabezpečený kód nemusí spustit stejným způsobem jako v různých prostředích a také ztratí výhody systém uvolňování paměti a bezpečnost typů. Se doporučuje omezit a centralizovat co nejvíce nezabezpečený kód a důkladně otestovat tento kód.

Následující příklad je upravenou verzi `ToString()` metoda z `StringBuilder` třídy. Ukazuje, jak pomocí `unsafe` kódu můžete efektivně implementovat algoritmus přímo přesunutím kolem bloky paměti:

[!code-csharp[Unsafe](../../samples/csharp/snippets/tour/Unsafe.csx)]

## <a name="next-steps"></a>Další kroky

Pokud vás zajímá prohlídku funkcí jazyka C#, podívejte se na [prohlídka z jazyka C#](../csharp/tour-of-csharp/index.md).

Pokud vás zajímá prohlídku funkcí F #, přečtěte si téma [prohlídka z F #](../fsharp/tour.md).

Pokud chcete začít vytvářet kód vlastní, navštivte [Začínáme](get-started.md).

Další informace o důležité součásti rozhraní .NET, podívejte se na [součástí architektury .NET](components.md).
