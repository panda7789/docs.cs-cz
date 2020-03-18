---
title: Indexery
description: Další informace o indexery Jazyka C# a jak implementují indexované vlastnosti, které jsou vlastnosti odkazuje pomocí jednoho nebo více argumentů.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: 8e583b8a7cedab61ea6fdd56587608907610b6b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145681"
---
# <a name="indexers"></a>Indexery

*Indexery* jsou podobné vlastnostem. V mnoha ohledech indexery stavět na stejné jazykové funkce jako [vlastnosti](properties.md). Indexery umožňují *indexované* vlastnosti: vlastnosti odkazované pomocí jednoho nebo více argumentů. Tyto argumenty poskytují index do některé kolekce hodnot.

## <a name="indexer-syntax"></a>Syntaxe indexeru

K indexeru přistupujete prostřednictvím názvu proměnné a hranatých závorek. Argumenty indexeru umístíte do závorek:

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

Deklarujete `this` indexery pomocí klíčového slova jako název vlastnosti a deklaruje argumenty v rámci hranaté závorky. Toto prohlášení by odpovídalo použití uvedenému v předchozím odstavci:

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

Z tohoto počátečního příkladu můžete zobrazit vztah mezi syntaxí pro vlastnosti a indexery. Tato analogie nese přes většinu syntaxe pravidla pro indexery. Indexery mohou mít všechny platné modifikátory přístupu (veřejné, chráněné interní, chráněné, interní, soukromé nebo soukromé chráněné. Mohou být zapečetěné, virtuální nebo abstraktní. Stejně jako u vlastností můžete určit různé modifikátory přístupu pro přístupové objekty get a set v indexeru.
Můžete také zadat indexery jen pro čtení (vynecháním přístupového zařízení set) nebo indexery pouze pro zápis (vynecháním přístupového orátele get).

Můžete použít téměř vše, co se naučíte z práce s vlastnostmi na indexery. Jedinou výjimkou z tohoto pravidla jsou *automaticky implementované vlastnosti*. Kompilátor nemůže vždy generovat správné úložiště pro indexer.

Přítomnost argumentů odkazna položku v sadě položek odlišuje indexery od vlastností. Můžete definovat více indexerů na typu, tak dlouho, dokud seznamy argumentů pro každý indexer je jedinečný. Pojďme prozkoumat různé scénáře, kde můžete použít jeden nebo více indexerů v definici třídy.

## <a name="scenarios"></a>Scénáře

Byste definovat *indexery* v typu, když jeho rozhraní API modely některé kolekce, kde definujete argumenty pro tuto kolekci. Indexery může nebo nemusí mapovat přímo na typy kolekce, které jsou součástí rozhraní .NET core framework. Váš typ může mít další odpovědnosti kromě modelování kolekce.
Indexery umožňují poskytnout rozhraní API, které odpovídá abstrakce vašeho typu bez vystavení vnitřní podrobnosti o tom, jak jsou uloženy nebo vypočítány hodnoty pro abstrakce.

Pojďme projít některé běžné scénáře pro použití *indexery*. Můžete získat přístup ke [vzorové složce indexerů](https://github.com/dotnet/samples/tree/master/csharp/indexers). Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

### <a name="arrays-and-vectors"></a>Pole a vektory

Jedním z nejběžnějších scénářů pro vytváření indexerů je, když váš typ modely pole nebo vektor. Můžete vytvořit indexer pro modelování seřazeného seznamu dat.

Výhodou vytvoření vlastního indexeru je, že můžete definovat úložiště pro tuto kolekci tak, aby vyhovovalo vašim potřebám. Představte si scénář, kde váš typ modely historických dat, která je příliš velká pro načtení do paměti najednou. Je třeba načíst a uvolnit části kolekce na základě využití. Příklad následující modely toto chování. Informuje o tom, kolik datových bodů existuje. Vytvoří stránky pro uložení částí dat na vyžádání. Odstraňuje stránky z paměti, aby se uvolnilo místo pro stránky potřebné novějšími požadavky.

```csharp
public class DataSamples
{
    private class Page
    {
        private readonly List<Measurements> pageData = new List<Measurements>();
        private readonly int startingIndex;
        private readonly int length;
        private bool dirty;
        private DateTime lastAccess;

        public Page(int startingIndex, int length)
        {
            this.startingIndex = startingIndex;
            this.length = length;
            lastAccess = DateTime.Now;

            // This stays as random stuff:
            var generator = new Random();
            for(int i=0; i < length; i++)
            {
                var m = new Measurements
                {
                    HiTemp = generator.Next(50, 95),
                    LoTemp = generator.Next(12, 49),
                    AirPressure = 28.0 + generator.NextDouble() * 4
                };
                pageData.Add(m);
            }
        }
        public bool HasItem(int index) =>
            ((index >= startingIndex) &&
            (index < startingIndex + length));

        public Measurements this[int index]
        {
            get
            {
                lastAccess = DateTime.Now;
                return pageData[index - startingIndex];
            }
            set
            {
                pageData[index - startingIndex] = value;
                dirty = true;
                lastAccess = DateTime.Now;
            }
        }

        public bool Dirty => dirty;
        public DateTime LastAccess => lastAccess;
    }

    private readonly int totalSize;
    private readonly List<Page> pagesInMemory = new List<Page>();

    public DataSamples(int totalSize)
    {
        this.totalSize = totalSize;
    }

    public Measurements this[int index]
    {
        get
        {
            if (index < 0)
                throw new IndexOutOfRangeException("Cannot index less than 0");
            if (index >= totalSize)
                throw new IndexOutOfRangeException("Cannot index past the end of storage");

            var page = updateCachedPagesForAccess(index);
            return page[index];
        }
        set
        {
            if (index < 0)
                throw new IndexOutOfRangeException("Cannot index less than 0");
            if (index >= totalSize)
                throw new IndexOutOfRangeException("Cannot index past the end of storage");
            var page = updateCachedPagesForAccess(index);

            page[index] = value;
        }
    }

    private Page updateCachedPagesForAccess(int index)
    {
        foreach (var p in pagesInMemory)
        {
            if (p.HasItem(index))
            {
                return p;
            }
        }
        var startingIndex = (index / 1000) * 1000;
        var newPage = new Page(startingIndex, 1000);
        addPageToCache(newPage);
        return newPage;
    }

    private void addPageToCache(Page p)
    {
        if (pagesInMemory.Count > 4)
        {
            // remove oldest non-dirty page:
            var oldest = pagesInMemory
                .Where(page => !page.Dirty)
                .OrderBy(page => page.LastAccess)
                .FirstOrDefault();
            // Note that this may keep more than 5 pages in memory
            // if too much is dirty
            if (oldest != null)
                pagesInMemory.Remove(oldest);
        }
        pagesInMemory.Add(p);
    }
}
```

Můžete sledovat tento návrh idiom modelovat jakýkoli druh kolekce, kde existují dobré důvody, proč nenačíst celou sadu dat do kolekce v paměti. Všimněte `Page` si, že třída je soukromá vnořená třída, která není součástí veřejného rozhraní. Tyto podrobnosti jsou skryty před všemi uživateli této třídy.

### <a name="dictionaries"></a>Slovníky

Dalším běžným scénářem je, když potřebujete modelovat slovník nebo mapu. Tento scénář je, když váš typ ukládá hodnoty na základě klíče, obvykle textové klíče. Tento příklad vytvoří slovník, který mapuje argumenty příkazového řádku na [výrazy lambda,](delegates-overview.md) které tyto možnosti spravují. Následující příklad ukazuje dvě `ArgsActions` třídy: třída, která `Action` mapuje možnost `ArgsProcessor` příkazového `ArgsActions` řádku `Action` delegátovi a která používá ke spuštění každé z nich, když narazí na tuto možnost.

```csharp
public class ArgsProcessor
{
    private readonly ArgsActions actions;

    public ArgsProcessor(ArgsActions actions)
    {
        this.actions = actions;
    }

    public void Process(string[] args)
    {
        foreach(var arg in args)
        {
            actions[arg]?.Invoke();
        }
    }

}
public class ArgsActions
{
    readonly private Dictionary<string, Action> argsActions = new Dictionary<string, Action>();

    public Action this[string s]
    {
        get
        {
            Action action;
            Action defaultAction = () => {} ;
            return argsActions.TryGetValue(s, out action) ? action : defaultAction;
        }
    }

    public void SetOption(string s, Action a)
    {
        argsActions[s] = a;
    }
}
```

V tomto příkladu `ArgsAction` kolekce mapuje úzce základní kolekce.
Určuje, `get` zda byla nakonfigurována daná možnost. Pokud ano, vrátí `Action` přidružené s tou možností. Pokud ne, vrátí, `Action` který neprovede nic. Veřejný přistupující odkaz `set` neobsahuje přistupující ho. Spíše návrh pomocí veřejné metody pro nastavení možností.

### <a name="multi-dimensional-maps"></a>Vícerozměrné mapy

Můžete vytvořit indexery, které používají více argumentů. Kromě toho tyto argumenty nejsou omezeny být stejného typu. Podívejme se na dva příklady.

První příklad ukazuje třídu, která generuje hodnoty pro sadu Mandelbrot. Další informace o matematice za sadou naleznete v [tomto článku](https://en.wikipedia.org/wiki/Mandelbrot_set).
Indexer používá dvě dvojníky k definování bodu v rovině X, Y.
Get přistupující ho vypočítá počet iterací, dokud bod je určen není v sadě. Pokud je dosaženo maximální iterace, bod je v sadě a je vrácena hodnota maxIterations třídy. (Počítačem generované obrázky popularizované pro sadu Mandelbrot definují barvy pro počet iterací potřebných k určení, že bod je mimo sadu.

```csharp
public class Mandelbrot
{
    readonly private int maxIterations;

    public Mandelbrot(int maxIterations)
    {
        this.maxIterations = maxIterations;
    }

    public int this [double x, double y]
    {
        get
        {
            var iterations = 0;
            var x0 = x;
            var y0 = y;

            while ((x*x + y * y < 4) &&
                (iterations < maxIterations))
            {
                var newX = x * x - y * y + x0;
                y = 2 * x * y + y0;
                x = newX;
                iterations++;
            }
            return iterations;
        }
    }
}
```

Sada Mandelbrot definuje hodnoty na každé souřadnici (x,y) pro hodnoty reálných čísel.
To definuje slovník, který by mohl obsahovat nekonečný počet hodnot. Proto neexistuje žádné úložiště za sadu. Místo toho tato třída vypočítá hodnotu pro `get` každý bod při volání kódu přistupujícího pole. Není použito žádné podkladové úložiště.

Podívejme se na poslední použití indexery, kde indexer trvá více argumentů různých typů. Vezměme si program, který spravuje historická data teploty. Tento indexer používá město a datum pro nastavení nebo získání vysokých a nízkých teplot pro toto umístění:

```csharp
using DateMeasurements =
    System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements =
    System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;

public class HistoricalWeatherData
{
    readonly CityDataMeasurements storage = new CityDataMeasurements();

    public Measurements this[string city, DateTime date]
    {
        get
        {
            var cityData = default(DateMeasurements);

            if (!storage.TryGetValue(city, out cityData))
                throw new ArgumentOutOfRangeException(nameof(city), "City not found");

            // strip out any time portion:
            var index = date.Date;
            var measure = default(Measurements);
            if (cityData.TryGetValue(index, out measure))
                return measure;
            throw new ArgumentOutOfRangeException(nameof(date), "Date not found");
        }
        set
        {
            var cityData = default(DateMeasurements);

            if (!storage.TryGetValue(city, out cityData))
            {
                cityData = new DateMeasurements();
                storage.Add(city, cityData);
            }

            // Strip out any time portion:
            var index = date.Date;
            cityData[index] = value;
        }
    }
}
```

Tento příklad vytvoří indexer, který mapuje data o počasí na `string`dva různé argumenty: `DateTime`město (reprezentované ) a datum (reprezentované ). Vnitřní úložiště používá `Dictionary` dvě třídy představují dvojrozměrný slovník. Veřejné rozhraní API již představuje základní úložiště. Spíše jazykové funkce indexerů umožňuje vytvořit veřejné rozhraní, které představuje abstrakce, i když základní úložiště musí používat různé typy základní kolekce.

Existují dvě části tohoto kódu, které mohou být neznámé pro některé vývojáře. Tato `using` dvě prohlášení:

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

vytvořte *alias* pro vytvořený obecný typ. Tyto příkazy umožňují kód později použít `DateMeasurements` více `CityDateMeasurements` popisné a názvy namísto obecné konstrukce `Dictionary<DateTime, Measurements>` a `Dictionary<string, Dictionary<DateTime, Measurements> >`.
Tato konstrukce vyžaduje použití plně kvalifikovaných názvů typů `=` na pravé straně znaménko.

Druhá technika je odstranit časové části libovolný `DateTime` objekt, který slouží k indexování do kolekcí. Rozhraní .NET neobsahuje typ pouze pro datum.
Vývojáři `DateTime` používají typ, `Date` ale použít vlastnost `DateTime` k zajištění, že všechny objekty z tohoto dne jsou stejné.

## <a name="summing-up"></a>Sečtením

Indexery byste měli vytvořit kdykoli máte prvek podobný vlastnosti ve vaší třídě, kde tato vlastnost nepředstavuje jednu hodnotu, ale spíše kolekci hodnot, kde je každá jednotlivá položka identifikována sadou argumentů. Tyto argumenty lze jednoznačně určit, která položka v kolekci by měla být odkazována.
Indexery rozšířit koncept [vlastností](properties.md), kde člen je zpracována jako datové položky mimo třídu, ale jako metoda na vnitřní straně. Indexery umožňují argumentům najít jednu položku ve vlastnosti, která představuje sadu položek.
