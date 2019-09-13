---
title: Návrh s použitím typů odkazů s možnou hodnotou null
description: Tento rozšířený kurz poskytuje Úvod k odkazům s možnou hodnotou null. Naučíte se vyjádřit svůj návrh na to, kdy mohou být referenční hodnoty null, a nechat vynutit kompilátor, pokud nesmí mít hodnotu null.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 0c95065e6c380fab6ba33432a32b3297e78027a3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926632"
---
# <a name="tutorial-migrate-existing-code-with-nullable-reference-types"></a>Kurz: Migrovat existující kód s odkazy s možnou hodnotou null

C#8 zavádí **typy odkazů s možnou hodnotou null**, které připlňují odkazové typy stejným způsobem jako typy hodnot s možnou hodnotou null. Deklarujete proměnnou, která bude představovat **typ odkazu s možnou hodnotou null** připojením `?` k typu. Například `string?` představuje možnou hodnotu null `string`. Tyto nové typy můžete použít k přehlednějšímu vyjádření záměru návrhu: některé proměnné *musí mít vždy hodnotu*, jiné *mohou chybět hodnoty*. Všechny existující proměnné typu odkazu by byly interpretovány jako typ odkazu, který není null. 

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Při práci s kódem povolit kontroly pro prázdné odkazy
> - Diagnostikujte a opravte různá upozornění související s hodnotami null.
> - Spravujte rozhraní mezi povolenými povolenými a zakázanými kontexty s povolenou hodnotou null.
> - Ovládá kontexty anotace s možnou hodnotou null.

## <a name="prerequisites"></a>Požadavky

Musíte nastavit počítač tak, aby běžel .NET Core, včetně kompilátoru C# 8,0 beta. Kompilátor C# 8 beta je k dispozici v [aplikaci Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)nebo nejnovější verzi [.NET Core 3,0 Preview](https://dotnet.microsoft.com/download/dotnet-core/3.0).

V tomto kurzu se předpokládá, že C# máte zkušenosti s platformou a .NET, včetně sady Visual Studio nebo .NET Core CLI.

## <a name="explore-the-sample-application"></a>Prozkoumejte ukázkovou aplikaci

Ukázková aplikace, kterou migrujete, je webová aplikace čtečky informačního kanálu RSS. Čte z jednoho informačního kanálu RSS a zobrazuje souhrny pro nejnovější články. Můžete kliknout na některý z článků a navštívit web. Aplikace je relativně nová, ale byla zapsána před přístupným odkazem s možnou hodnotou null. Rozhodnutí o návrhu aplikace představují zásady zvuku, ale nevyužívají tuto důležitou funkci jazyka.

Ukázková aplikace obsahuje knihovnu testů jednotek, která ověřuje hlavní funkčnost aplikace. Tento projekt usnadňuje upgrade bezpečně, pokud změníte jakoukoli implementaci na základě vygenerovaných upozornění. Počáteční kód si můžete stáhnout z úložiště [dotnet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/start) GitHub.

Váš cíl migrace projektu by měl být využívat nové funkce jazyka, aby bylo jasné vyjádřit záměr na hodnotu null proměnných, a tak učinit tak, že kompilátor negeneruje upozornění, když máte kontext anotace s možnou hodnotou null a nastaven výstražný kontext s `enabled`možnou hodnotou null.

## <a name="upgrade-the-projects-to-c-8"></a>Upgradovat projekty na C# 8

Dobrým prvním krokem je určit rozsah úlohy migrace. Začněte upgradem projektu na C# 8,0 (nebo novější). `LangVersion` Přidejte element do obou souborů csproj pro webový projekt a projekt testování částí:

```xml
<LangVersion>8.0</LangVersion>
```

Upgrade jazykové verze vybere C# 8,0, ale nepovoluje kontext anotace s možnou hodnotou null nebo kontext s možnou hodnotou null. Znovu sestavte projekt, aby se zajistilo, že bude sestaven bez upozornění.

Dobrým dalším krokem je zapnout kontext anotace s možnou hodnotou null a zjistit, kolik upozornění se vygenerovalo. Přidejte následující element do obou souborů csproj v řešení přímo pod `LangVersion` prvkem:

```xml
<Nullable>enable</Nullable>
```

> [!IMPORTANT]
> Element se dřív jmenoval `NullableContextOptions`. `Nullable` Přejmenování se dodává se sadou Visual Studio 2019, 16,2-P1. Tato změna nemá .NET Core SDK 3.0.100-preview5-011568. Pokud používáte .NET Core CLI, budete ho muset použít `NullableContextOptions` , až bude k dispozici další verze Preview.

Proveďte testovací sestavení a Všimněte si seznamu upozornění. V této malé aplikaci kompilátor vygeneruje pět upozornění, takže je pravděpodobně nutné povolit kontext poznámky s možnou hodnotou null a zahájit opravy upozornění pro celý projekt.

Tato strategie funguje jenom pro menší projekty. U všech větších projektů je počet upozornění vygenerovaných povolením kontextu anotace s možnou hodnotou null pro celý základ kódu obtížnější opravit upozornění systematicky. U větších podnikových projektů často budete chtít najednou migrovat projekt. V každém projektu migrujte jednu třídu nebo soubor v jednom okamžiku.

## <a name="warnings-help-discover-original-design-intent"></a>Upozornění, která vám pomůžou zjistit původní záměr návrhu

K dispozici jsou dvě třídy, které generují více upozornění. `NewsStoryViewModel` Začněte třídou. `Nullable` Odeberte prvek z obou souborů csproj, abyste mohli omezit rozsah upozornění na oddíly kódu, se kterými pracujete. Otevřete soubor *NewsStoryViewModel.cs* a přidejte následující direktivy, abyste povolili kontext anotace s možnou hodnotou null pro `NewsStoryViewModel` a obnovili následující definici třídy:

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

Tyto dvě direktivy vám pomůžou zaměřit se na vaše úsilí při migraci. Pro oblast kódu, na které aktivně pracujete, jsou vygenerována upozornění s možnou hodnotou null. Můžete je nechat zapnuté, dokud nebudete připraveni zapnout upozornění pro celý projekt. `restore` Místo toho byste měli použít hodnotu `disable` spíše než, abyste omylem neaktivovali kontext později, když jste zapnuli anotace s možnou hodnotou null pro celý projekt. Jakmile zapnete kontext anotace s možnou hodnotou null pro celý projekt, můžete odebrat všechny `#nullable` direktivy pragma z tohoto projektu.

`NewsStoryViewModel` Třída je objekt pro přenos dat (DTO) a dvě vlastnosti jsou řetězce pro čtení a zápis:

[!code-csharp[InitialViewModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#StarterViewModel)]

Příčinou `CS8618`těchto dvou vlastností je neinicializovaná vlastnost "nepovolená hodnota null". Je dostatečně jasné: obě `string` vlastnosti mají výchozí `null` hodnotu při vytvoření `NewsStoryViewModel` konstrukce. To, co je důležité pro zjišťování `NewsStoryViewModel` , je způsob konstrukce objektů. Při prohlížení této třídy nemůžete zjistit, zda `null` je hodnota součástí návrhu, nebo pokud jsou tyto objekty nastaveny na hodnoty, které nejsou null vždy při vytvoření jedné z nich. Novinové články jsou vytvořeny v `GetNews` metodě `NewsService` třídy:

[!code-csharp[StarterCreateNewsItem](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#CreateNewsItem)]

V předchozím bloku kódu se už trochu přechází. Tato aplikace používá balíček NuGet [automapper](https://automapper.org/) k vytvoření položky zpráv z `ISyndicationItem`. Zjistili jste, že položky novinového článku jsou vytvořeny a vlastnosti jsou nastaveny v daném příkazu. To znamená, že v návrhu `NewsStoryViewModel` pro je tato vlastnost nikdy `null` mít hodnotu. Tyto vlastnosti by neměly být **typy odkazů**, které nejsou null. Který nejlépe vyjadřuje původní záměr návrhu. Ve skutečnosti *jsou* všechny `NewsStoryViewModel` správně vytvořeny instance s hodnotami, které nejsou null. Díky tomu následující inicializační kód provede platnou opravu:

```csharp
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; } = default!;
    public string Uri { get; set; } = default!;
}
```

Přiřazení `Title` `Uri` `default` typu a, `null` na které je pro typ, nemění chování programu za běhu. `string` `NewsStoryViewModel` Je stále vytvořen s hodnotami null, ale nyní kompilátor hlásí žádná upozornění. **Operátor null-striktní**, `!` znak následující po `default` výrazu instruuje kompilátor, že předchozí výraz není null. Tato technika může být účelná, pokud jiné změny vynutí mnohem větší změny základu kódu, ale v této aplikaci je poměrně rychlé a lepší řešení: `NewsStoryViewModel` Nastavte neměnný typ, kde jsou všechny vlastnosti nastaveny v konstruktoru. Proveďte následující změny `NewsStoryViewModel`:

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#FinishedViewModel)]

Až to uděláte, musíte aktualizovat kód, který konfiguruje automapper, aby místo nastavení vlastností používal konstruktor. V `NewsService.cs` dolní části souboru otevřete a vyhledejte následující kód:

[!code-csharp[StarterAutoMapper](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Tento kód mapuje vlastnosti `ISyndicationItem` objektu `NewsStoryViewModel` na vlastnosti. Chcete, aby automapper místo toho poskytovala mapování pomocí konstruktoru. Výše uvedený kód nahraďte následující konfigurací automapper:

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Všimněte si, že vzhledem k tomu, že je tato třída malá a že jste pečlivě prozkoumali, měli byste zapnout `#nullable enable` direktivu nad touto deklarací třídy. Změna konstruktoru mohla způsobit poškození, takže je vhodné spustit všechny testy a otestovat aplikaci před přechodem na.

První sada změn ukázala, jak zjistit, kdy původní návrh uvedl, že proměnné by neměly být nastaveny na `null`. Technika je označována jako **správná konstrukcí**. Deklarujete, že objekt a jeho vlastnosti nemohou být `null` při sestavení. Analýza toku kompilátoru poskytuje záruku, že tyto vlastnosti nejsou nastaveny `null` po konstrukci. Všimněte si, že tento konstruktor je volán externím kódem a tento kód je **oblivious s možnou hodnotou null**. Nová syntaxe neposkytuje kontrolu za běhu. Externí kód může obejít analýzu toku kompilátoru. 

Jindy, struktura třídy poskytuje různé změny záměru. Otevřete soubor *Error.cshtml.cs* ve složce *stránky* . `ErrorViewModel` Obsahuje následující kód:

[!code-csharp[StarterErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Error.cshtml.cs#StartErrorModel)]

Přidejte direktivu před deklaraci třídy `#nullable restore` a direktivu po ní. `#nullable enable` Zobrazí se jedno upozornění, které `RequestId` není inicializováno. Pohledem na třídu byste měli rozhodnout, že `RequestId` v některých případech by vlastnost měla mít hodnotu null. Existence `ShowRequestId` vlastnosti označuje, že chybějící hodnoty jsou možné. Vzhledem `null` k tomu, že je `?` platný, `string` přidejte na typ, `RequestId` který určuje, že vlastnost je *typ odkazu s možnou hodnotou null*. Konečná třída vypadá jako v následujícím příkladu:

[!code-csharp[FinishedErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Error.cshtml.cs#ErrorModel)]

Zkontrolujte použití vlastnosti a uvidíte, že na přidružené stránce je vlastnost před vykreslením v kódu zkontrolována na hodnotu null. To je bezpečné použití typu odkazu s možnou hodnotou null, takže jste s touto třídou hotovi.

## <a name="fixing-nulls-causes-change"></a>Oprava hodnot null způsobí změnu.

Oprava pro jednu sadu upozornění často vytvoří nová upozornění v souvisejícím kódu. Pojďme se podívat na upozornění v akci `index.cshtml.cs` opravou třídy. `index.cshtml.cs` Otevřete soubor a Projděte si kód. Tento soubor obsahuje kód za stránkou indexu:

[!code-csharp[StarterIndexModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Index.cshtml.cs#IndexModelStart)]

`#nullable enable` Přidejte direktivu a uvidíte dvě upozornění. Není inicializována `NewsItems`vlastnostanivlastnost `ErrorText` . Přezkoumání této třídy by vedlo k názoru, že obě vlastnosti by měly být odkazy s možnou hodnotou null: Oba mají privátní metody setter. V `OnGet` metodě je přiřazena právě jedna. Před provedením změn se podívejte na uživatele obou vlastností. Na samotné stránce je před generováním značek pro všechny chyby zkontrolováno na `ErrorText` hodnotu null. Kolekce je porovnána s a zkontrolována ,abybylozajištěno,žekolekceobsahujepoložky.`null` `NewsItems` Rychlá oprava by představovala vlastnosti odkazu s možnou hodnotou null. Lepším řešením je vytvořit kolekci odkazový typ, který není null, a při načítání zpráv přidat položky do existující kolekce. První oprava je přidat `?` `string` do typu pro `ErrorText`:

[!code-csharp[UpdateErrorText](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#UpdateErrorText)]

Tato změna se neprojeví na základě jiného kódu, protože jakýkoliv `ErrorText` přístup k této vlastnosti byl již chráněn pomocí kontroly hodnoty null. Dále inicializujte `NewsItems` seznam a odeberte metodu setter vlastnosti a vytvořte ji jako vlastnost jen pro čtení:

[!code-csharp[InitializeNewsItems](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#InitializeNewsItems)]

Opravili jsme upozornění, ale zavedli chybu. Seznam je nyní **správný konstrukcí**, ale kód, který nastaví v `OnGet` seznamu, musí být změněn tak, aby odpovídal novému rozhraní API. `NewsItems` Místo přiřazení volejte volání `AddRange` pro přidání položek zpráv do existujícího seznamu:

[!code-csharp[AddRange](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#AddRange)]

Použití `AddRange` namísto přiřazení znamená `GetNews` , že metoda může `List`vracet `IEnumerable` namísto. Který ukládá jedno přidělení. Změňte signaturu metody a odeberte `ToList` volání, jak je znázorněno v následujícím příkladu kódu:

[!code-csharp[GetNews](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#GetNewsFinished)]

Změna signatury také zruší jeden z testů. `NewsServiceTests.cs` Otevřete soubor`Services` ve složce`SimpleFeedReader.Tests` projektu. Přejděte na `Returns_News_Stories_Given_Valid_Uri` test a změňte typ `result` proměnné na `IEnumerable<NewsItem>`. Změna typu znamená, že `Count` vlastnost již není k dispozici, takže `Count` nahraďte vlastnost `Assert` voláním metody `Any()`:

[!code-csharp[FixTests](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader.Tests/Services/NewsServiceTests.cs#FixTestSignature)]

Je nutné přidat `using System.Linq` příkaz na začátek souboru.

Tato sada změn zvýrazňuje zvláštní pozornost při aktualizaci kódu, který obsahuje obecné vytváření instancí. Seznam i elementy v seznamu typů bez hodnoty null. V obou případech mohou být typy s možnou hodnotou null. Jsou povoleny všechny následující deklarace:

- `List<NewsStoryViewModel>`: neprázdný seznam modelů zobrazení s hodnotou null
- `List<NewsStoryViewModel?>`: neprázdný seznam modelů zobrazení s možnou hodnotou null
- `List<NewsStoryViewModel>?`: seznam s možnou hodnotou null v neprázdných modelech zobrazení.
- `List<NewsStoryViewModel?>?`: nepovolený seznam modelů zobrazení s možnou hodnotou null.

## <a name="interfaces-with-external-code"></a>Rozhraní s externím kódem

Provedli jste změny `NewsService` třídy, takže zapnete `#nullable enable` anotaci pro tuto třídu. To negeneruje žádná nová upozornění. Pečlivé zkoumání třídy však pomáhá ilustrovat některá omezení analýzy toku kompilátoru. Prověřte konstruktor:

[!code-csharp[ServiceConstructor](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ServiceConstructor)]

`IMapper` Parametr je zadán jako neprázdný odkaz. Je volána ASP.NET Core kódem infrastruktury, takže kompilátor ve skutečnosti neví, že `IMapper` nikdy nebude null. Výchozí kontejner pro vkládání závislostí (DI) ASP.NET Core vyvolá výjimku, pokud nemůže vyřešit nezbytnou službu, takže kód je správný. Kompilátor nemůže ověřit všechna volání vašich veřejných rozhraní API, a to i v případě, že je váš kód zkompilován s povolenými kontexty anotace s možnou hodnotou null. Kromě toho mohou být knihovny spotřebovány projekty, které ještě nebyly přihlášeny k použití typů odkazů s možnou hodnotou null. Ověřte vstupy do veřejných rozhraní API, i když je deklarujete jako nehodnotné typy.

## <a name="get-the-code"></a>Získat kód

Opravili jste upozornění, která jste identifikovali při počáteční kompilaci testů, takže teď můžete zapnout kontext anotace s možnou hodnotou null pro oba projekty. Znovu sestavte projekty; Kompilátor ohlásí žádná upozornění. V úložišti GitHub [/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/finished) můžete získat kód dokončeného projektu.

Nové funkce, které podporují typy odkazů s možnou hodnotou null, vám pomůžou najít a opravit `null` potenciální chyby ve vašem kódu. Povolení kontextu anotace s možnou hodnotou null umožňuje vyjádřit svůj záměr návrhu: některé proměnné by nikdy neměly mít hodnotu null, jiné proměnné mohou obsahovat hodnoty null. Tyto funkce usnadňují deklaraci záměru návrhu. Podobně kontext varování s možnou hodnotou null instruuje kompilátor, aby vydával upozornění v případě porušení tohoto záměru. Tato upozornění vás provedou, abyste provedli aktualizace, které by váš kód lépe odolný `NullReferenceException` a méně pravděpodobně vyvolali během provádění. Rozsah těchto kontextů můžete řídit tak, abyste se mohli soustředit na místní oblasti kódu, které se mají migrovat, zatímco zbývající základ kódu se nedotkne. V praxi můžete tuto úlohu migrace provést jako součást běžné údržby tříd. V tomto kurzu se ukázal proces migrace aplikace na použití typů odkazů s možnou hodnotou null. Můžete prozkoumat větší reálný příklad tohoto procesu prozkoumáním žádosti o přijetí změn (PR [Jan Skeet](https://github.com/jskeet) ), která umožňuje zahrnutí typů odkazů s možnou hodnotou null do [NodaTime](https://github.com/nodatime/nodatime/pull/1240/commits).
