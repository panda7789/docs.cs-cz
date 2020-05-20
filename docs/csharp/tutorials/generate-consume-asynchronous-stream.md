---
title: Generování a využívání asynchronních datových proudů
description: V tomto rozšířeném kurzu se dozvíte, jak generovat a využívat asynchronní streamy. Asynchronní datové proudy poskytují přirozenější způsob práce s posloupnosti dat, která mohou být vygenerována asynchronně.
ms.date: 02/10/2019
ms.technology: csharp-async
ms.custom: mvc
ms.openlocfilehash: fd9fed3469d18c919102640df7bb501b116f5e0e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420367"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>Kurz: generování a využívání asynchronních datových proudů pomocí C# 8,0 a .NET Core 3,0

C# 8,0 zavádí **asynchronní streamy**, které modelují zdroj dat streamování. Datové proudy často načítají nebo generují prvky asynchronně. Asynchronní streamy spoléhají na nová rozhraní představená v .NET Standard 2,1. Tato rozhraní jsou podporovaná v .NET Core 3,0 a novějších verzích. Poskytují přirozený programovací model pro asynchronní streamování zdrojů dat.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Vytvořte zdroj dat, který generuje posloupnost datových prvků asynchronně.
> - Spotřebujte tento zdroj dat asynchronně.
> - Podpora zrušení a zachycených kontextů pro asynchronní datové proudy.
> - Rozpoznat, kdy je nové rozhraní a zdroj dat upřednostňováno na dřívější synchronní sekvence dat.

## <a name="prerequisites"></a>Požadavky

Musíte nastavit počítač tak, aby běžel .NET Core, včetně kompilátoru C# 8,0. Kompilátor C# 8 je k dispozici počínaje [verzí Visual Studio 2019 verze 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download).

Budete muset vytvořit [přístupový token GitHubu](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) , abyste mohli získat přístup ke koncovému bodu GraphQL GitHubu. Pro přístupový token GitHubu vyberte následující oprávnění:

- úložiště: stav
- public_repo

Uložte přístupový token na bezpečném místě, abyste ho mohli použít k získání přístupu ke koncovému bodu rozhraní API GitHubu.

> [!WARNING]
> Udržujte svůj osobní přístupový token zabezpečený. Libovolný software s vaším osobním přístupovým tokenem by mohl volat rozhraní API GitHubu pomocí vašich přístupových práv.

V tomto kurzu se předpokládá, že máte zkušenosti s jazykem C# a .NET, včetně sady Visual Studio nebo .NET Core CLI.

## <a name="run-the-starter-application"></a>Spuštění aplikace Starter

Kód pro úvodní aplikaci použitou v tomto kurzu můžete získat z úložiště [dotnet/docs](https://github.com/dotnet/docs) ve složce [CSharp/tutorials/AsyncStreams](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/snippets/generate-consume-asynchronous-streams/start) .

Úvodní aplikace je Konzolová aplikace, která používá rozhraní [GitHub GraphQL](https://developer.github.com/v4/) k načtení nedávných problémů napsaných v úložišti [dotnet/docs](https://github.com/dotnet/docs) . Začněte tím, že si vyhledáte následující kód pro `Main` metodu počáteční aplikace:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetStarterAppMain" :::

Můžete buď nastavit `GitHubKey` proměnnou prostředí na váš osobní přístupový token, nebo můžete nahradit poslední argument v volání `GenEnvVariable` pomocí tokenu vašeho osobního přístupového tokenu. Pokud budete zdroj sdílet s ostatními, neumísťujte kód pro přístup do zdrojového kódu. Nikdy Nenahrávat přístupové kódy do sdíleného zdrojového úložiště.

Po vytvoření klienta GitHub kód v `Main` vytvoří objekt vytváření sestav o průběhu a token zrušení. Po vytvoření těchto objektů `Main` volání `runPagedQueryAsync` načtou nejnovější 250 vytvořené problémy. Po dokončení této úlohy se zobrazí výsledky.

Při spuštění aplikace Starter můžete provést několik důležitých pozorování, jak se tato aplikace spouští.  Uvidíte průběh nahlášený pro každou stránku vrácenou z GitHubu. Můžete sledovat, že se pozastavená pauza ještě před tím, než GitHub vrátí všechny nové stránky problémů. A konečně problémy se zobrazí až po načtení všech 10 stránek z GitHubu.

## <a name="examine-the-implementation"></a>Kontrola implementace

Implementace odhalí, proč jste pozorováni chování popsané v předchozí části. Projděte si kód pro `runPagedQueryAsync` :

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetRunPagedQuery" :::

Pojďme se soustředit na algoritmus stránkování a asynchronní strukturu předchozího kódu. (Podrobnosti o rozhraních API GitHub GraphQL najdete v [dokumentaci k GitHubu GraphQL](https://developer.github.com/v4/guides/) .) `runPagedQueryAsync`Metoda vytvoří výčet problémů od nejnovějších k nejstarší. Vyžádá 25 problémů na stránku a prověřuje `pageInfo` strukturu odpovědi, aby pokračovala na předchozí stránce. To sleduje standardní podporu stránkování GraphQL pro reakce na vícestránkové stránky. Odpověď obsahuje `pageInfo` objekt, který obsahuje `hasPreviousPages` hodnotu a `startCursor` hodnotu použitou k vyžádání předchozí stránky. Problémy jsou v poli `nodes` . `runPagedQueryAsync`Metoda připojí tyto uzly k poli, které obsahuje všechny výsledky ze všech stránek.

Po načtení a obnovení stránky výsledků se `runPagedQueryAsync` nahlásí průběh a kontrolují zrušení. Pokud je požadováno zrušení, `runPagedQueryAsync` vyvolá výjimku <xref:System.OperationCanceledException> .

Tento kód obsahuje několik prvků, které lze zlepšit. Co je nejdůležitější, `runPagedQueryAsync` musí přidělit úložiště pro všechny vrácené problémy. Tato ukázka zastaví problémy 250, protože načtení všech otevřených problémů by vyžadovalo mnohem více paměti pro uložení všech načtených problémů. Protokoly pro podporu sestav průběhu a zrušení usnadňují pochopení algoritmu při prvním čtení. Jsou zapojeny další typy a rozhraní API. Komunikaci je nutné trasovat prostřednictvím <xref:System.Threading.CancellationTokenSource> a jejího přidruženého <xref:System.Threading.CancellationToken> k pochopení, kde je požadováno zrušení a kde je uděleno.

## <a name="async-streams-provide-a-better-way"></a>Asynchronní streamy poskytují lepší způsob

Asynchronní streamy a přidružená jazyková podpora řeší všechna tyto aspekty. Kód, který generuje sekvenci, teď může použít `yield return` k vrácení prvků v metodě, která byla deklarována s `async` modifikátorem. Asynchronní datový proud můžete využívat pomocí `await foreach` smyčky stejně, jako byste využívali jakoukoli sekvenci pomocí `foreach` smyčky.

Tyto nové funkce jazyka závisí na třech nových rozhraních přidaných do .NET Standard 2,1 a implementovaná v rozhraní .NET Core 3,0:

- <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>
- <xref:System.IAsyncDisposable?displayProperty=nameWithType>

Tato tři rozhraní by měla být obeznámena s většinou vývojářů v jazyce C#. Chovají se způsobem podobným jejich synchronním protějškům:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

Jeden typ, který může být neznámý, je <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType> . `ValueTask`Struktura poskytuje podobné rozhraní API pro <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídu. `ValueTask`se používá v těchto rozhraních z důvodů výkonu.

## <a name="convert-to-async-streams"></a>Převést na asynchronní proudy

Dále převeďte `runPagedQueryAsync` metodu pro generování asynchronního datového proudu. Nejprve změňte signaturu `runPagedQueryAsync` na, pokud chcete vrátit `IAsyncEnumerable<JToken>` , a odeberte token zrušení a objekty průběhu ze seznamu parametrů, jak je znázorněno v následujícím kódu:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetUpdateSignature" :::

Počáteční kód zpracuje každou stránku při načtení stránky, jak je znázorněno v následujícím kódu:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetProcessPage" :::

Nahraďte tyto tři řádky následujícím kódem:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetYieldReturnPage" :::

Můžete také odebrat deklaraci `finalResults` výše v této metodě a `return` příkaz, který následuje za smyčkou, kterou jste změnili.

Dokončili jste změny pro vygenerování asynchronního datového proudu. Metoda dokončená by měla vypadat podobně jako následující kód:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetGenerateAsyncStream" :::

Dále změníte kód, který používá kolekci ke využívání asynchronního datového proudu. Vyhledejte následující kód v `Main` , který zpracovává kolekci problémů:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetEnumerateOldStyle" :::

Nahraďte tento kód následujícím `await foreach` smyčkou:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetEnumerateAsyncStream" :::

Nové rozhraní <xref:System.Collections.Generic.IAsyncEnumerator%601> je odvozeno z <xref:System.IAsyncDisposable> . To znamená, že předchozí smyčka asynchronně odstraní Stream po dokončení smyčky. Můžete si představit, že smyčka vypadá jako následující kód:

```csharp
int num = 0;
var enumerator = runPagedQueryAsync(client, PagedIssueQuery, "docs").GetEnumeratorAsync();
try
{
    while (await enumerator.MoveNextAsync())
    {
        var issue = enumerator.Current;
        Console.WriteLine(issue);
        Console.WriteLine($"Received {++num} issues in total");
    }
} finally
{
    if (enumerator != null)
        await enumerator.DisposeAsync();
}
```

Ve výchozím nastavení jsou prvky Stream zpracovávány v zachyceném kontextu. Pokud chcete zakázat zachycování kontextu, použijte <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> metodu rozšíření. Další informace o kontextech synchronizace a zaznamenávání aktuálního kontextu naleznete v článku o [využívání asynchronního vzoru založeného na úlohách](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

Asynchronní streamy podporují zrušení pomocí stejného protokolu jako jiné `async` metody. Signaturu metody asynchronního iterátoru byste upravili následujícím způsobem, aby se mohla podporovat zrušení:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetGenerateWithCancellation" :::

<xref:System.Runtime.CompilerServices.EnumeratorCancellationAttribute?dipslayProperty=nameWithType>Atribut způsobí, že kompilátor vygeneruje kód pro <xref:System.Collections.Generic.IAsyncEnumerator%601> , který předává token k `GetAsyncEnumerator` viditelnosti textu asynchronního iterátoru jako tento argument. Uvnitř `runQueryAsync` byste mohli prověřit stav tokenu a v případě potřeby zrušit další práci.

<xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.WithCancellation%2A>K předání tokenu zrušení do asynchronního datového proudu použijete jinou metodu rozšíření. Provedete to tak, že se tyto problémy vyčíslují následujícím způsobem:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetEnumerateWithCancellation" :::

Kód pro dokončený kurz můžete získat z úložiště [dotnet/docs](https://github.com/dotnet/docs) ve složce [CSharp/tutorials/AsyncStreams](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/snippets/generate-consume-asynchronous-streams/finished) .

## <a name="run-the-finished-application"></a>Spuštění dokončené aplikace

Spusťte aplikaci znovu. Kontrastujte své chování s chováním úvodní aplikace. První stránka výsledků je vyhodnocena, jakmile bude k dispozici. Je možné, že při každém vyžádání a načtení každé nové stránky dojde k pozastavení, takže se výsledky další stránky rychle vytvoří. `try`  /  `catch` Blok není potřebný ke zpracování zrušení: volající může zastavit výčet kolekce. Průběh je jasně nahlášený, protože asynchronní datový proud generuje výsledky při stažení každé stránky. Stav každého vráceného problému je hladce zahrnutý ve `await foreach` smyčce. K sledování průběhu nepotřebujete objekt zpětného volání.

Vylepšení využití paměti můžete zobrazit zkoumáním kódu. Již nemusíte přidělovat kolekci pro uložení všech výsledků před jejich výčtem. Volající může určit, jak se mají výsledky využívat, a pokud je potřeba kolekce úložiště.

Spouštějte počáteční i hotové aplikace a můžete sledovat rozdíly mezi implementacemi pro sebe. Přístupový token GitHubu, který jste vytvořili po spuštění tohoto kurzu, můžete odstranit po dokončení tohoto kurzu. Pokud útočník získal přístup k tomuto tokenu, měl by získat přístup k rozhraním API GitHubu pomocí vašich přihlašovacích údajů.
