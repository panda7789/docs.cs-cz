---
title: Generování a využívání asynchronních datových proudů
description: Tento rozšířený kurz znázorňuje scénáře, kdy generování a využívání asynchronních streamů poskytuje přirozenější způsob práce s posloupnosti dat, která se dají vygenerovat asynchronně.
ms.date: 02/10/2019
ms.technology: csharp-async
ms.custom: mvc
ms.openlocfilehash: 412e5de5d9d73846fe2af36e3def383364389c75
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039226"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>Kurz: generování a využívání asynchronních datových C# proudů pomocí 8,0 a .net Core 3,0

C#8,0 zavádí **asynchronní streamy**, které modelují zdroj dat streamování, když mohou být prvky v datovém proudu načteny nebo generovány asynchronně. Asynchronní streamy spoléhají na nová rozhraní zavedená v .NET Standard 2,1 a implementovaná v rozhraní .NET Core 3,0 za účelem poskytnutí přirozeného programovacího modelu pro zdroje dat pro asynchronní streamování.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Vytvořte zdroj dat, který generuje posloupnost datových prvků asynchronně.
> - Spotřebujte tento zdroj dat asynchronně.
> - Rozpoznat, kdy je nové rozhraní a zdroj dat upřednostňováno na dřívější synchronní sekvence dat.

## <a name="prerequisites"></a>Požadavky

Musíte nastavit počítač tak, aby běžel .NET Core, včetně kompilátoru C# 8,0. Kompilátor C# 8 je k dispozici počínaje [verzí Visual Studio 2019 verze 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download).

Budete muset vytvořit [přístupový token GitHubu](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) , abyste mohli získat přístup ke koncovému bodu GraphQL GitHubu. Pro přístupový token GitHubu vyberte následující oprávnění:

- úložiště: stav
- public_repo

Uložte přístupový token na bezpečném místě, abyste ho mohli použít k získání přístupu ke koncovému bodu rozhraní API GitHubu.

> [!WARNING]
> Udržujte svůj osobní přístupový token zabezpečený. Libovolný software s vaším osobním přístupovým tokenem by mohl volat rozhraní API GitHubu pomocí vašich přístupových práv.

V tomto kurzu se předpokládá, že C# máte zkušenosti s platformou a .NET, včetně sady Visual Studio nebo .NET Core CLI.

## <a name="run-the-starter-application"></a>Spuštění aplikace Starter

Kód pro úvodní aplikaci použitou v tomto kurzu můžete získat z našeho úložiště [dotnet/Samples](https://github.com/dotnet/samples) ve složce [CSharp/tutorials/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/start) .

Úvodní aplikace je Konzolová aplikace, která používá rozhraní [GitHub GraphQL](https://developer.github.com/v4/) k načtení nedávných problémů napsaných v úložišti [dotnet/docs](https://github.com/dotnet/docs) . Začněte tím, že si vyhledáte následující kód pro úvodní aplikaci `Main` metodu:

[!code-csharp[StarterAppMain](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#StarterAppMain)]

Můžete buď nastavit proměnnou prostředí `GitHubKey` na váš osobní přístupový token, nebo můžete nahradit poslední argument ve volání `GenEnvVariable` pomocí vašeho osobního přístupového tokenu. Pokud uložíte zdroj s ostatními nebo pokud ho umístíte do sdíleného zdrojového úložiště, neumísťujte do zdrojového kódu svůj přístupový kód.

Po vytvoření klienta GitHub kód v `Main` vytvoří objekt vytváření sestav o průběhu a token zrušení. Po vytvoření těchto objektů `Main` voláním `runPagedQueryAsync` načíst nejnovější 250 vytvořené problémy. Po dokončení této úlohy se zobrazí výsledky.

Při spuštění aplikace Starter můžete provést několik důležitých pozorování, jak se tato aplikace spouští.  Uvidíte průběh nahlášený pro každou stránku vrácenou z GitHubu. Můžete sledovat, že se pozastavená pauza ještě před tím, než GitHub vrátí všechny nové stránky problémů. A konečně problémy se zobrazí až po načtení všech 10 stránek z GitHubu.

## <a name="examine-the-implementation"></a>Kontrola implementace

Implementace odhalí, proč jste pozorováni chování popsané v předchozí části. Projděte si kód pro `runPagedQueryAsync`:

[!code-csharp[RunPagedQueryStarter](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#RunPagedQuery)]

Pojďme se soustředit na algoritmus stránkování a asynchronní strukturu předchozího kódu. (Podrobnosti o rozhraních API GitHub GraphQL najdete v [dokumentaci k GitHubu GraphQL](https://developer.github.com/v4/guides/) .) Metoda `runPagedQueryAsync` vytvoří výčet problémů od nejnovějších k nejstarší. Vyžádá 25 problémů na stránku a prověřuje `pageInfo` struktury odpovědi, aby pokračovaly na předchozí stránce. To sleduje standardní podporu stránkování GraphQL pro reakce na vícestránkové stránky. Odpověď obsahuje objekt `pageInfo`, který obsahuje hodnotu `hasPreviousPages` a hodnotu `startCursor`, která se používá k vyžádání předchozí stránky. Problémy se nacházejí v poli `nodes`. Metoda `runPagedQueryAsync` připojí tyto uzly k poli, které obsahuje všechny výsledky ze všech stránek.

Po načtení a obnovení stránky výsledků `runPagedQueryAsync` nahlásí průběh a kontrolují zrušení. Pokud je požadováno zrušení, `runPagedQueryAsync` vyvolá <xref:System.OperationCanceledException>.

Tento kód obsahuje několik prvků, které lze zlepšit. Nejdůležitější je, `runPagedQueryAsync` musí přidělit úložiště pro všechny vrácené problémy. Tato ukázka zastaví problémy 250, protože načtení všech otevřených problémů by vyžadovalo mnohem více paměti pro uložení všech načtených problémů. Navíc protokoly pro podporu pokroku a podpory zrušení usnadňují pochopení algoritmu při prvním čtení. Chcete-li zjistit, kde je zaznamenán průběh, je nutné vyhledat třídu Progress. Také je nutné trasovat komunikaci prostřednictvím <xref:System.Threading.CancellationTokenSource> a její přidružené <xref:System.Threading.CancellationToken>, abyste pochopili, kde je požadováno zrušení a kde je uděleno.

## <a name="async-streams-provide-a-better-way"></a>Asynchronní streamy poskytují lepší způsob

Asynchronní streamy a přidružená jazyková podpora řeší všechna tyto aspekty. Kód, který generuje sekvenci, teď může použít `yield return` k vrácení prvků v metodě, která byla deklarována pomocí modifikátoru `async`. Asynchronní datový proud můžete využívat pomocí `await foreach` smyčky stejným způsobem jako jakoukoli sekvenci pomocí `foreach` smyčky.

Tyto nové funkce jazyka závisí na třech nových rozhraních přidaných do .NET Standard 2,1 a implementovaná v rozhraní .NET Core 3,0:

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

Tato tři rozhraní by měla být obeznámena C# s většinou pro vývojáře. Chovají se způsobem podobným jejich synchronním protějškům:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

Jeden typ, který může být neznámý, je <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>. Struktura `ValueTask` poskytuje podobné rozhraní API pro třídu <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>. `ValueTask` se v těchto rozhraních používají z důvodů výkonu.

## <a name="convert-to-async-streams"></a>Převést na asynchronní proudy

Dále převeďte metodu `runPagedQueryAsync` pro vygenerování asynchronního datového proudu. Nejprve změňte podpis `runPagedQueryAsync` a vraťte `IAsyncEnumerable<JToken>` a odeberte token zrušení a objekty průběhu ze seznamu parametrů, jak je znázorněno v následujícím kódu:

[!code-csharp[FinishedSignature](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#UpdateSignature)]

Počáteční kód zpracuje každou stránku při načtení stránky, jak je znázorněno v následujícím kódu:

[!code-csharp[StarterPaging](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#ProcessPage)]

Nahraďte tyto tři řádky následujícím kódem:

[!code-csharp[FinishedPaging](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#YieldReturnPage)]

Můžete také odebrat deklaraci `finalResults` dříve v této metodě a příkaz `return`, který následuje za smyčkou, kterou jste změnili.

Dokončili jste změny pro vygenerování asynchronního datového proudu. Metoda Finish by měla vypadat podobně jako následující kód:

[!code-csharp[FinishedGenerate](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#GenerateAsyncStream)]

Dále změníte kód, který používá kolekci ke využívání asynchronního datového proudu. V `Main`, který zpracovává kolekci problémů, vyhledejte následující kód:

[!code-csharp[EnumerateOldStyle](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#EnumerateOldStyle)]

Nahraďte tento kód následující `await foreach` smyčce:

[!code-csharp[FinishedEnumerateAsyncStream](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#EnumerateAsyncStream)]

Kód pro dokončený kurz můžete získat z úložiště [dotnet/Samples](https://github.com/dotnet/samples) ve složce [CSharp/tutorials/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/finished) .

## <a name="run-the-finished-application"></a>Spuštění dokončené aplikace

Spusťte aplikaci znovu. Kontrastujte své chování s chováním úvodní aplikace. První stránka výsledků je vyhodnocena, jakmile bude k dispozici. Je možné, že při každém vyžádání a načtení každé nové stránky dojde k pozastavení, takže se výsledky další stránky rychle vytvoří. Blok `catch` `try`  /  není nutné ke zpracování zrušení: volající může zastavit výčet kolekce. Průběh je jasně nahlášený, protože asynchronní datový proud generuje výsledky při stažení každé stránky. Stav každého vráceného problému je bez problémů zahrnutý ve smyčce `await foreach`. K sledování průběhu nepotřebujete objekt zpětného volání.

Vylepšení využití paměti můžete zobrazit zkoumáním kódu. Již nemusíte přidělovat kolekci pro uložení všech výsledků před jejich výčtem. Volající může určit, jak se mají výsledky využívat, a pokud je potřeba kolekce úložiště.

Spouštějte počáteční i hotové aplikace a můžete sledovat rozdíly mezi implementacemi pro sebe. Přístupový token GitHubu, který jste vytvořili po spuštění tohoto kurzu, můžete odstranit po dokončení tohoto kurzu. Pokud útočník získal přístup k tomuto tokenu, měl by získat přístup k rozhraním API GitHubu pomocí vašich přihlašovacích údajů.
