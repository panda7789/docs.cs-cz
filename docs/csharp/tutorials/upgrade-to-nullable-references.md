---
title: Upgrade na typy odkazů s možnou hodnotou null
description: Tento pokročilý kurz ukazuje, jak migrovat existující kód s typy odkazů s možnou hodnotou null.
ms.date: 02/19/2019
ms.technology: csharp-null-safety
ms.custom: mvc
ms.openlocfilehash: 9767493059623e770cc100b83b9284e8d0bdf0f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156451"
---
# <a name="tutorial-migrate-existing-code-with-nullable-reference-types"></a>Kurz: Migrace existujícího kódu s typy odkazů s možnou hodnotou null

C# 8 zavádí **typy odkazů s možnou hodnotou null**, které doplňují typy odkazů stejným způsobem typy hodnot s možnou hodnotou null. Deklarujete proměnnou jako **typ odkazu s možnou hodnotou null** připojením typu a. `?` Například `string?` představuje hodnotu `string`nullable . Tyto nové typy můžete použít k jasněji vyjádřit záměr návrhu: některé proměnné *musí mít vždy hodnotu*, jiné *mohou chybět hodnotu*. Všechny existující proměnné typu odkazu by byly interpretovány jako typ odkazu s hodnotou nes hotelnou hodnotou null.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Povolte kontroly nulového odkazu při práci s kódem.
> - Diagnostikovat a opravit různá upozornění týkající se hodnoty null.
> - Spravujte rozhraní mezi povolenými a zakázanými kontexty s možnou hodnotou null.
> - Řídit kontexty poznámk y s možnou hodnotou null.

## <a name="prerequisites"></a>Požadavky

Budete muset nastavit počítač pro spuštění .NET Core, včetně kompilátoru C# 8.0. Kompilátor Jazyka C# 8 je k dispozici počínaje [sadou Visual Studio 2019 verze 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).

Tento kurz předpokládá, že jste obeznámeni s C# a .NET, včetně Visual Studio nebo .NET Core CLI.

## <a name="explore-the-sample-application"></a>Prozkoumejte ukázkovou aplikaci

Ukázková aplikace, kterou budete migrovat, je webová aplikace pro čtení informačních kanálů RSS. Čte z jednoho informačního kanálu RSS a zobrazuje souhrny nejnovějších článků. Můžete si vybrat některý z článků k návštěvě webu. Aplikace je relativně nová, ale byla zapsána před použitím typů odkazů s možnou hodnotou null. Rozhodnutí o návrhu aplikace představovala zásady zvuku, ale nevyužívají tuto důležitou jazykovou funkci.

Ukázková aplikace obsahuje knihovnu testování částí, která ověřuje hlavní funkce aplikace. Tento projekt usnadní bezpečné upgradování, pokud změníte některou z implementací na základě generovaných upozornění. Startovací kód si můžete stáhnout z úložiště [GitHub dotnet/samples.](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/start)

Vaším cílem migrace projektu by mělo být využití nové funkce jazyka tak, aby jasně vyjádřit svůj záměr na nullability proměnných a tak učinit takovým způsobem, že kompilátor negeneruje `enabled`upozornění, pokud máte nullable kontext poznámky a nullable upozornění kontextu nastavena na .

## <a name="upgrade-the-projects-to-c-8"></a>Upgrade projektů na C# 8

Dobrým prvním krokem je určení rozsahu úlohy migrace. Začněte upgradem projektu na C# 8.0 (nebo novější). Přidejte `LangVersion` prvek do PropertyGroup v souborech csproj pro webový projekt i projekt testování částí:

```xml
<LangVersion>8.0</LangVersion>
```

Upgrade jazykové verze vybere C# 8.0, ale nepovolí kontext poznámky s možnou hodnotou null nebo kontext upozornění s možnou hodnotou null. Znovu sestavit projekt a zajistit, že se staví bez upozornění.

Dobrým dalším krokem je zapnout kontext poznámky s možnou hodnotou null a zjistit, kolik upozornění je generováno. Přidejte následující prvek do obou csproj souborů `LangVersion` v řešení, přímo pod element:

```xml
<Nullable>enable</Nullable>
```

Proveďte testovací sestavení a všimněte si seznamu upozornění. V této malé aplikaci kompilátor generuje pět upozornění, takže je pravděpodobné, že byste ponechat kontext poznámky s možnou hodnotou null povoleno a začít opravovat upozornění pro celý projekt.

Tato strategie funguje pouze u menších projektů. Pro všechny větší projekty počet upozornění generovaných povolením kontextu poznámky s možnou hodnotou null pro celý základ kódu ztěžuje systematickou opravu upozornění. U větších projektů organizace budete často chtít migrovat jeden projekt po druhém. V každém projektu migrujte jednu třídu nebo soubor najednou.

## <a name="warnings-help-discover-original-design-intent"></a>Upozornění pomáhají zjistit původní záměr návrhu

Existují dvě třídy, které generují více upozornění. Začni `NewsStoryViewModel` s hodinou. Odeberte `Nullable` prvek z obou souborů csproj, abyste mohli omezit rozsah upozornění na části kódu, se kterými pracujete. Otevřete soubor *NewsStoryViewModel.cs* a přidejte následující direktivy, `NewsStoryViewModel` které povolí kontext poznámky s možnou hodnotou null pro a obnovení podle této definice třídy:

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

Tyto dvě směrnice vám pomohou soustředit úsilí o migraci. Upozornění s možnou hodnotou null jsou generována pro oblast kódu, na které aktivně pracujete. Necháte je zapnuté, dokud nebudete připraveni zapnout varování pro celý projekt. Měli byste `restore` použít `disable` spíše než hodnotu, abyste později omylem nezakázali kontext, když jste zapnuli poznámky s možnou hodnotou null pro celý projekt. Po zapnutí kontextu poznámky s možnou hodnotou null pro celý `#nullable` projekt můžete odebrat všechny pragmy z tohoto projektu.

Třída `NewsStoryViewModel` je objekt přenosu dat (DTO) a dvě vlastnosti jsou řetězce pro čtení a zápis:

[!code-csharp[InitialViewModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#StarterViewModel)]

Tyto dvě `CS8618`vlastnosti způsobit , "Vlastnost nes platnou hodnotou null je neinicializován". To je dostatečně jasné: obě `string` vlastnosti `null` mají `NewsStoryViewModel` výchozí hodnotu při vytvoření. Co je důležité zjistit, `NewsStoryViewModel` je, jak jsou vytvořeny objekty. Při pohledu na tuto třídu `null` nelze zjistit, zda je hodnota součástí návrhu nebo pokud jsou tyto objekty nastaveny na hodnoty bez nuly při každém vytvoření. Novinky příběhy jsou vytvořeny `GetNews` v `NewsService` metodě třídy:

[!code-csharp[StarterCreateNewsItem](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#CreateNewsItem)]

V předchozím bloku kódu se toho děje docela dost. Tato aplikace používá balíček [AutoMapper](https://automapper.org/) NuGet k `ISyndicationItem`vytvoření zpravodajské položky z . Zjistili jste, že položky zpravodajského příběhu jsou vytvořeny a vlastnosti jsou nastaveny v tomto jednom příkazu. To znamená, že `NewsStoryViewModel` návrh pro označuje, `null` že tyto vlastnosti by nikdy mít hodnotu. Tyto vlastnosti by měly být **neplatné typy odkazů**. To nejlépe vyjadřuje původní záměr návrhu. Ve skutečnosti `NewsStoryViewModel` *je* každý správně vytvořena s hodnotami bez nuly. Díky tomu je následující inicializační kód platnou opravou:

```csharp
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; } = default!;
    public string Uri { get; set; } = default!;
}
```

`Title` Přiřazení a `Uri` `default` na který `null` je `string` pro typ nezmění chování za běhu programu. Je `NewsStoryViewModel` stále konstruována s hodnotami null, ale nyní kompilátor hlásí žádná upozornění. **Operátor null odpouštějící** `!` , znak `default` za výrazem říká kompilátoru, že předchozí výraz není null. Tato technika může být účelná, když jiné změny vynucují mnohem větší změny základu `NewsStoryViewModel` kódu, ale v této aplikaci je relativně rychlé a lepší řešení: Vytvořte neměnný typ, kde jsou všechny vlastnosti nastaveny v konstruktoru. Proveďte následující změny `NewsStoryViewModel`v :

[!code-csharp[FinishedViewModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#FinishedViewModel)]

Jakmile je to hotovo, je třeba aktualizovat kód, který konfiguruje AutoMapper tak, aby používá konstruktor spíše než nastavení vlastností. Otevřete `NewsService.cs` a vyhledejte následující kód v dolní části souboru:

[!code-csharp[StarterAutoMapper](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Tento kód mapuje `ISyndicationItem` vlastnosti `NewsStoryViewModel` objektu na vlastnosti. Chcete, aby automapper poskytnout mapování pomocí konstruktoru místo. Nahraďte výše uvedený kód následující konfigurací automapperu:

[!code-csharp[FinishedViewModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Všimněte si, že vzhledem k tomu, že tato `#nullable enable` třída je malá a pečlivě jste prozkoumali, měli byste zapnout direktivu nad touto deklarací třídy. Změna konstruktoru mohla něco rozbít, takže stojí za to spustit všechny testy a otestovat aplikaci před přechodem.

První sada změn ukázala, jak zjistit, kdy původní návrh naznačil, že `null`proměnné by neměly být nastaveny na . Tato technika je **označována jako správná konstrukcí**. Deklarujete, že `null` objekt a jeho vlastnosti nemůže být, když je vytvořen. Analýza toku kompilátoru poskytuje záruku, že `null` tyto vlastnosti nejsou nastaveny na po výstavbě. Všimněte si, že tento konstruktor je volána externí kód a že kód je **nula nevšímavý**. Nová syntaxe neposkytuje kontrolu za běhu. Externí kód může obejít analýzu toku kompilátoru.

Jindy struktura třídy poskytuje různé stopy k záměru. Otevřete *soubor Error.cshtml.cs* ve složce *Stránky.* Obsahuje `ErrorViewModel` následující kód:

[!code-csharp[StarterErrorModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Error.cshtml.cs#StartErrorModel)]

Přidejte `#nullable enable` direktivu před `#nullable restore` deklaraci třídy a za ní direktivu. Dostanete jedno upozornění, `RequestId` které není inicializováno. Při pohledu na třídu, `RequestId` měli byste se rozhodnout, že vlastnost by měla být null v některých případech. Existence vlastnosti `ShowRequestId` označuje, že chybějící hodnoty jsou možné. Protože `null` je platný, `?` přidejte `string` na `RequestId` typ označující vlastnost je *typ odkazu s možnou hodnotou null*. Poslední třída vypadá jako následující příklad:

[!code-csharp[FinishedErrorModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Error.cshtml.cs#ErrorModel)]

Zkontrolujte použití vlastnosti a uvidíte, že na přidružené stránce je vlastnost zkontrolována na hodnotu null před vykreslením ve značkách. To je bezpečné použití typu odkazu s možnou hodnotou null, takže jste hotovi s touto třídou.

## <a name="fixing-nulls-causes-change"></a>Oprava nuly způsobí změnu

Oprava pro jednu sadu upozornění často vytváří nová upozornění v souvisejícím kódu. Podívejme se na varování v `index.cshtml.cs` akci opravou třídy. Otevřete `index.cshtml.cs` soubor a zkontrolujte kód. Tento soubor obsahuje kód, který je pro stránku indexu:

[!code-csharp[StarterIndexModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Index.cshtml.cs#IndexModelStart)]

Přidejte `#nullable enable` direktivu a zobrazí se dvě upozornění. Vlastnost ani `ErrorText` `NewsItems` vlastnost není inicializována. Zkoumání této třídy by vést k domněnce, že obě vlastnosti by měly být typy odkazů s možnou hodnotou null: Oba mají soukromé setters. Přesně jeden je `OnGet` přiřazen v metodě. Před provedením změn se podívejte na spotřebitele obou vlastností. Na samotné stránce `ErrorText` je kontrolována proti null před generováním značky pro všechny chyby. Kolekce `NewsItems` je kontrolována `null`proti , a kontrolována, aby bylo zajištěno, že kolekce obsahuje položky. Rychlou opravou by bylo, aby obě vlastnosti s možnou hodnotou null typy odkazů. Lepší oprava by bylo vytvořit kolekce neplatný typ odkazu a přidat položky do existující kolekce při načítání novinek. První oprava je přidat `?` do `string` typu `ErrorText`pro :

[!code-csharp[UpdateErrorText](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#UpdateErrorText)]

Tato změna nebude zvlnění prostřednictvím jiného `ErrorText` kódu, protože jakýkoli přístup k vlastnosti byl již střežen null kontroly. Dále inicializovat `NewsItems` seznam a odebrat setter vlastností, takže je vlastnost jen pro čtení:

[!code-csharp[InitializeNewsItems](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#InitializeNewsItems)]

To opravilo varování, ale zavedlo chybu. Seznam `NewsItems` je nyní **správné podle konstrukce**, ale `OnGet` kód, který nastaví seznam v musí změnit tak, aby odpovídaly nové rozhraní API. Místo přiřazení volejte `AddRange` a přidejte novinky do existujícího seznamu:

[!code-csharp[AddRange](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#AddRange)]

Použití `AddRange` namísto přiřazení znamená, že `GetNews` `IEnumerable` metoda může `List`vrátit místo . To šetří jednu alokaci. Změňte podpis metody a odeberte `ToList` volání, jak je znázorněno v následujícím příkladu kódu:

[!code-csharp[GetNews](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#GetNewsFinished)]

Změna podpisu přeruší jeden z testů také. Otevřete `NewsServiceTests.cs` soubor `Services` ve složce `SimpleFeedReader.Tests` projektu. Přejděte `Returns_News_Stories_Given_Valid_Uri` na test a změňte `IEnumerable<NewsItem>`typ proměnné na `result` . Změna typu `Count` znamená, že vlastnost již není `Count` k `Assert` dispozici, proto `Any()`vlastnost v písmenu a) nahraďte voláním :

[!code-csharp[FixTests](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader.Tests/Services/NewsServiceTests.cs#FixTestSignature)]

Na začátek souboru `using System.Linq` budete muset také přidat příkaz.

Tato sada změn upozorňuje zvláštní pozornost při aktualizaci kódu, který zahrnuje obecné instance. Seznam a prvky v seznamu typů s nulovou hodnotou. Buď nebo oba mohou být typy s možnou hodnotou null. Jsou povolena všechna tato prohlášení:

- `List<NewsStoryViewModel>`: neplatný seznam modelů zobrazení, které nelze utnout.
- `List<NewsStoryViewModel?>`: neplatný seznam modelů zobrazení s možnou hodnotou null.
- `List<NewsStoryViewModel>?`: seznam neplatných modelů zobrazení s možnou neplatnou platnosti.
- `List<NewsStoryViewModel?>?`: seznam modelů zobrazení s možnou hodnotou null.

## <a name="interfaces-with-external-code"></a>Rozhraní s externím kódem

Provedli jste změny `NewsService` ve třídě, proto `#nullable enable` zapněte poznámky pro tuto třídu. Tím se nevygenerují žádná nová upozornění. Pečlivé zkoumání třídy však pomáhá ilustrovat některá omezení analýzy toku kompilátoru. Zkontrolujte konstruktor:

[!code-csharp[ServiceConstructor](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ServiceConstructor)]

Parametr `IMapper` je zadán jako neplatný odkaz. Nazývá se ASP.NET základní infrastruktury kódu, takže kompilátor není `IMapper` opravdu vědět, že nikdy nebude null. Výchozí ASP.NET kontejner uzákladní ho vkládání závislostí (DI) vyvolá výjimku, pokud nemůže vyřešit potřebnou službu, takže kód je správný. Kompilátor nemůže ověřit všechna volání veřejných rozhraní API, i když je váš kód zkompilován s povolenými kontexty poznámk s možnou hodnotou null. Kromě toho mohou být vaše knihovny spotřebovány projekty, které se ještě nerozhodly používat referenční typy s možnou hodnotou null. Ověřte vstupy pro veřejná api, i když jste je deklarovali jako neplatné typy.

## <a name="get-the-code"></a>Získání kódu

Opravili jste upozornění, která jste identifikovali v počátečním testu kompilace, takže nyní můžete zapnout kontext poznámky s možnou hodnotou null pro oba projekty. Znovu sestavit projekty; kompilátor nehlásí žádná upozornění. Kód pro dokončený projekt můžete získat v úložišti [GitHub dotnet/samples.](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/finished)

Nové funkce, které podporují typy odkazů s možnou hodnotou `null` null, vám pomohou najít a opravit potenciální chyby v tom, jak zpracováváte hodnoty v kódu. Povolení kontextu poznámky s možnou hodnotou null umožňuje vyjádřit záměr návrhu: některé proměnné by nikdy neměly být nulové, jiné proměnné mohou obsahovat hodnoty null. Tyto funkce usnadňují deklarování záměru návrhu. Podobně kontext upozornění s možnou hodnotou null instruuje kompilátor udělit upozornění, pokud jste porušili tento záměr. Tato upozornění vás k provedení aktualizací, které váš kód `NullReferenceException` odolnější a méně pravděpodobné, že vyvolat během provádění. Můžete řídit rozsah těchto kontextů tak, aby se můžete zaměřit na místní oblasti kódu migrovat, zatímco zbývající základ kódu je nedotčena. V praxi můžete tento úkol migrace součást pravidelné údržby do tříd. Tento kurz demonstroval proces migrace aplikace pro použití typů odkazů s možnou hodnotou null. Můžete prozkoumat větší real-svět příklad tohoto procesu zkoumáním PR [Jon Skeet](https://github.com/jskeet) se začlenit nullable typy odkazů do [NodaTime](https://github.com/nodatime/nodatime/pull/1240/commits). Nebo jen kromě toho můžete naučit techniky pro použití typů odkazů s možnou hodnotou null s entity framework core v [entity framework core - práce s typy odkazů s možnou hodnotou null](/ef/core/miscellaneous/nullable-reference-types).
