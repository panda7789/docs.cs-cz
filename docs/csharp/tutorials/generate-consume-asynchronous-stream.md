---
title: Generování a využívání asynchronních datových proudů
description: Tento pokročilý kurz ilustruje scénáře, kde generování a využívání asynchronních datových proudů poskytuje přirozenější způsob práce s sekvencemi dat, které mohou být generovány asynchronně.
ms.date: 02/10/2019
ms.technology: csharp-async
ms.custom: mvc
ms.openlocfilehash: de090eb9cc1e8b511956313ab5169ee4d07a492f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156737"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>Kurz: Generování a využívání asynchronních datových proudů pomocí c# 8.0 a .NET Core 3.0

C# 8.0 zavádí **asynchronní proudy**, které modelují zdroj datových proudů, když mohou být prvky v datovém proudu načteny nebo generovány asynchronně. Asynchronní proudy spoléhají na nová rozhraní zavedená v rozhraní .NET Standard 2.1 a implementovaná v rozhraní .NET Core 3.0, aby poskytla přirozený programovací model pro asynchronní zdroje dat streamování.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Vytvořte zdroj dat, který generuje posloupnost datových prvků asynchronně.
> - Spotřebovávat tento zdroj dat asynchronně.
> - Rozpoznat, kdy nové rozhraní a zdroj dat jsou upřednostňovány před starší synchronní datové sekvence.

## <a name="prerequisites"></a>Požadavky

Budete muset nastavit počítač pro spuštění .NET Core, včetně kompilátoru C# 8.0. Kompilátor Jazyka C# 8 je k dispozici počínaje [sadou Visual Studio 2019 verze 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).

Budete muset vytvořit [přístupový token GitHubu,](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) abyste měli přístup ke koncovému bodu GitHub GraphQL. Vyberte následující oprávnění pro přístupový token GitHubu:

- repo:stav
- public_repo

Uložte přístupový token na bezpečném místě, abyste ho mohli použít k získání přístupu ke koncovému bodu rozhraní API GitHub.

> [!WARNING]
> Udržujte svůj osobní přístupový token v bezpečí. Jakýkoli software s vaším osobním přístupovým tokenem může volat rozhraní GitHub API pomocí vašich přístupových práv.

Tento kurz předpokládá, že jste obeznámeni s C# a .NET, včetně Visual Studio nebo .NET Core CLI.

## <a name="run-the-starter-application"></a>Spuštění startovací aplikace

Můžete získat kód pro počáteční aplikace použité v tomto kurzu z [našeho úložiště dotnet/samples](https://github.com/dotnet/samples) ve složce [csharp/tutorials/AsyncStreams.](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/start)

Počáteční aplikace je konzolová aplikace, která používá rozhraní [GitHub GraphQL](https://developer.github.com/v4/) k načtení nedávných problémů napsaných v úložišti [dotnet/docs.](https://github.com/dotnet/docs) Začněte tím, že se podíváte na následující kód pro metodu počáteční aplikace: `Main`

[!code-csharp[StarterAppMain](~/samples/snippets/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#StarterAppMain)]

Můžete buď nastavit `GitHubKey` proměnnou prostředí na váš osobní přístupový token, nebo `GenEnvVariable` můžete nahradit poslední argument ve volání s vaším osobním přístupovým tokenem. Nevkládejte přístupový kód do zdrojového kódu, pokud budete zdroj ukládat s ostatními nebo jej ukládat do sdíleného zdrojového úložiště.

Po vytvoření klienta GitHub `Main` kód v vytvoří objekt hlášení průběhu a token zrušení. Po vytvoření těchto `Main` objektů `runPagedQueryAsync` volání načíst posledních 250 vytvořených problémů. Po dokončení tohoto úkolu se zobrazí výsledky.

Při spuštění počáteční aplikace, můžete provést některé důležité poznámky o tom, jak tato aplikace běží.  Uvidíte průběh hlášené pro každou stránku vrácenou z GitHubu. Můžete sledovat znatelnou pauzu, než GitHub vrátí každou novou stránku problémů. Nakonec se problémy zobrazí až po načtení všech 10 stránek z GitHubu.

## <a name="examine-the-implementation"></a>Prozkoumat provádění

Implementace odhaluje, proč jste pozorovali chování popsané v předchozí části. Zkontrolujte kód `runPagedQueryAsync`pro :

[!code-csharp[RunPagedQueryStarter](~/samples/snippets/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#RunPagedQuery)]

Soustřeďme se na stránkovací algoritmus a asynchronní strukturu předchozího kódu. (Podrobnosti o rozhraní API GitHub GraphQL najdete v dokumentaci k [rozhraní GitHub](https://developer.github.com/v4/guides/) GraphQL.) Metoda `runPagedQueryAsync` vyjmenovává problémy od nejnovějších po nejstarší. Požaduje 25 otázek na stránku `pageInfo` a zkoumá strukturu odpovědi pokračovat s předchozí stránku. To vyplývá graphql standardní stránkování podporu pro vícestránkové odpovědi. Odpověď obsahuje `pageInfo` objekt, který `hasPreviousPages` obsahuje `startCursor` hodnotu a hodnotu použitou k vyžádání předchozí stránky. Problémy jsou `nodes` v poli. Metoda `runPagedQueryAsync` připojí tyto uzly k poli, které obsahuje všechny výsledky ze všech stránek.

Po načtení a obnovení stránky `runPagedQueryAsync` výsledků, hlásí průběh a kontroly zrušení. Pokud bylo požadováno `runPagedQueryAsync` zrušení, <xref:System.OperationCanceledException>vyvolá .

Existuje několik prvků v tomto kódu, které lze zlepšit. A co `runPagedQueryAsync` je nejdůležitější, musí přidělit úložiště pro všechny vrácené problémy. Tato ukázka se zastaví na 250 problémy, protože načítání všech otevřených problémů by vyžadovalo mnohem více paměti pro uložení všech načtených problémů. Kromě toho protokoly pro podporu pokroku a podporu zrušení algoritmus těžší pochopit na jeho první čtení. Musíte vyhledat třídu průběhu a zjistit, kde je hlášen průběh. Musíte také sledovat komunikaci prostřednictvím <xref:System.Threading.CancellationTokenSource> a <xref:System.Threading.CancellationToken> jeho přidružené pochopit, kde je požadováno zrušení a kde je uděleno.

## <a name="async-streams-provide-a-better-way"></a>Asynchronní proudy poskytují lepší způsob

Asynchronní proudy a související jazyková podpora řeší všechny tyto obavy. Kód, který generuje sekvence nyní `yield return` můžete použít k vrácení prvků `async` v metodě, která byla deklarována s modifikátorem. Můžete konzumovat asynchronní `await foreach` datový proud pomocí smyčky stejně jako spotřebovávají libovolné sekvence pomocí `foreach` smyčky.

Tyto nové jazykové funkce závisí na třech nových rozhraních, která jsou přidána do standardu .NET Standard 2.1 a implementována v rozhraní .NET Core 3.0:

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

Tato tři rozhraní by měla být známá většině vývojářů jazyka C#. Chovají se podobně jako jejich synchronní protějšky:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

Jeden typ, který může <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>být neznámý, je . `ValueTask` Struktura poskytuje podobné rozhraní API <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídy. `ValueTask`se používá v těchto rozhraních z důvodů výkonu.

## <a name="convert-to-async-streams"></a>Převod na asynchronní datové proudy

Dále převeďte metodu `runPagedQueryAsync` a vygenerujte asynchronní datový proud. Nejprve změňte `runPagedQueryAsync` podpis pro `IAsyncEnumerable<JToken>`vrácení a odeberte objekty tokenu zrušení a průběhu ze seznamu parametrů, jak je znázorněno v následujícím kódu:

[!code-csharp[FinishedSignature](~/samples/snippets/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#UpdateSignature)]

Počáteční kód zpracovává každou stránku při načítání stránky, jak je znázorněno v následujícím kódu:

[!code-csharp[StarterPaging](~/samples/snippets/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#ProcessPage)]

Nahraďte tyto tři řádky následujícím kódem:

[!code-csharp[FinishedPaging](~/samples/snippets/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#YieldReturnPage)]

Můžete také odebrat `finalResults` prohlášení dříve v `return` této metodě a příkaz, který následuje za smyčky, kterou jste upravili.

Dokončili jste změny pro generování asynchronního datového proudu. Hotová metoda by se měla podobat níže uvedenému kódu:

[!code-csharp[FinishedGenerate](~/samples/snippets/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#GenerateAsyncStream)]

Dále změníte kód, který spotřebovává kolekce využívat asynchronní datový proud. V tomto zpracuje tekutou kolekci problémů následující kód: `Main`

[!code-csharp[EnumerateOldStyle](~/samples/snippets/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#EnumerateOldStyle)]

Nahraďte tento `await foreach` kód následující smyčkou:

[!code-csharp[FinishedEnumerateAsyncStream](~/samples/snippets/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#EnumerateAsyncStream)]

Ve výchozím nastavení jsou prvky datového proudu zpracovány v zachyceném kontextu. Pokud chcete zakázat zachycení kontextu, použijte <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> metodu rozšíření. Další informace o kontextech synchronizace a zachycení aktuálního kontextu naleznete v článku o [využití asynchronního vzoru založeného na úlohách](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

Můžete získat kód pro hotový kurz z [úložiště dotnet/samples](https://github.com/dotnet/samples) ve složce [csharp/tutorials/AsyncStreams.](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/finished)

## <a name="run-the-finished-application"></a>Spuštění dokončené aplikace

Spusťte aplikaci znovu. Porovnejte jeho chování s chováním počáteční aplikace. První stránka výsledků je uveden, jakmile je k dispozici. Je tu pozorovatelné pauza jako každá nová stránka je požadována a načtena, pak další stránka výsledky jsou rychle vyčísleny. `try`  /  Blok `catch` není potřeba ke zpracování zrušení: volající můžete zastavit výčet kolekce. Průběh je jasně hlášena, protože asynchronní datový proud generuje výsledky jako každá stránka je stažena. Stav pro každý vrácený problém je `await foreach` hladce součástí smyčky. Ke sledování průběhu nepotřebujete objekt zpětného volání.

Můžete zobrazit zlepšení využití paměti kontrolou kódu. Již není nutné přidělit kolekci pro uložení všech výsledků před jejich výčtu. Volající můžete určit, jak spotřebovat výsledky a pokud je potřeba kolekce úložiště.

Spusťte počáteční i dokončené aplikace a můžete sledovat rozdíly mezi implementacemi pro sebe. Můžete odstranit přístupový token GitHub, který jste vytvořili při spuštění tohoto kurzu po dokončení. Pokud útočník získal přístup k tomuto tokenu, mohl by přistupovat k rozhraním API GitHub pomocí vašich přihlašovacích údajů.
