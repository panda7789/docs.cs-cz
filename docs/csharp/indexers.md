---
title: Indexery
description: Seznamte C# se s indexery a jejich implementací indexovaných vlastností, což jsou vlastnosti, na které odkazuje jeden nebo více argumentů.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: 86e646b341cf098d8621f095d4bfc9ea2191940d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039122"
---
# <a name="indexers"></a>Indexery

*Indexery* jsou podobné vlastnostem. V mnoha způsobech indexerů vytváří stejné jazykové funkce jako [vlastnosti](properties.md). Indexery povolují *indexované* vlastnosti: vlastnosti odkazované pomocí jednoho nebo více argumentů. Tyto argumenty poskytují index pro určitou kolekci hodnot.

## <a name="indexer-syntax"></a>Syntaxe indexeru

K indexeru přistupujete pomocí názvu proměnné a hranatých závorek. Argumenty indexeru umístíte do závorek:

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

Indexery deklarujete pomocí klíčového slova `this` jako názvu vlastnosti a deklarujete argumenty v hranatých závorkách. Tato deklarace by odpovídala využití uvedenému v předchozím odstavci:

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

Z tohoto počátečního příkladu můžete vidět vztah mezi syntaxí pro vlastnosti a indexery. Tato analogická průchody procházejí většinou pravidel syntaxe pro indexery. Indexery můžou mít libovolný platný modifikátor přístupu (Public, Protected Internal, Protected, Internal, private nebo Private Protected). Můžou být zapečetěné, virtuální nebo abstraktní. Stejně jako u vlastností můžete určit různé modifikátory přístupu pro přístupové objekty get a Set v indexeru.
Můžete také zadat indexery jen pro čtení (vynecháním přístupového objektu set) nebo indexerů jen pro zápis (vynecháním přístupového objektu Get).

Můžete použít téměř všechno, co se naučíte pracovat s vlastnostmi pro indexery. Jedinou výjimkou z tohoto pravidla jsou *automaticky implementované vlastnosti*. Kompilátor nemůže vždy vygenerovat správné úložiště pro indexer.

Přítomnost argumentů odkazujících na položku v sadě položek rozlišuje indexery od vlastností. Můžete definovat více indexerů pro typ, pokud je seznam argumentů pro každý indexer jedinečný. Pojďme prozkoumat různé scénáře, kde můžete použít jeden nebo více indexerů v definici třídy. 

## <a name="scenarios"></a>Scénáře

*Indexery* byste definovali v typu, když jeho model rozhraní API nějaké kolekce, kde definujete argumenty této kolekce. Indexery mohou nebo nemusí být mapovány přímo na typy kolekce, které jsou součástí rozhraní .NET Core Framework. Váš typ může kromě modelování kolekce obsahovat i další zodpovědnosti.
Indexery umožňují poskytovat rozhraní API, které odpovídá abstrakci typu, bez vystavení vnitřních podrobností o tom, jak se hodnoty pro tuto abstrakci ukládají nebo vypočítávají.

Pojďme si projít některé z běžných scénářů použití *indexerů*. K [ukázkové složce pro indexery](https://github.com/dotnet/samples/tree/master/csharp/indexers)můžete získat přístup. Pokyny ke stažení najdete v tématu [ukázky a kurzy](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

### <a name="arrays-and-vectors"></a>Pole a vektory

Jedním z nejběžnějších scénářů pro vytváření indexerů je, že typ modeluje pole nebo vektor. Můžete vytvořit indexer pro modelování seřazeného seznamu dat. 

Výhodou vytvoření vlastního indexeru je, že můžete definovat úložiště pro tuto kolekci tak, aby vyhovovalo vašim potřebám. Představte si situaci, kdy váš typ modeluje historická data, která jsou příliš velká pro načtení do paměti najednou. Musíte načíst a uvolnit části kolekce na základě využití. V následujícím příkladu jsou modely tohoto chování. Oznamuje, kolik datových bodů existuje. Vytvoří stránky pro uložení částí dat na vyžádání. Odstraní stránky z paměti a uvolní tak místo pro stránky vyžadované novějšími požadavky.

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

Můžete postupovat podle tohoto návrhu idiom a modelovat jakýkoli druh kolekce, kde jsou dobré důvody, proč nenačíst celou sadu dat do kolekce v paměti. Všimněte si, že třída `Page` je soukromá vnořená třída, která není součástí veřejného rozhraní. Tyto podrobnosti jsou skryté od všech uživatelů této třídy.

### <a name="dictionaries"></a>slovníky

Dalším běžným scénářem je situace, kdy potřebujete modelovat slovník nebo mapu. Tento scénář je v případě, že váš typ ukládá hodnoty na základě klíče, obvykle textových klíčů. Tento příklad vytvoří slovník, který mapuje argumenty příkazového řádku na [výrazy lambda](delegates-overview.md) , které spravují tyto možnosti. Následující příklad ukazuje dvě třídy: `ArgsActions` třídu, která mapuje možnost příkazového řádku na delegáta `Action` a `ArgsProcessor`, který používá `ArgsActions` ke spuštění každého `Action`, když k této možnosti dojde.

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

V tomto příkladu je kolekce `ArgsAction` úzce namapována na podkladovou kolekci.
`get` určuje, zda byla daná možnost nakonfigurována. Pokud ano, vrátí `Action` přidružené k této možnosti. Pokud ne, vrátí `Action`, který nic nedělá. Veřejný přistupující objekt nezahrnuje přistupující objekt `set`. Místo toho návrh pomocí veřejné metody pro nastavení možností.

### <a name="multi-dimensional-maps"></a>Multidimenzionální mapy

Můžete vytvořit indexery, které používají více argumentů. Kromě toho nejsou tyto argumenty omezeny na stejný typ. Pojďme se podívat na dva příklady.   

První příklad ukazuje třídu, která generuje hodnoty pro Mandelbrot sadu. Další informace o matematikě za sadou najdete v [tomto článku](https://en.wikipedia.org/wiki/Mandelbrot_set). Indexer používá dvě dvojité čárky k definování bodu v rovině X, Y.
Přistupující objekt get vypočítá počet iterací, dokud není v sadě zjištěn bod. Pokud je dosaženo maximálního počtu iterací, je bod v sadě a vrátí se hodnota maxIterations třídy. (Počítače generované obrázky, které jsou populární pro Mandelbrot sadu, definují barvy pro počet iterací potřebných k určení, jestli je bod mimo sadu.

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

Mandelbrot sada definuje hodnoty v každé souřadnici (x, y) pro hodnoty reálného čísla.
Který definuje slovník, který by mohl obsahovat nekonečný počet hodnot. Proto neexistuje žádné úložiště za sadou. Místo toho tato třída vypočítá hodnotu pro každý bod, když kód volá přistupující objekt `get`. Nepoužívá se žádné základní úložiště.

Pojďme se podívat na poslední použití indexerů, kde indexer přijímá více argumentů různých typů. Vezměte v úvahu program, který spravuje historická data o teplotě. Tento indexer používá město a datum k nastavení nebo získání vysoké a nízké teploty pro toto umístění:

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

Tento příklad vytvoří indexer, který mapuje data o počasí ve dvou různých argumentech: město (reprezentované `string`) a datum (reprezentované `DateTime`). Interní úložiště používá dvě `Dictionary` třídy k reprezentaci dvojrozměrného slovníku. Veřejné rozhraní API už nepředstavuje základní úložiště. Spíše funkce jazyka indexerů vám umožní vytvořit veřejné rozhraní, které představuje vaši abstrakci, i když základní úložiště musí používat jiné typy základních kolekcí.

Existují dvě části tohoto kódu, které mohou být někteří vývojáři Neobeznámeni. Tyto dva `using` příkazy:

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

vytvoří *alias* pro konstruovaný obecný typ. Tyto příkazy umožňují kódu později použít výstižnější `DateMeasurements` a `CityDateMeasurements` názvy namísto obecné konstrukce `Dictionary<DateTime, Measurements>` a `Dictionary<string, Dictionary<DateTime, Measurements> >`. Tento konstruktor vyžaduje použití plně kvalifikovaného názvu typu na pravé straně znaku `=`.

Druhým postupem je obložení časových částí libovolného objektu `DateTime`, který se používá k indexování do kolekcí. Rozhraní .NET Framework neobsahuje typ pouze datum.
Vývojáři používají `DateTime` typ, ale pomocí vlastnosti `Date` zajistěte, aby všechny objekty `DateTime` z tohoto dne byly stejné.

## <a name="summing-up"></a>Sčítání

Indexery byste měli vytvořit kdykoli, když máte element, který je ve vaší třídě, kde tato vlastnost představuje nejedinou hodnotu, ale spíše kolekci hodnot, kde je každá jednotlivá položka identifikována sadou argumentů. Tyto argumenty mohou jednoznačně určit, která položka v kolekci má být odkazována.
Indexery rozšiřuje koncept [vlastností](properties.md), kde se člen považuje za datovou položku z vnějšku třídy, ale jako metodu v rámci. Indexery umožňují argumentům vyhledat jednu položku ve vlastnosti, která představuje sadu položek.
