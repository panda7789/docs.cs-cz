---
title: Generování a asynchronní datové proudy
description: V tomto kurzu pokročilé znázorňuje scénáře, kdy generování a využívání asynchronní datové proudy poskytuje přirozenější způsob, jak pracovat s posloupností dat, která může být generována asynchronně.
ms.date: 02/10/2019
ms.custom: mvc
ms.openlocfilehash: 0fa7c778ca9ce0f0124fcc520dd4de65f2f92ea8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308546"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>Kurz: Vygenerování a zpracování datových proudů asynchronní pomocí C# 8.0 a .NET Core 3.0

C#8.0 představuje **asynchronní datové proudy**, který model streamování zdroj dat, pokud prvky v datovém proudu může načíst nebo generována asynchronně. Spolehněte se na nové rozhraní zavedené v .NET Standard 2.1 a implementovat v .NET Core 3.0 zajištění přirozené programovací model pro asynchronního streamování zdroje dat asynchronní datové proudy.

V tomto kurzu se dozvíte jak:

> [!div class="checklist"]
> * Vytvořte zdroj dat, který generuje sekvenci prvků data asynchronně.
> * Tento zdroj dat spotřebovat asynchronně.
> * Rozpoznat nové rozhraní a zdroje dat jsou upřednostňované dříve synchronní data sekvencí.

## <a name="prerequisites"></a>Požadavky

Budete muset nastavit počítač pro spuštění .NET Core, včetně C# 8.0 beta verze kompilátoru. C# Je k dispozici od verze 8 beta verze kompilátoru [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), nebo si prohlédnout nejnovější [preview SDK .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0). Asynchronní datové proudy jsou nejprve k dispozici v rozhraní .NET Core 3.0 ve verzi preview 1.

Budete muset vytvořit [přístupový token Githubu](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) tak, aby vám může přístup ke koncovému bodu GraphQL Githubu. Vyberte následující oprávnění pro váš Token přístupu Githubu:

- repo:status
- public_repo

Uložte přístupový token na bezpečném místě, ve kterém můžete získat přístup ke koncovému bodu rozhraní API Githubu.

> [!WARNING]
> Zabezpečit svůj osobní přístupový token. Veškerý software s svůj osobní přístupový token může volat rozhraní API Githubu pomocí vašimi přístupovými právy.

Tento kurz předpokládá, že jste obeznámeni s C# a .NET, včetně sady Visual Studio nebo rozhraní příkazového řádku .NET Core.

## <a name="run-the-starter-application"></a>Spuštění aplikace starter

Můžete získat kód pro Startovní aplikace použité v tomto kurzu z našich [dotnet/samples](https://github.com/dotnet/samples) úložiště v [csharp/kurzy/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/start) složky.

Startovní aplikace je konzolová aplikace, která používá [Githubu GraphQL](https://developer.github.com/v4/) rozhraní k načtení poslední problémy, které jsou napsané v [dotnet/docs](https://github.com/dotnet/docs) úložiště. Začněte zobrazením následující kód pro úvodní aplikaci `Main` metody:

[!code-csharp[StarterAppMain](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#StarterAppMain)]

Můžete buď nastaven `GitHubKey` proměnnou prostředí pro svůj osobní přístupový token, nebo můžete nahradit posledním argumentem ve volání `GenEnvVariable` s svůj osobní přístupový token. Neumisťujte přístupový kód ve zdrojovém kódu Pokud budete se ukládání zdroji s ostatními, nebo jej v úložišti sdílené zdroje.

Po vytvoření klienta Githubu, kód v `Main` vytvoří průběh vytváření sestav objektu a token zrušení. Po vytvoření těchto objektů `Main` volání `runPagedQueryAsync` načíst posledních 250 vytvořili problémy. Po dokončení této úlohy se zobrazí výsledky.

Při spuštění aplikace starter, můžete provést některé důležité skutečnosti o tom, jak tato aplikace funguje.  Zobrazí se průběh pro každou stránku vrácená z Githubu. Patrné pozastavení můžete sledovat, před vrácením každou novou stránku problémy Githubu. A konečně problémy se zobrazí až po všech 10 stránek byly načteny z Githubu.

## <a name="examine-the-implementation"></a>Vyzkoušení implementace

Implementace odhalí důvod, proč jste zaznamenali chování popsané v předchozí části. Zkontrolujte kód pro `runPagedQueryAsync`:

[!code-csharp[RunPagedQueryStarter](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#RunPagedQuery)]

Pojďme se soustředit na stránkování algoritmus a asynchronní konstrukce předchozí kód. (Můžete konzultovat [dokumentace Githubu GraphQL](https://developer.github.com/v4/guides/) podrobnosti o rozhraní API Githubu GraphQL.) `runPagedQueryAsync` Metoda výčet problémů od nejnovější po nejstarší. Požaduje 25 problémy na jedné stránce a zkoumá `pageInfo` struktura odpovědi a pokračujte na předchozí stránku. Který sleduje GraphQL na standardní podporu stránkování pro více stránek odpovědí. Odpověď obsahuje `pageInfo` objekt, který zahrnuje `hasPreviousPages` hodnotu a `startCursor` hodnota používaná pro požádání o na předchozí stránku. Tyto problémy jsou v `nodes` pole. `runPagedQueryAsync` Metoda přidá tyto uzly na pole, která obsahuje všechny výsledky ze všech stránek.

Po načtení a obnovení stránku výsledků, `runPagedQueryAsync` hlásí průběh a kontroluje zrušení. Pokud bylo vyžádáno zrušení, `runPagedQueryAsync` vyvolá <xref:System.OperationCanceledException>.

Existuje několik elementů v tento kód, který se může zlepšit. Co je nejdůležitější `runPagedQueryAsync` musí přidělit úložiště pro všechny problémy, které jsou vráceny. Tato ukázka se zastaví na 250 problémy vzhledem k tomu, že načítání všech otevřených problémů by vyžadoval víc paměti pro ukládání všechny načtené problémy. Kromě toho protokoly pro podporu průběh a podporuje zrušení znesnadnit algoritmus pochopit na jeho nejprve přečíst. Je třeba najít třídu průběh najít, kde hlášení. Budete také muset trasování komunikace prostřednictvím <xref:System.Threading.CancellationTokenSource> spolu s přidruženými <xref:System.Threading.CancellationToken> pochopit, kde je požadováno zrušení a je-li poskytnuta.

## <a name="async-streams-provide-a-better-way"></a>Asynchronní datové proudy poskytují lepší způsob

Asynchronní datové proudy a přiřazená jazyková podpora řeší všechny tyto aspekty. Teď můžete použít kód, který generuje sekvenci `yield return` vrátit prvky v metodě, která byla deklarována pomocí `async` modifikátor. Můžete využívat na asynchronní datový proud pomocí `await foreach` smyčky, stejně jako využívat jakékoli pořadí pomocí `foreach` smyčky.

Tyto nové funkce jazyka závisí na třech nových rozhraní přidány do .NET Standard 2.1 a implementovat v .NET Core 3.0:

```csharp
namespace System.Collections.Generic
{
    public interface IAsyncEnumerable<out T>
    {
        IAsyncEnumerator<T> GetAsyncEnumerator(CancellationToken cancellationToken = default);
    }

    public interface IAsyncEnumerator<out T> : IAsyncDisposable
    {
        T Current { get; }

        ValueTask<bool> MoveNextAsync();
    }
}

namespace System
{
    public interface IAsyncDisposable
    {
        ValueTask DisposeAsync();
    }
}
```

Tyto tři rozhraní by měl být většina C# vývojáři. Chovají se podobně jako jejich protějšky v synchronním způsobem:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

Jeden typ, který může být obeznámeni se <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>. `ValueTask` Struktury poskytuje podobné rozhraní API k <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídy. `ValueTask` se používá v těchto rozhraní z důvodů výkonu.

## <a name="convert-to-async-streams"></a>Převést na asynchronní datové proudy

V dalším kroku převést `runPagedQueryAsync` metoda ke generování na asynchronní datový proud. Nejprve změňte podpis `runPagedQueryAsync` se vraťte `IAsyncEnumerable<JToken>`a zrušení tokenu a průběh objekty odebrat ze seznamu parametrů, jak je znázorněno v následujícím kódu:

[!code-csharp[FinishedSignature](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#UpdateSignature)]

Počáteční kód zpracovává každé stránce jako se stránka načte, jak je znázorněno v následujícím kódu:

[!code-csharp[StarterPaging](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#ProcessPage)]

Tyto tři řádky nahraďte následujícím kódem:

[!code-csharp[FinishedPaging](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#YieldReturnPage)]

Můžete také odebrat deklaraci `finalResults` výše v této metodě a `return` příkazu, který následuje smyčky změnil.

Dokončili jste změny Generovat asynchronní proud. Dokončená metoda by se mělo podobat následujícím kódem:

[!code-csharp[FinishedGenerate](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#GenerateAsyncStream)]

V dalším kroku změníte kód, který využívá kolekce, kterou chcete používat asynchronní datový proud. Následující kód, který v `Main` , která zpracovává sadu problémy:

[!code-csharp[EnumerateOldStyle](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#EnumerateOldStyle)]

Nahraďte kód následujícím kódem `await foreach` smyčka:

[!code-csharp[FinishedEnumerateAsyncStream](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#EnumerateAsyncStream)]

Můžete získat kód pro dokončení kurzu z [dotnet/samples](https://github.com/dotnet/samples) úložiště v [csharp/kurzy/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/finished) složky.

## <a name="run-the-finished-application"></a>Spusťte dokončenou aplikaci

Spusťte aplikaci znovu. Porovnejte své chování s chováním Startovní aplikace. První stránka výsledků je vypočten, jakmile je k dispozici. Každá nová stránka je požadováno a načíst je pozorovatelných pozastavit a potom rychle vytvořit výčet další stránky výsledků. `try`  /  `catch` Bloku není potřeba ke zpracování zrušení: volající zastavit vyčíslení kolekce. Jasně hlášení vzhledem k tomu, že asynchronní datový proud generuje výsledky stažené každou stránku.

Uvidíte zdokonalení využití paměti porovnáním kód. Už nemusíte přidělit kolekce pro ukládání všech výsledků, předtím, než jste výčtu. Volající můžete určit, jak využívat výsledky a pokud je zapotřebí úložiště kolekce.

Spustit počáteční i hotové aplikace a můžete sledovat rozdílů mezi implementacemi sami. Můžete odstranit přístupový token Githubu, který jste vytvořili při spuštění v tomto kurzu po dokončení. Pokud útočník získal přístup do tohoto tokenu, může přístup k rozhraní API Githubu pomocí svých přihlašovacích údajů.
