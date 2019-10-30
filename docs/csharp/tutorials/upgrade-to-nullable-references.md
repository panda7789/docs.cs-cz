---
title: Návrh s použitím typů odkazů s možnou hodnotou null
description: Tento rozšířený kurz poskytuje Úvod k odkazům s možnou hodnotou null. Naučíte se vyjádřit svůj návrh na to, kdy mohou být referenční hodnoty null, a nechat vynutit kompilátor, pokud nesmí mít hodnotu null.
ms.date: 02/19/2019
ms.technology: csharp-null-safety
ms.custom: mvc
ms.openlocfilehash: 9cb9ac1b292e61d6a8a5f84be29a6a6c323725fc
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039689"
---
# <a name="tutorial-migrate-existing-code-with-nullable-reference-types"></a>Kurz: migrace stávajícího kódu s odkazy s možnou hodnotou null

C#8 zavádí **typy odkazů s možnou hodnotou null**, které připlňují odkazové typy stejným způsobem jako typy hodnot s možnou hodnotou null. Deklarujete proměnnou, která bude představovat **typ odkazu s možnou hodnotou null** připojením `?` k typu. Například `string?` představuje hodnotu null `string`. Tyto nové typy můžete použít k přehlednějšímu vyjádření záměru návrhu: některé proměnné *musí mít vždy hodnotu*, jiné *mohou chybět hodnoty*. Všechny existující proměnné typu odkazu by byly interpretovány jako typ odkazu, který není null. 

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Při práci s kódem povolit kontroly pro prázdné odkazy
> - Diagnostikujte a opravte různá upozornění související s hodnotami null.
> - Spravujte rozhraní mezi povolenými povolenými a zakázanými kontexty s povolenou hodnotou null.
> - Ovládá kontexty anotace s možnou hodnotou null.

## <a name="prerequisites"></a>Požadavky

Musíte nastavit počítač tak, aby běžel .NET Core, včetně kompilátoru C# 8,0. Kompilátor C# 8 je k dispozici počínaje [verzí Visual Studio 2019 verze 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download).

V tomto kurzu se předpokládá, že C# máte zkušenosti s platformou a .NET, včetně sady Visual Studio nebo .NET Core CLI.

## <a name="explore-the-sample-application"></a>Prozkoumejte ukázkovou aplikaci

Ukázková aplikace, kterou migrujete, je webová aplikace čtečky informačního kanálu RSS. Čte z jednoho informačního kanálu RSS a zobrazuje souhrny pro nejnovější články. Můžete kliknout na některý z článků a navštívit web. Aplikace je relativně nová, ale byla zapsána před přístupným odkazem s možnou hodnotou null. Rozhodnutí o návrhu aplikace představují zásady zvuku, ale nevyužívají tuto důležitou funkci jazyka.

Ukázková aplikace obsahuje knihovnu testů jednotek, která ověřuje hlavní funkčnost aplikace. Tento projekt usnadňuje upgrade bezpečně, pokud změníte jakoukoli implementaci na základě vygenerovaných upozornění. Počáteční kód si můžete stáhnout z úložiště [dotnet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/start) GitHub.

Váš cíl migrace projektu by měl být využívat nové funkce jazyka, aby bylo jasné vyjádřit záměr na hodnotu null proměnných, a tak učinit tak, že kompilátor negeneruje upozornění, když máte kontext anotace s možnou hodnotou null a Výstražný kontext s možnou hodnotou null je nastaven na `enabled`.

## <a name="upgrade-the-projects-to-c-8"></a>Upgradovat projekty na C# 8

Dobrým prvním krokem je určit rozsah úlohy migrace. Začněte upgradem projektu na C# 8,0 (nebo novější). Přidejte `LangVersion` element do obou souborů csproj pro webový projekt a projekt testování částí:

```xml
<LangVersion>8.0</LangVersion>
```

Upgrade jazykové verze vybere C# 8,0, ale nepovoluje kontext anotace s možnou hodnotou null nebo kontext s možnou hodnotou null. Znovu sestavte projekt, aby se zajistilo, že bude sestaven bez upozornění.

Dobrým dalším krokem je zapnout kontext anotace s možnou hodnotou null a zjistit, kolik upozornění se vygenerovalo. Přidejte následující element do obou souborů csproj v řešení přímo pod prvkem `LangVersion`:

```xml
<Nullable>enable</Nullable>
```

Proveďte testovací sestavení a Všimněte si seznamu upozornění. V této malé aplikaci kompilátor vygeneruje pět upozornění, takže je pravděpodobně nutné povolit kontext poznámky s možnou hodnotou null a zahájit opravy upozornění pro celý projekt.

Tato strategie funguje jenom pro menší projekty. U všech větších projektů je počet upozornění vygenerovaných povolením kontextu anotace s možnou hodnotou null pro celý základ kódu obtížnější opravit upozornění systematicky. U větších podnikových projektů často budete chtít najednou migrovat projekt. V každém projektu migrujte jednu třídu nebo soubor v jednom okamžiku.

## <a name="warnings-help-discover-original-design-intent"></a>Upozornění, která vám pomůžou zjistit původní záměr návrhu

K dispozici jsou dvě třídy, které generují více upozornění. Začněte s třídou `NewsStoryViewModel`. Odeberte prvek `Nullable` z obou souborů csproj, abyste mohli omezit rozsah upozornění na oddíly kódu, se kterými pracujete. Otevřete soubor *NewsStoryViewModel.cs* a přidejte následující direktivy, abyste povolili kontext anotace s možnou hodnotou null pro `NewsStoryViewModel` a obnovili je následující definice třídy:

```csharp
#nullable enable
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; }
    public string Uri { get; set; }
}
#nullable restore
```

Tyto dvě direktivy vám pomůžou zaměřit se na vaše úsilí při migraci. Pro oblast kódu, na které aktivně pracujete, jsou vygenerována upozornění s možnou hodnotou null. Můžete je nechat zapnuté, dokud nebudete připraveni zapnout upozornění pro celý projekt. Místo `disable` hodnoty byste měli použít `restore`, takže nechtěně zakážete kontext později, když jste zapnuli anotace s možnou hodnotou null pro celý projekt. Jakmile zapnete kontext anotace s možnou hodnotou null pro celý projekt, můžete z tohoto projektu odebrat všechny `#nullable` direktivy pragma.

Třída `NewsStoryViewModel` je objekt pro přenos dat (DTO) a dvě vlastnosti jsou řetězce pro čtení a zápis:

[!code-csharp[InitialViewModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#StarterViewModel)]

Tyto dvě vlastnosti způsobují `CS8618`, nepovolenou vlastnost není inicializovaná. Je to dostatečně jasné: vlastnosti `string` mají výchozí hodnotu `null`, když je vytvořen `NewsStoryViewModel`. Důležité je, abyste zjistili, jak se vytvářejí objekty `NewsStoryViewModel`. Při prohlížení této třídy nemůžete zjistit, zda je hodnota `null` součástí návrhu, nebo pokud jsou tyto objekty nastaveny na hodnoty, které nejsou null vždy při vytvoření jedné z nich. Příběhy novinek jsou vytvořeny v metodě `GetNews` `NewsService` třídy:

[!code-csharp[StarterCreateNewsItem](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#CreateNewsItem)]

V předchozím bloku kódu se už trochu přechází. Tato aplikace používá balíček NuGet [automapper](https://automapper.org/) k vytvoření položky zpráv z `ISyndicationItem`. Zjistili jste, že položky novinového článku jsou vytvořeny a vlastnosti jsou nastaveny v daném příkazu. To znamená, že návrh `NewsStoryViewModel` označuje, že tyto vlastnosti by nikdy neměly mít hodnotu `null`. Tyto vlastnosti by neměly být **typy odkazů**, které nejsou null. Který nejlépe vyjadřuje původní záměr návrhu. Ve skutečnosti *jsou* všechny `NewsStoryViewModel` správně vytvořeny s hodnotami, které nejsou null. Díky tomu následující inicializační kód provede platnou opravu:

```csharp
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; } = default!;
    public string Uri { get; set; } = default!;
}
```

Přiřazení `Title` a `Uri` `default`, které `null` pro typ `string`, nemění chování programu za běhu. `NewsStoryViewModel` je stále vytvořen s hodnotami null, ale nyní kompilátor hlásí žádná upozornění. **Operátor null-striktní**, znak `!` následující po `default` výrazu instruuje kompilátor, že předchozí výraz není null. Tato technika může být účelná, pokud jiné změny vynutí mnohem větší změny základu kódu, ale v této aplikaci je poměrně rychlé a lepší řešení: `NewsStoryViewModel` neměnného typu, kde jsou všechny vlastnosti nastaveny v konstruktoru. Proveďte následující změny `NewsStoryViewModel`:

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#FinishedViewModel)]

Až to uděláte, musíte aktualizovat kód, který konfiguruje automapper, aby místo nastavení vlastností používal konstruktor. Otevřete `NewsService.cs` a vyhledejte následující kód v dolní části souboru:

[!code-csharp[StarterAutoMapper](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Tento kód mapuje vlastnosti objektu `ISyndicationItem` na vlastnosti `NewsStoryViewModel`. Chcete, aby automapper místo toho poskytovala mapování pomocí konstruktoru. Výše uvedený kód nahraďte následující konfigurací automapper:

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Všimněte si, že vzhledem k tomu, že je tato třída malá a že jste pečlivě prozkoumali, měli byste zapnout direktivu `#nullable enable` nad rámec této deklarace třídy. Změna konstruktoru mohla způsobit poškození, takže je vhodné spustit všechny testy a otestovat aplikaci před přechodem na.

První sada změn ukázala, jak zjistit, kdy původní návrh určil, že by proměnné neměly být nastavené na `null`. Technika je označována jako **správná konstrukcí**. Deklarujete, že objekt a jeho vlastnosti nelze `null`, když je vytvořen. Analýza toku kompilátoru poskytuje záruku, že tyto vlastnosti nejsou nastaveny na `null` po konstrukci. Všimněte si, že tento konstruktor je volán externím kódem a tento kód je **oblivious s možnou hodnotou null**. Nová syntaxe neposkytuje kontrolu za běhu. Externí kód může obejít analýzu toku kompilátoru. 

Jindy, struktura třídy poskytuje různé změny záměru. Otevřete soubor *Error.cshtml.cs* ve složce *stránky* . `ErrorViewModel` obsahuje následující kód:

[!code-csharp[StarterErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Error.cshtml.cs#StartErrorModel)]

Přidejte direktivu `#nullable enable` před deklaraci třídy a direktivu `#nullable restore`. Zobrazí se jedno upozornění, že `RequestId` neinicializuje. Pohledem na třídu byste měli rozhodnout, že v některých případech by vlastnost `RequestId` měla mít hodnotu null. Existence vlastnosti `ShowRequestId` označuje, že chybějící hodnoty jsou možné. Vzhledem k tomu, že je `null` platný, přidejte `?` na typ `string` k označení, že vlastnost `RequestId` je *odkazem s možnou hodnotou null*. Konečná třída vypadá jako v následujícím příkladu:

[!code-csharp[FinishedErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Error.cshtml.cs#ErrorModel)]

Zkontrolujte použití vlastnosti a uvidíte, že na přidružené stránce je vlastnost před vykreslením v kódu zkontrolována na hodnotu null. To je bezpečné použití typu odkazu s možnou hodnotou null, takže jste s touto třídou hotovi.

## <a name="fixing-nulls-causes-change"></a>Oprava hodnot null způsobí změnu.

Oprava pro jednu sadu upozornění často vytvoří nová upozornění v souvisejícím kódu. Pojďme se podívat na upozornění v akci tím, že opravíte třídu `index.cshtml.cs`. Otevřete soubor `index.cshtml.cs` a Projděte si kód. Tento soubor obsahuje kód za stránkou indexu:

[!code-csharp[StarterIndexModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Index.cshtml.cs#IndexModelStart)]

Přidejte direktivu `#nullable enable` a zobrazí se dvě upozornění. Není inicializována vlastnost `ErrorText` ani vlastnost `NewsItems`. Přezkoumání této třídy by vedlo k názoru, že obě vlastnosti by měly mít hodnoty s možnou hodnotou null: obě mají privátní metody setter. V metodě `OnGet` je přiřazena právě jedna. Před provedením změn se podívejte na uživatele obou vlastností. V samotné stránce je `ErrorText` před generováním značek pro všechny chyby zkontrolováno na hodnotu null. Kolekce `NewsItems` se kontroluje proti `null`a kontrolovala se, aby kolekce měla položky. Rychlá oprava by představovala vlastnosti odkazu s možnou hodnotou null. Lepším řešením je vytvořit kolekci odkazový typ, který není null, a při načítání zpráv přidat položky do existující kolekce. První oprava je přidání `?` do `string` typu pro `ErrorText`:

[!code-csharp[UpdateErrorText](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#UpdateErrorText)]

Tato změna se nevyhodnotí na základě jiného kódu, protože jakýkoli přístup k vlastnosti `ErrorText` byl již chráněn pomocí kontroly hodnoty null. Dále inicializujte seznam `NewsItems` a odeberte metodu setter vlastnosti a vytvořte ji jako vlastnost jen pro čtení:

[!code-csharp[InitializeNewsItems](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#InitializeNewsItems)]

Opravili jsme upozornění, ale zavedli chybu. Seznam `NewsItems` je nyní **správný konstrukcí**, ale kód, který nastaví seznam v `OnGet` se musí změnit tak, aby odpovídal novému rozhraní API. Místo přiřazení volejte `AddRange`, aby se položky příspěvků přidaly do existujícího seznamu:

[!code-csharp[AddRange](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#AddRange)]

Použití `AddRange` místo přiřazení znamená, že metoda `GetNews` může vracet `IEnumerable` namísto `List`. Který ukládá jedno přidělení. Změňte signaturu metody a odeberte `ToList` volání, jak je znázorněno v následujícím příkladu kódu:

[!code-csharp[GetNews](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#GetNewsFinished)]

Změna signatury také zruší jeden z testů. Otevřete soubor `NewsServiceTests.cs` ve složce `Services` projektu `SimpleFeedReader.Tests`. Přejděte na `Returns_News_Stories_Given_Valid_Uri` test a změňte typ proměnné `result` na `IEnumerable<NewsItem>`. Změna typu znamená, že vlastnost `Count` již není k dispozici, takže nahraďte vlastnost `Count` v `Assert` voláním `Any()`:

[!code-csharp[FixTests](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader.Tests/Services/NewsServiceTests.cs#FixTestSignature)]

Je nutné přidat příkaz `using System.Linq` na začátek souboru.

Tato sada změn zvýrazňuje zvláštní pozornost při aktualizaci kódu, který obsahuje obecné vytváření instancí. Seznam i elementy v seznamu typů bez hodnoty null. V obou případech mohou být typy s možnou hodnotou null. Jsou povoleny všechny následující deklarace:

- `List<NewsStoryViewModel>`: neprázdný seznam modelů zobrazení s hodnotou null
- `List<NewsStoryViewModel?>`: neprázdný seznam modelů zobrazení s možnou hodnotou null
- `List<NewsStoryViewModel>?`: seznam s možnou hodnotou null v neprázdných modelech zobrazení.
- `List<NewsStoryViewModel?>?`: seznam povolených typů zobrazení s možnou hodnotou null.

## <a name="interfaces-with-external-code"></a>Rozhraní s externím kódem

Provedli jste změny ve třídě `NewsService`, takže zapnete `#nullable enable` anotaci této třídy. To negeneruje žádná nová upozornění. Pečlivé zkoumání třídy však pomáhá ilustrovat některá omezení analýzy toku kompilátoru. Prověřte konstruktor:

[!code-csharp[ServiceConstructor](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ServiceConstructor)]

Parametr `IMapper` je zadán jako neprázdný odkaz. Je volána ASP.NET Core kódem infrastruktury, takže kompilátor opravdu neví, že `IMapper` nikdy nebude null. Výchozí kontejner pro vkládání závislostí (DI) ASP.NET Core vyvolá výjimku, pokud nemůže vyřešit nezbytnou službu, takže kód je správný. Kompilátor nemůže ověřit všechna volání vašich veřejných rozhraní API, a to i v případě, že je váš kód zkompilován s povolenými kontexty anotace s možnou hodnotou null. Kromě toho mohou být knihovny spotřebovány projekty, které ještě nebyly přihlášeny k použití typů odkazů s možnou hodnotou null. Ověřte vstupy do veřejných rozhraní API, i když je deklarujete jako nehodnotné typy.

## <a name="get-the-code"></a>Získat kód

Opravili jste upozornění, která jste identifikovali při počáteční kompilaci testů, takže teď můžete zapnout kontext anotace s možnou hodnotou null pro oba projekty. Znovu sestavte projekty; Kompilátor ohlásí žádná upozornění. V úložišti GitHub [/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/finished) můžete získat kód dokončeného projektu.

Nové funkce, které podporují typy odkazů s možnou hodnotou null, vám pomůžou najít a opravit potenciální chyby ve způsobu zpracování `null` hodnot ve vašem kódu. Povolení kontextu anotace s možnou hodnotou null umožňuje vyjádřit svůj záměr návrhu: některé proměnné by nikdy neměly mít hodnotu null, jiné proměnné mohou obsahovat hodnoty null. Tyto funkce usnadňují deklaraci záměru návrhu. Podobně kontext varování s možnou hodnotou null instruuje kompilátor, aby vydával upozornění v případě porušení tohoto záměru. Tato upozornění vás provedou, abyste provedli aktualizace, díky kterým je váš kód větší odolný a méně pravděpodobný, aby během provádění vyvolal `NullReferenceException`. Rozsah těchto kontextů můžete řídit tak, abyste se mohli soustředit na místní oblasti kódu, které se mají migrovat, zatímco zbývající základ kódu se nedotkne. V praxi můžete tuto úlohu migrace provést jako součást běžné údržby tříd. V tomto kurzu se ukázal proces migrace aplikace na použití typů odkazů s možnou hodnotou null. Můžete prozkoumat větší reálný příklad tohoto procesu prozkoumáním žádosti o přijetí změn (PR [Jan Skeet](https://github.com/jskeet) ), která umožňuje zahrnutí typů odkazů s možnou hodnotou null do [NodaTime](https://github.com/nodatime/nodatime/pull/1240/commits).
