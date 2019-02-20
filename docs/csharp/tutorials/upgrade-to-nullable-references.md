---
title: Návrh s typy s možnou hodnotou Null odkazů
description: V tomto kurzu pokročilé obsahuje úvod do typy s možnou hodnotou Null odkazů. Se dozvíte, jak vyjádřit svůj návrh úmyslem při může mít hodnotu null referenční hodnoty a nechat kompilátor vynucovat, když nemohou být null.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 57f738771a6f1d2cebe7af546d06ac7d7289a338
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2019
ms.locfileid: "56443265"
---
# <a name="tutorial-migrate-existing-code-with-nullable-reference-types"></a>Kurz: Migrovat existující kód s typy s možnou hodnotou Null odkazů

C#8 zavádí **typy s možnou hodnotou Null odkazů**, kterou doplněk referenční typy stejným způsobem jako typy s možnou hodnotou doplňují typy hodnot. Deklarujete proměnnou **typ s možnou hodnotou Null odkazu** připojením `?` typu. Například `string?` představuje s povolenou hodnotou Null `string`. Pro větší přehlednost express máte v úmyslu návrhu můžete použít tyto nové typy: Některé proměnné *musí mít vždy hodnotu*, ostatní *pravděpodobně chybí hodnota*. Všechny existující proměnné typu odkazu je interpretován jako typ neumožňující hodnotu odkazu. 

V tomto kurzu se dozvíte jak:

> [!div class="checklist"]
> * Povolte kontroly odkaz s hodnotou null při práci s kódem.
> * Diagnostikujte a opravte různých upozornění související s hodnotami null.
> * Správa rozhraní mezi s možnou hodnotou Null zakázané kontexty povolené a s povolenou hodnotou Null.
> * Ovládací prvek s možnou hodnotou Null anotace kontexty.

## <a name="prerequisites"></a>Požadavky

Budete muset nastavit počítač pro spuštění .NET Core, včetně C# 8.0 beta verze kompilátoru. C# 8 beta verze kompilátoru je k dispozici s [Visual Studio 2019 preview 2 a novější](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+preview), nebo [.NET Core 3.0 ve verzi preview 2](https://dotnet.microsoft.com/download/dotnet-core/3.0).

Tento kurz předpokládá, že jste obeznámeni s C# a .NET, včetně sady Visual Studio nebo rozhraní příkazového řádku .NET Core.

## <a name="explore-the-sample-application"></a>Prozkoumat ukázkové aplikace

Ukázkové aplikace, provedeme migraci je informačního kanálu čtečky webové aplikace. Načte z jedné informační kanál RSS a zobrazuje souhrny pro nejnovější články. Můžete kliknout na kterýkoli z následujících článků na webu. Aplikace je relativně nové, ale byla zapsána před typy s možnou hodnotou NULL referenční vlastnosti byly k dispozici. Rozhodnutí o návrhu pro aplikaci reprezentována zvukové zásady, ale není využít výhod této funkci jazyka důležité.

Ukázkové aplikace obsahuje knihovnu testu jednotky, která ověřuje hlavní funkce aplikace. Tento projekt usnadní upgradovat bez obav, pokud změníte některá provádění podle vygeneruje upozornění. Můžete stáhnout počáteční kód z [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/start) úložiště GitHub.

Vaším cílem migrace projektu by měl být využívat nové funkce jazyků tak, aby vám jasně express máte v úmyslu na Null proměnné a udělat tak, že kompilátor negeneruje upozornění, když budete mít kontext s možnou hodnotou Null poznámky a s povolenou hodnotou Null kontext upozornění nastavena na `enabled`.

## <a name="upgrade-the-projects-to-c-8"></a>Upgrade projektů na C# 8

Je dobrý první krok k určení oboru této úlohy migrace. Začněte tím, že probíhá upgrade projektu na C# 8.0 (nebo novější). Přidat `LangVersion` element na oba soubory csproj pro webový projekt a projekt testování částí:

```xml
<LangVersion>8.0</LangVersion>
```

Upgrade verze jazyka vybere C# 8.0, ale neumožňuje kontext poznámky s možnou hodnotou Null nebo s povolenou hodnotou Null kontext upozornění. Znovu sestavte projekt k zajištění, že sestavení bez upozornění.

Dobré dalším krokem je zapnout v kontextu s možnou hodnotou Null poznámky a zobrazit, kolik upozornění. Přidejte následující prvek na oba soubory csproj v řešení, přímo pod `LangVersion` element:

```xml
<NullableContextOptions>enable</NullableContextOptions>
```

Provést testovací sestavení a Všimněte si, že seznam upozornění. V tomto malou aplikaci kompilátor vygeneruje pět upozornění, tak, aby byl pravděpodobně ponecháte kontextu s možnou hodnotou Null anotace povolená a začít řešit upozornění pro celý projekt.

Strategie je, že funguje pouze pro menší projekty. U větších projektů, počet upozornění vygenerované povolením kontext s možnou hodnotou Null anotace pro celým základem kódu bude těžší, chcete-li vyřešit upozornění systematicky. Pro větší podnikových projektů budete často chcete migrovat jeden projekt současně. V každém projektu migrace jedné třídy nebo soubor v čase.

## <a name="warnings-help-discover-original-design-intent"></a>Upozornění pomáhají zjistit původní záměr návrhu

Existují dvě třídy, které generují několik upozornění. Začněte `NewsStoryViewModel` třídy. Odeberte `NullableContextOptions` element z obou csproj soubory tak, aby bylo možné omezit obor upozornění na části kódu, kterou pracujete. Otevřít *NewsStoryViewModel.cs* a přidejte následující direktivy umožňující kontext s možnou hodnotou NULL Poznámky `NewsStoryViewModel` a obnovte ji po definici této třídy:

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

Tyto dvě direktivy umožňují zaměřit migrace. Pro oblasti kódu aktivně pracuje na vygenerují se upozornění s možnou hodnotou Null. Budete necháte je na až budete připraveni k zapnutí nastavení v upozornění pro celý projekt. Měli byste použít `restore` spíše než `disable` hodnotu tak, aby není zakážete omylem kontextu později při jste zapnuli poznámky s možnou hodnotou Null pro celý projekt. Jakmile jste zapnuli kontext s možnou hodnotou Null anotace pro celý projekt, můžete odebrat všechny `#nullable` direktivy pragma z tohoto projektu.

`NewsStoryViewModel` Třída je objekt pro přenos dat (DTO) a dvě vlastnosti jsou řetězce pro čtení a zápisu:

[!code-csharp[InitialViewModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#StarterViewModel)]

Tyto dvě vlastnosti způsobit `CS8618`, "neumožňující vlastností není inicializován". Který má dostatek zrušte: oba `string` vlastnosti mají výchozí hodnotu `null` při `NewsStoryViewModel` je vytvořený. Co je důležité, abyste zjišťování je jak `NewsStoryViewModel` jsou objekty zhotoveny. Prohlížení Tato třída, nelze zjistit, pokud `null` hodnota je součástí návrhu nebo pokud tyto objekty jsou nastavené na nenulovou hodnoty pokaždé, když se jeden se vytvoří. Nové příběhy jsou vytvořené v `GetNews` metodu `NewsService` třídy:

[!code-csharp[StarterCreateNewsItem](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#CreateNewsItem)]

Je poměrně děje předchozí blok kódu. Tato aplikace používá [AutoMapper](http://automapper.org/) balíček NuGet pro vytvoření položky zpráv ze `ISyndicationItem`. Jste se seznámili, že položky zprávy scénáře jsou vytvořeny a jsou nastaveny vlastnosti v tomto jeden příkaz. To znamená, že návrh pro `NewsStoryViewModel` označuje, že tyto vlastnosti by měly mít nikdy `null` hodnotu. Tyto vlastnosti by měla být **nemá odkazové typy**. Které bude nejlépe vyjadřují záměr původní návrhu. Ve skutečnosti všechny `NewsStoryViewModel` *je* správně vytvořena instance s jinou hodnotu než null. Díky tomu se následující inicializace platnou opravu kódu:

```csharp
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; } = default!;
    public string Uri { get; set; } = default!;
}
```

Přiřazení `Title` a `Uri` k `default` tedy `null` pro `string` typ nedojde ke změně chování za běhu programu. `NewsStoryViewModel` Stále zkonstruován s hodnotou null, ale teď kompilátor oznámí žádná upozornění. **Striktní null operátor**, `!` následující znak `default` výraz sděluje kompilátoru, že předcházejícího výrazu není null. Tato technika může být vhodné při další změny vynutit mnohem větší změn do základu kódu, ale v této aplikaci je poměrně rychle a lepší řešení: Ujistěte se, `NewsStoryViewModel` typem neměnné, ve kterém jsou nastavené všechny vlastnosti v konstruktoru. Proveďte následující změny `NewsStoryViewModel`:

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#FinishedViewModel)]

Po dokončení, je potřeba aktualizovat kód, který konfiguruje AutoMapper tak, aby používala konstruktoru spíše než nastavení vlastnosti. Otevřít `NewsService.cs` a vyhledejte následující kód v dolní části souboru:

[!code-csharp[StarterAutoMapper](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Že vlastnosti mapy kódu `ISyndicationItem` objektu `NewsStoryViewModel` vlastnosti. Chcete, aby AutoMapper poskytnout mapování místo toho použít konstruktor. Ve výše uvedeném kódu nahraďte následující automapper konfiguraci:

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Všimněte si, že vzhledem k tomu, že tato třída je malý a jste pečlivě prozkoumat, měli byste zapnout `#nullable enable` direktiv vyšší než tato deklarace třídy. Změna konstruktoru může mají poškozen něco, takže je vhodné spustit všechny testy a testování aplikací před přechodem na.

První sada změn vám ukázali, jak zjistit, kdy původní návrh uvedeno, že proměnné by neměl být nastavený `null`. Postup se označuje jako **správné pomocí vytváření**. Deklarujte, že objekt a jeho vlastnosti nemohou být `null` při jejím vytváření. Analýzy toku kompilátoru poskytuje záruku, že tyto vlastnosti nejsou nastaveny na `null` po konstrukci. Mějte na paměti, že tento konstruktor je volán externího kódu a tento kód je **s možnou hodnotou Null oblivious**. Nová syntaxe neposkytuje kontroly runtime. Externí kód může obejít analýzy toku kompilátoru. 

Jindy struktura třídy poskytuje různé příčiny záměr. Otevřít *Error.cshtml.cs* soubor *stránky* složky. `ErrorViewModel` Obsahuje následující kód:

[!code-csharp[StarterErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Error.cshtml.cs#StartErrorModel)]

Přidat `#nullable enable` direktiv před deklaraci třídy a `#nullable restore` direktiv po něm. Zobrazí se jedné upozornění, která `RequestId` není inicializován. Podle třídy, byste měli rozhodnout, která `RequestId` vlastnost by měla mít hodnotu null v některých případech. Existence `ShowRequestId` vlastnost označuje, že jsou možné chybějící hodnoty. Protože `null` je platný, přidejte `?` na `string` typu k označení `RequestId` vlastnost je *typ s možnou hodnotou Null odkazu*. Finální třídy bude vypadat jako v následujícím příkladu:

[!code-csharp[FinishedErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Error.cshtml.cs#ErrorModel)]

Zkontrolujte použití vlastnosti a uvidíte, že na stránce přidružené vlastnosti se kontroluje u null před vykreslením v kódu. To je bezpečné používání typu s možnou hodnotou Null odkazu, tak budete hotovi s touto třídou.

## <a name="fixing-nulls-causes-change"></a>Oprava hodnoty NULL způsobí, že změna

Oprava pro jednu sadu upozornění často, vytvoří nová upozornění v související kód. Podívejme se po opravě upozornění v akci `index.cshtml.cs` třídy. Otevřít `index.cshtml.cs` souboru a prozkoumejte kód. Tento soubor obsahuje kód za pro indexovou stránku:

[!code-csharp[StarterIndexModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Index.cshtml.cs#IndexModelStart)]

Přidat `#nullable enable` směrnice a uvidíte dvě upozornění. Ani `ErrorText` vlastnost ani `NewsItems` vlastnost inicializuje. Prozkoumání této třídy vedlo domnívat, že obě vlastnosti by měl být typy s možnou hodnotou Null odkazů: Mít privátní metody setter. Přesně jeden je přiřazen do `OnGet` metody. Před provedením změn, podívejte se na spotřebitele obě vlastnosti. V samotné stránky `ErrorText` je porovnávána s hodnotou null před vygenerováním kódu chyby. `NewsItems` Kolekce je porovnávána s `null`a kontrolovaný zajistit kolekci položek. Rychlé opravy je oba typy s možnou hodnotou NULL referenční vlastnosti. Může být lepší oprava nastavují kolekci nemá typ odkazu a přidat položky do existující kolekce při načítání zpráv. První opravu, je přidat `?` k `string` zadejte `ErrorText`:

[!code-csharp[UpdateErrorText](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#UpdateErrorText)]

Nebude změna rozšíří jiný kód, protože žádný přístup k `ErrorText` vlastnost byl již chráněn pomocí kontroly hodnoty null. V dalším kroku inicializovat `NewsItems` seznamu a odeberte metodu nastavení vlastnosti, takže vlastnost jen pro čtení:

[!code-csharp[InitializeNewsItems](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#InitializeNewsItems)]

Který opraveny upozornění však zavést chybu. `NewsItems` Je seznam **správné pomocí vytváření**, ale kód, který nastaví seznam v `OnGet` musí změnit tak, aby odpovídala nové rozhraní API. Namísto přiřazení, volání `AddRange` přidání položek zpráv do existujícího seznamu:

[!code-csharp[AddRange](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#AddRange)]

Pomocí `AddRange` namísto přiřazení znamená, že `GetNews` metoda může vrátit `IEnumerable` místo `List`. Který uloží jednu přidělení. Změna podpisu metody a odebrat `ToList` volání, jak je znázorněno v následujícím příkladu kódu:

[!code-csharp[GetNews](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#GetNewsFinished)]

Změna podpisu dělí jeden také testy. Otevřít `NewsServiceTests.cs` soubor `Services` složky `SimpleFeedReader.Tests` projektu. Přejděte `Returns_News_Stories_Given_Valid_Uri` testování a změňte typ `result` proměnnou `IEnumerable<NewsItem>`. Změna typu znamená, že `Count` vlastnost již není k dispozici, takže nahradit `Count` vlastnost `Assert` voláním `Any()`:

[!code-csharp[FixTests](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader.Tests/Services/NewsServiceTests.cs#FixTestSignature)]

Bude potřeba přidat `using System.Linq` příkaz na začátek souboru také.

Tato sada změn zvýrazní zvláštní pozornost při aktualizaci kódu, který obsahuje obecných instancích. V seznamu a prvky v seznamu typů Null. Jeden nebo oba, může být typy připouštějící hodnotu Null. Jsou povoleny všechny následující deklarace:

- `List<NewsStoryViewModel>`: nemá seznam nonullable Zobrazit modely.
- `List<NewsStoryViewModel?>`: nemá seznam modelů zobrazení s možnou hodnotou Null.
- `List<NewsStoryViewModel>?`: seznam nonnullable Zobrazit modely s možnou hodnotou Null.
- `List<NewsStoryViewModel?>?`: s možnou hodnotou Null seznamu modelů zobrazení s možnou hodnotou Null.

## <a name="interfaces-with-external-code"></a>Rozhraní s externí kód

Změny provedené `NewsService` třídy, takže zapnout `#nullable enable` anotace pro danou třídu. Nebudou se generovat žádné nové upozornění. Prohlídkou třídy pomáhá ale objasňuje některé omezení kompilátoru analýzy toku. Prozkoumejte konstruktoru:

[!code-csharp[ServiceConstructor](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ServiceConstructor)]

`IMapper` Parametr zadán jako odkaz nemá. Je volána metodou kód infrastruktury ASP.NET Core, aby kompilátor nebude vědět ve skutečnosti, že `IMapper` bude mít nikdy hodnotu null. Výchozí kontejner vkládání (DI) závislostí ASP.NET Core vyvolá výjimku, pokud nelze přeložit potřebné služby, takže kód je správný. Kompilátor nemůže ověřit všechna volání do veřejných rozhraní API, i v případě, že váš kód je zkompilován s kontexty poznámky s možnou hodnotou Null povolené. Kromě toho mohou být využívány knihoven pro projekty, které ještě nebyly přihlášení ke službě použití typů s povolenou hodnotou Null reference. Ověření vstupy pro veřejné rozhraní API, i když jste je deklarován jako typy nemá.

## <a name="get-the-code"></a>Získat kód

Vyřešili jsme upozornění jste identifikovali v počáteční test kompilace, takže teď můžete zapnout kontextu s možnou hodnotou Null Poznámka u obou projektů. Znovu sestavte projekty; Kompilátor oznámí žádná upozornění. Můžete získat kód pro dokončení projektu v [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/finished) úložiště GitHub.

Nové funkce, které podporují připouštějící hodnotu NULL referenční typy pomáhají nacházet a opravte potenciální chyby v tom, jak zpracovat `null` hodnoty ve vašem kódu. Povolení kontextu s možnou hodnotou Null poznámky umožňuje vyjádřit záměr vašeho návrhu: Některé proměnné by měl mít nikdy hodnotu null, jiné proměnné můžou obsahovat hodnoty null. Tyto funkce usnadnění deklarovat máte v úmyslu návrhu. Podobně s možnou hodnotou Null kontext upozornění instruuje kompilátor, aby upozornění na problém při mají porušení tohoto záměru. Upozornění Průvodce, abyste provedli aktualizace, které váš kód odolné a méně pravděpodobně vyvolá výjimku `NullReferenceException` během provádění. Rozsah těchto kontextech můžete řídit, abyste se mohli zaměřit na místní oblasti kódu pro migraci zbývající codebase je beze změny. V praxi můžete provést migrace úloh součástí pravidelné údržby do vaší třídy. V tomto kurzu jsme vám ukázali postup, jak migrovat aplikace pro použití s možnou hodnotou NULL referenční typy. Větší reálný příklad tohoto procesu můžete prozkoumat prozkoumáním žádosti o přijetí změn [Jon Skeet](https://github.com/jskeet) provedené obsahovat typy s možnou hodnotou Null odkazů do [NodaTime](https://github.com/nodatime/nodatime/pull/1240/commits).
