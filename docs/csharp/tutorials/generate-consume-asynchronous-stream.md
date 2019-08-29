---
title: Generování a využívání asynchronních datových proudů
description: Tento rozšířený kurz znázorňuje scénáře, kdy generování a využívání asynchronních streamů poskytuje přirozenější způsob práce s posloupnosti dat, která se dají vygenerovat asynchronně.
ms.date: 02/10/2019
ms.custom: mvc
ms.openlocfilehash: cd1159c139f2c885eacf55b8577bea9e79bf0d7a
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105855"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>Kurz: Generování a využívání asynchronních datových C# proudů pomocí 8,0 a .net Core 3,0

C#8,0 zavádí **asynchronní streamy**, které modelují zdroj dat streamování, když mohou být prvky v datovém proudu načteny nebo generovány asynchronně. Asynchronní streamy spoléhají na nová rozhraní zavedená v .NET Standard 2,1 a implementovaná v rozhraní .NET Core 3,0 za účelem poskytnutí přirozeného programovacího modelu pro zdroje dat pro asynchronní streamování.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> - Vytvořte zdroj dat, který generuje posloupnost datových prvků asynchronně.
> - Spotřebujte tento zdroj dat asynchronně.
> - Rozpoznat, kdy je nové rozhraní a zdroj dat upřednostňováno na dřívější synchronní sekvence dat.

## <a name="prerequisites"></a>Požadavky

Musíte nastavit počítač tak, aby běžel .NET Core, včetně kompilátoru C# 8,0 beta. Kompilátor C# 8 beta je k dispozici od verze [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)nebo nejnovější [sady .NET Core 3,0 Preview SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0). Asynchronní streamy jsou první dostupné v .NET Core 3,0 Preview 1.

Budete muset vytvořit [přístupový token GitHubu](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) , abyste mohli získat přístup ke koncovému bodu GraphQL GitHubu. Pro přístupový token GitHubu vyberte následující oprávnění:

- repo:status
- public_repo

Uložte přístupový token na bezpečném místě, abyste ho mohli použít k získání přístupu ke koncovému bodu rozhraní API GitHubu.

> [!WARNING]
> Udržujte svůj osobní přístupový token zabezpečený. Libovolný software s vaším osobním přístupovým tokenem by mohl volat rozhraní API GitHubu pomocí vašich přístupových práv.

V tomto kurzu se předpokládá, že C# máte zkušenosti s platformou a .NET, včetně sady Visual Studio nebo .NET Core CLI.

## <a name="run-the-starter-application"></a>Spuštění aplikace Starter

Kód pro úvodní aplikaci použitou v tomto kurzu můžete získat z našeho úložiště [dotnet/Samples](https://github.com/dotnet/samples) ve složce [CSharp/tutorials/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/start) .

Úvodní aplikace je Konzolová aplikace, která používá rozhraní [GitHub GraphQL](https://developer.github.com/v4/) k načtení nedávných problémů napsaných v úložišti [dotnet/docs](https://github.com/dotnet/docs) . Začněte tím, že si vyhledáte následující kód pro `Main` metodu počáteční aplikace:

[!code-csharp[StarterAppMain](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#StarterAppMain)]

Můžete buď nastavit `GitHubKey` proměnnou prostředí na váš osobní přístupový token, nebo můžete nahradit poslední argument v `GenEnvVariable` volání pomocí tokenu vašeho osobního přístupového tokenu. Pokud uložíte zdroj s ostatními nebo pokud ho umístíte do sdíleného zdrojového úložiště, neumísťujte do zdrojového kódu svůj přístupový kód.

Po vytvoření klienta GitHub kód v `Main` vytvoří objekt vytváření sestav o průběhu a token zrušení. Po vytvoření `Main` těchto objektů volání `runPagedQueryAsync` načtou nejnovější 250 vytvořené problémy. Po dokončení této úlohy se zobrazí výsledky.

Při spuštění aplikace Starter můžete provést několik důležitých pozorování, jak se tato aplikace spouští.  Uvidíte průběh nahlášený pro každou stránku vrácenou z GitHubu. Můžete sledovat, že se pozastavená pauza ještě před tím, než GitHub vrátí všechny nové stránky problémů. A konečně problémy se zobrazí až po načtení všech 10 stránek z GitHubu.

## <a name="examine-the-implementation"></a>Kontrola implementace

Implementace odhalí, proč jste pozorováni chování popsané v předchozí části. Projděte si kód `runPagedQueryAsync`pro:

[!code-csharp[RunPagedQueryStarter](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#RunPagedQuery)]

Pojďme se soustředit na algoritmus stránkování a asynchronní strukturu předchozího kódu. (Podrobnosti o rozhraních API GitHub GraphQL najdete v [dokumentaci k GitHubu GraphQL](https://developer.github.com/v4/guides/) .) `runPagedQueryAsync` Metoda vytvoří výčet problémů od nejnovějších k nejstarší. Vyžádá 25 problémů na stránku a prověřuje `pageInfo` strukturu odpovědi, aby pokračovala na předchozí stránce. To sleduje standardní podporu stránkování GraphQL pro reakce na vícestránkové stránky. Odpověď obsahuje `pageInfo` objekt, který `hasPreviousPages` obsahuje hodnotu a `startCursor` hodnotu použitou k vyžádání předchozí stránky. Problémy jsou v `nodes` poli. `runPagedQueryAsync` Metoda připojí tyto uzly k poli, které obsahuje všechny výsledky ze všech stránek.

Po načtení a obnovení stránky výsledků se `runPagedQueryAsync` nahlásí průběh a kontrolují zrušení. Pokud je požadováno zrušení, `runPagedQueryAsync` <xref:System.OperationCanceledException>vyvolá výjimku.

Tento kód obsahuje několik prvků, které lze zlepšit. Co je nejdůležitější, `runPagedQueryAsync` musí přidělit úložiště pro všechny vrácené problémy. Tato ukázka zastaví problémy 250, protože načtení všech otevřených problémů by vyžadovalo mnohem více paměti pro uložení všech načtených problémů. Navíc protokoly pro podporu pokroku a podpory zrušení usnadňují pochopení algoritmu při prvním čtení. Chcete-li zjistit, kde je zaznamenán průběh, je nutné vyhledat třídu Progress. Také je nutné trasovat komunikaci prostřednictvím <xref:System.Threading.CancellationTokenSource> a jejího přidruženého <xref:System.Threading.CancellationToken> k pochopení, kde je zrušení požadováno a kde je uděleno.

## <a name="async-streams-provide-a-better-way"></a>Asynchronní streamy poskytují lepší způsob

Asynchronní streamy a přidružená jazyková podpora řeší všechna tyto aspekty. Kód, který generuje sekvenci, teď může `yield return` použít k vrácení prvků v metodě, která byla deklarována `async` s modifikátorem. Asynchronní datový proud můžete využívat pomocí `await foreach` smyčky stejně, jako byste využívali jakoukoli sekvenci `foreach` pomocí smyčky.

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

Jeden typ, který může být neznámý <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>, je. Struktura poskytuje podobné rozhraní API <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> pro třídu. `ValueTask` `ValueTask`se používá v těchto rozhraních z důvodů výkonu.

## <a name="convert-to-async-streams"></a>Převést na asynchronní proudy

Dále převeďte `runPagedQueryAsync` metodu pro generování asynchronního datového proudu. Nejprve změňte signaturu `runPagedQueryAsync` na `IAsyncEnumerable<JToken>`, pokud chcete vrátit, a odeberte token zrušení a objekty průběhu ze seznamu parametrů, jak je znázorněno v následujícím kódu:

[!code-csharp[FinishedSignature](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#UpdateSignature)]

Počáteční kód zpracuje každou stránku při načtení stránky, jak je znázorněno v následujícím kódu:

[!code-csharp[StarterPaging](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#ProcessPage)]

Nahraďte tyto tři řádky následujícím kódem:

[!code-csharp[FinishedPaging](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#YieldReturnPage)]

Můžete také odebrat deklaraci `finalResults` výše v této metodě `return` a příkaz, který následuje za smyčkou, kterou jste změnili.

Dokončili jste změny pro vygenerování asynchronního datového proudu. Metoda Finish by měla vypadat podobně jako následující kód:

[!code-csharp[FinishedGenerate](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#GenerateAsyncStream)]

Dále změníte kód, který používá kolekci ke využívání asynchronního datového proudu. Vyhledejte následující kód v `Main` , který zpracovává kolekci problémů:

[!code-csharp[EnumerateOldStyle](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#EnumerateOldStyle)]

Nahraďte tento kód následujícím `await foreach` smyčkou:

[!code-csharp[FinishedEnumerateAsyncStream](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#EnumerateAsyncStream)]

Kód pro dokončený kurz můžete získat z úložiště [dotnet/Samples](https://github.com/dotnet/samples) ve složce [CSharp/tutorials/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/finished) .

## <a name="run-the-finished-application"></a>Spuštění dokončené aplikace

Spusťte aplikaci znovu. Kontrastujte své chování s chováním úvodní aplikace. První stránka výsledků je vyhodnocena, jakmile bude k dispozici. Je možné, že při každém vyžádání a načtení každé nové stránky dojde k pozastavení, takže se výsledky další stránky rychle vytvoří. Blok není potřebný ke zpracování zrušení: volající může zastavit výčet kolekce. `try`  /  `catch` Průběh je jasně nahlášený, protože asynchronní datový proud generuje výsledky při stažení každé stránky.

Vylepšení využití paměti můžete zobrazit zkoumáním kódu. Již nemusíte přidělovat kolekci pro uložení všech výsledků před jejich výčtem. Volající může určit, jak se mají výsledky využívat, a pokud je potřeba kolekce úložiště.

Spouštějte počáteční i hotové aplikace a můžete sledovat rozdíly mezi implementacemi pro sebe. Přístupový token GitHubu, který jste vytvořili po spuštění tohoto kurzu, můžete odstranit po dokončení tohoto kurzu. Pokud útočník získal přístup k tomuto tokenu, měl by získat přístup k rozhraním API GitHubu pomocí vašich přihlašovacích údajů.
