---
title: Prohlídka technologie .NET
description: Průvodce se všemi výraznými funkcemi .NET.
author: cartermp
ms.author: wiwagn
ms.date: 05/22/2017
ms.technology: dotnet-standard
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
ms.openlocfilehash: f4cd2e47da236d276a42b972265ffd1a2fe27310
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160336"
---
# <a name="tour-of-net"></a>Prohlídka technologie .NET

.NET je vývojová platforma pro obecné účely. Má několik klíčových funkcí, jako je podpora pro více programovacích jazyků, asynchronní a souběžné programovací modely a nativní interoperabilitu, která umožňuje široké spektrum scénářů napříč různými platformami.

Tento článek obsahuje průvodce s některými klíčovými funkcemi rozhraní .NET. V tématu [komponenty architektury rozhraní .NET](components.md) se dozvíte o architektonických částech .NET a o tom, k čemu se používají.

## <a name="how-to-run-the-code-samples"></a>Jak spustit ukázky kódu

Informace o tom, jak nastavit vývojové prostředí pro spuštění ukázek kódu, naleznete v tématu [Začínáme](get-started.md) . Zkopírování a vložení ukázek kódu z této stránky do vašeho prostředí, aby je bylo možné spustit.

## <a name="programming-languages"></a>Programovací jazyky

Rozhraní .NET podporuje více programovacích jazyků. Implementace rozhraní .NET implementují rozhraní [Common Language Infrastructure (CLI)](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/), které kromě jiného určuje interoperabilitu modulu runtime a jazyka nezávislého na jazyce. To znamená, že zvolíte libovolný jazyk .NET pro sestavování aplikací a služeb v rozhraní .NET.

Microsoft aktivně vyvíjí a podporuje tři jazyky .NET: C#, F#a Visual Basic.

* C#je jednoduchý, výkonný, typově bezpečný a objektově orientovaný a přitom zachovává expresivity a elegance jazyků ve stylu jazyka C. Kdokoli, kdo zná jazyk C a podobné jazyky, najde v přizpůsobení několik C#problémů. Další informace o nástroji C#najdete v [ C# příručce](../csharp/index.yml) .

* F#je programovací jazyk, který je pro více platforem, který podporuje také tradiční objekty orientované a imperativní programování. Další informace o nástroji F#najdete v [ F# příručce](../fsharp/index.yml) .

* Visual Basic je jednoduchý jazyk, pomocí kterého se naučíte vytvářet nejrůznější aplikace, které běží na .NET. V rámci jazyků .NET je syntaxe Visual Basic nejblíže běžnému lidskému jazyku, často usnadňuje lidem novému vývoji softwaru.

## <a name="automatic-memory-management"></a>Automatická správa paměti

Rozhraní .NET používá [uvolňování paměti (GC)](garbage-collection/index.md) k zajištění automatické správy paměti pro programy. GC funguje při opožděném přístupu ke správě paměti a předchází propustnosti aplikace okamžitému shromažďování paměti. Další informace o uvolňování paměti .NET najdete v tématu [základní informace o uvolňování paměti (GC)](garbage-collection/fundamentals.md).

Paměť přidělují následující dva řádky:

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L1-L2)]

Neexistuje žádné podobné klíčové slovo, které by bylo možné zrušit přidělení paměti, protože dealokace probíhá automaticky, když uvolňování paměti uvolní paměť prostřednictvím naplánovaného spuštění.

Systém uvolňování paměti je jednou ze služeb, které pomůžou zajistit *bezpečnost paměti*. Program je bezpečný pro paměť, pokud přistupuje pouze k přidělené paměti. Modul runtime například zajišťuje, že aplikace nemá přístup k nepřidělené paměti mimo hranice pole.

V následujícím příkladu vyvolá modul runtime výjimku <xref:System.IndexOutOfRangeException> pro vymáhání zabezpečení paměti:

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

## <a name="working-with-unmanaged-resources"></a>Práce s nespravovanými prostředky

Některé objekty odkazují na *nespravované prostředky*. Nespravované prostředky jsou prostředky, které nejsou automaticky spravovány modulem runtime .NET. Například popisovač souboru je nespravovaný prostředek. Objekt <xref:System.IO.FileStream> je spravovaný objekt, ale odkazuje na popisovač souboru, který je nespravovaný. Až budete s použitím <xref:System.IO.FileStream>, musíte vydávat popisovač souboru.

V rozhraní .NET objekty, které odkazují na nespravované prostředky, implementují rozhraní <xref:System.IDisposable>. Po dokončení používání objektu zavoláte <xref:System.IDisposable.Dispose> metodu objektu, která je zodpovědná za uvolnění nespravovaných prostředků. Jazyky .NET poskytují pohodlný [příkaz`using`](../csharp/language-reference/keywords/using.md) pro takové objekty, jak je znázorněno v následujícím příkladu:

[!code-csharp[UnmanagedResources](../../samples/csharp/snippets/tour/UnmanagedResources.csx#L1-L6)]

Po dokončení `using` bloku rozhraní .NET runtime automaticky zavolá metodu <xref:System.IDisposable.Dispose> objektu `stream`, která uvolní popisovač souboru. Modul runtime také provádí tuto chybu, pokud výjimka způsobí, že ovládací prvek opustí blok.

Další podrobnosti najdete v následujících tématech:

* Další C#informace naleznete v tématu [using –C# příkaz (Referenční dokumentace)](../csharp/language-reference/keywords/using-statement.md) .
* F#Informace najdete v tématu [Správa prostředků: klíčové slovo use](../fsharp/language-reference/resource-management-the-use-keyword.md).
* Visual Basic najdete v tématu [příkaz using (Visual Basic)](../visual-basic/language-reference/statements/using-statement.md) .

## <a name="type-safety"></a>Bezpečnost typů

Objekt je instance konkrétního typu. Jediné operace, které jsou povoleny pro daný objekt, jsou typu. `Dog` typ může mít metody `Jump` a `WagTail`, ale nikoli metodu `SumTotal`. Program volá pouze metody patřící k danému typu. Všechna ostatní volání mají za následek chybu při kompilaci nebo výjimku za běhu (v případě použití dynamických funkcí nebo `object`).

Jazyky .NET jsou objektově orientované s hierarchiemi základních a odvozených tříd. Modul runtime .NET povoluje pouze přetypování a volání objektů, které odpovídají hierarchii objektů. Pamatujte, že každý typ definovaný v jakémkoli jazyce .NET je odvozen ze základního typu <xref:System.Object>.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L19-L23)]

Bezpečnost typů se také používá k vymáhání zapouzdření tím, že zaručuje přesnost přístupových klíčových slov. Přístupová klíčová slova jsou artefakty, které řídí přístup ke členům daného typu jiným kódem. Ty se obvykle používají pro různé druhy dat v rámci typu, který se používá ke správě jeho chování.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L3-L3)]

C#, Visual Basic a F# podpora *odvození místního typu*. Odvození typu znamená, že kompilátor odvodit typ výrazu na levé straně z výrazu na pravé straně. To neznamená, že bezpečnost typů je přerušena nebo se nepoužívá. Výsledný typ má silný typ se všemi, který implikuje. Z předchozího příkladu je přepsána `dog` pro zavedení odvození typu a zbývající část příkladu je beze změny:

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L28-L34)]

F#má ještě další možnosti odvození typu, než odvození typu místní metody, které se C# nacházejí v a Visual Basic. Další informace najdete v tématu [odvození typu](../fsharp/language-reference/type-inference.md).

## <a name="delegates-and-lambdas"></a>Delegáty a výrazy lambda

Delegát je reprezentován signaturou metody. Jakékoli metody s tímto podpisem mohou být přiřazeny delegátovi a provedeny při vyvolání delegáta.

Delegáti jsou C++ jako ukazatelé na funkce s tím rozdílem, že jsou typově bezpečné. Jedná se o druh odpojené metody v rámci systému typů CLR. Pravidelné metody jsou připojeny ke třídě a jsou přímo volány prostřednictvím statických konvencí nebo konvencí volání instance.

V rozhraní .NET se delegáti běžně používají v obslužných rutinách událostí, při definování asynchronních operací a ve výrazech lambda, které jsou základem LINQ. Další informace najdete v tématu [Delegáti a výrazy lambda](delegates-lambdas.md) .

## <a name="generics"></a>Obecné typy

Obecné typy umožňují programátorům zavést *parametr typu* při navrhování tříd, které umožňují kódu klienta (uživatelům typu) zadat přesný typ pro použití namísto parametru typu.

Byly přidány obecné typy, které programátorům pomůžou implementovat generické datové struktury. Před jejich příchodem, aby bylo možné typ, jako je například `List` typ obecný, pracovat s prvky, které byly typu `object`. Došlo k různým výkonům a sémantickým problémům společně s možnými malými chybami v době běhu. Obvyklou chybou za běhu je, když datová struktura obsahuje, například celá čísla i řetězce a při zpracování členů seznamu je vyvolána <xref:System.InvalidCastException>.

Následující příklad ukazuje základní program spuštěný pomocí instance <xref:System.Collections.Generic.List%601>ch typů:

[!code-csharp[GenericsShort](../../samples/csharp/snippets/tour/GenericsShort.csx)]

Další informace naleznete v tématu [Obecné typy (obecné typy) – přehled](generics.md) .

## <a name="async-programming"></a>Asynchronní programování

Asynchronní programování je první třídou konceptu v rámci .NET s asynchronní podporou v konstrukcích modulu runtime, architektury a jazyka .NET. Interně jsou založeny na objektech (například `Task`), které využívají operační systém k co nejúčinnějšímu provádění úloh vázaných na vstupně-výstupní operace.

Chcete-li získat další informace o asynchronním programování v rozhraní .NET, začněte s asynchronním tématem s [přehledem](async.md) .

## <a name="language-integrated-query-linq"></a>LINQ (Language Integrated Query)

LINQ je výkonná sada funkcí pro C# a Visual Basic, která umožňuje psaní jednoduchého deklarativního kódu pro práci na datech. Data mohou být v mnoha formách (například objekty v paměti, databáze SQL nebo dokumentu XML), ale kód jazyka LINQ, který zapisujete, se obvykle neliší od zdroje dat.

Další informace a příklady naleznete v tématu [LINQ (Language Integrated Query)](using-linq.md) .

## <a name="native-interoperability"></a>Nativní interoperabilita

Každý operační systém obsahuje aplikační programovací rozhraní (API), které poskytuje systémové služby. Rozhraní .NET poskytuje několik způsobů, jak tato rozhraní API volat.

Hlavním způsobem, jak provést nativní interoperabilitu, je prostřednictvím "vyvolání platformy" nebo volání nespravovaného kódu pro krátké, které je podporováno pro platformy Linux a Windows. Způsob, jakým se jenom systém Windows provádí v nativní interoperabilitě, se označuje jako zprostředkovatel komunikace s objekty COM, který se používá pro práci s [komponentami com](/cpp/atl/introduction-to-com) ve spravovaném kódu. Je postavená na infrastruktuře volání nespravovaného systému, ale funguje v nestejném počtu různých způsobů.

Většina podpory interoperability (a tudíž Xamarin) pro jazyk Java a cíl-C je postavená podobně, to znamená, že používají stejné zásady.

Další informace o nativní interoperabilitě najdete v článku věnovaném [nativní interoperabilitě](native-interop/index.md) .

## <a name="unsafe-code"></a>Nebezpečný kód

V závislosti na jazykové podpoře vám CLR umožní přistupovat k nativní paměti a provádět aritmetické ukazatele pomocí kódu `unsafe`. Tyto operace jsou potřeba pro určité algoritmy a interoperabilitu systému. I když je efektivní použití nebezpečného kódu doporučeno, pokud není nutné pro interoperabilitu se systémovými rozhraními API nebo implementaci nejúčinnějšího algoritmu. Nezabezpečený kód nesmí provádět stejný způsob v různých prostředích a také ztratí výhody uvolňování paměti a bezpečnosti typů. Doporučuje se co nejvíc a centralizace nezabezpečeného kódu a testování kódu.

Následující příklad je upravená verze metody `ToString()` z `StringBuilder` třídy. Ukazuje, jak lze pomocí `unsafe` kódu efektivně implementovat algoritmus přesunutím kolem bloků paměti přímo:

[!code-csharp[Unsafe](../../samples/csharp/snippets/tour/Unsafe.csx)]

## <a name="next-steps"></a>Další kroky

Pokud vás zajímá prohlídka C# funkcí, Projděte si [část C#prohlídky ](../csharp/tour-of-csharp/index.md).

Pokud vás zajímá prohlídka F# funkcí, přečtěte si téma [prohlídky F# ](../fsharp/tour.md).

Pokud chcete začít psát vlastní kód, navštivte [Začínáme](get-started.md).

Pokud se chcete dozvědět o důležitých součástech rozhraní .NET, podívejte se na [komponenty architektury .NET](components.md).
