---
title: Indexery
description: Další informace o C# indexery a jak implementovat indexovaných vlastností, které jsou vlastnosti odkazovat pomocí jedné nebo více argumentů.
ms.date: 06/20/2016
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: a13163cb6bd835dfdd16c83c905c134eb8a86e7d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197597"
---
# <a name="indexers"></a>Indexery

*Indexery* jsou podobné vlastnostem. Ve spoustě ohledů indexery sestavení na stejné funkce jako jazyk [vlastnosti](properties.md). Indexery povolují *indexované* vlastnosti: vlastnosti odkazovat pomocí jedné nebo více argumentů. Tyto argumenty poskytuje index do některé kolekce hodnot.

## <a name="indexer-syntax"></a>Syntaxe indexeru

Přístup indexeru prostřednictvím název proměnné a hranaté závorky. Umístíte argumenty indexeru v závorkách:

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

Deklarovat pomocí indexerů `this` klíčového slova jako názvu vlastnosti a deklarační popisovač argumenty v hranatých závorkách. Tato deklarace odpovídají využití je znázorněno v předchozím odstavci:

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

Z tohoto počátečního příkladu uvidíte vztah mezi syntaxi pro vlastnosti a indexery. Tato analogie přenáší přes většinu pravidel syntaxe pro indexování. Indexery můžete mít libovolný platný přístupu modifikátory přístupu (veřejné, chráněné vnitřní, chráněný, interní, privátní nebo privátní chráněné). Mohou být zapečetěné, virtuální nebo abstraktní. Stejně jako u vlastnosti, můžete zadat různé přístupu modifikátory přístupu pro metodu get a přístupové objekty set v indexeru.
Můžete také zadat indexery jen pro čtení (vynecháním přístupový objekt set) nebo pouze pro zápis indexery (vynecháním přistupující objekt get).

Můžete použít téměř vše, co jste Učte se od práce s vlastnostmi pro indexery. Jedinou výjimkou tohoto pravidla je *automaticky implementované vlastnosti*. Kompilátor nemůže vždy generovat správný úložiště pro indexer.

Přítomnost argumenty odkažte na položku v sadě položek odlišuje od vlastnosti indexery. Několik indexerů může definovat podle typu, jako argument uvádí pro každý indexer je jedinečný. Podíváme na různé scénáře ve kterém můžete použít jeden nebo více indexerů v definici třídy. 

## <a name="scenarios"></a>Scénáře

Můžete definovat *indexery* v typu při jeho API modely některé kolekce, ve kterém definujete argumenty do této kolekce. Vaše indexerů může nebo nemusí mapují přímo na typy kolekcí, které jsou součástí rozhraní .NET core framework. Typ může být další úkoly, kromě modelování kolekce.
Indexery povolují, abychom vám poskytli rozhraní API, která odpovídá abstrakce váš typ bez vystavení vnitřní podrobnosti, jak jsou uložená nebo vypočítané hodnoty pro tento odběr.

Pojďme si projít některé běžné scénáře použití *indexery*. Můžete přistupovat [složky s ukázkou pro indexery](https://github.com/dotnet/samples/tree/master/csharp/indexers). Pokyny ke stažení najdete v tématu [ukázek a kurzů](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

### <a name="arrays-and-vectors"></a>Pole a vektorů

Jednou z nejběžnějších scénářů pro vytváření indexerů je modely typu pole nebo vektoru. Indexer pro modelování uspořádaný seznam dat můžete vytvořit. 

Výhoda vytváření vlastních indexeru je, že můžete definovat úložiště pro danou kolekci tak, aby odpovídala vašim potřebám. Představte si situaci, kdy váš typ modely historická data, která je příliš velký, aby najednou načíst do paměti. Budete muset načtení a uvolnění oddíly kolekce na základě využití. Následující příklad modely toto chování. Oznámí na existují jak mnoho datových bodů. Vytvoří stránky pro uložení části dat na vyžádání. Odebírá stránky z paměti, aby uvolnil prostor pro stránky vyžaduje novější požadavky.

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

Můžete postupovat podle tohoto idiomu návrhu modelovat jakýkoli druh kolekce Pokud existují oprávněné důvody nenačte celá sada dat do kolekce v paměti. Všimněte si, že `Page` třída je privátní vnořené třídy, který není součástí veřejného rozhraní. Tyto podrobnosti jsou skryté všichni uživatelé této třídy.

### <a name="dictionaries"></a>slovníky

Další z typických možností je, když budete potřebovat k modelování slovníku nebo mapy. Tento scénář je typ ukládá hodnoty na základě klíče, obvykle text klíče. Tento příklad vytvoří slovník, který mapuje argumenty příkazového řádku [výrazy lambda](delegates-overview.md) , které spravují tyto možnosti. Následující příklad ukazuje dvě třídy: `ArgsActions` třída, která mapuje možnosti příkazového řádku pro `Action` delegovat a `ArgsProcessor` , která používá `ArgsActions` ke spuštění každého `Action` při výskytu této možnosti.

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

V tomto příkladu `ArgsAction` kolekce úzce mapuje na zdrojové kolekce.
`get` Určuje-li dané možnosti není nakonfigurovaná. Pokud ano, vrátí `Action` přidružené k této možnosti. Pokud ne, vrátí `Action` , který nemá žádný účinek. Veřejný přístupový objekt neobsahuje `set` přistupujícího objektu. Místo toho návrh s použitím veřejné metody pro nastavení možností.

### <a name="multi-dimensional-maps"></a>Multidimenzionální mapy

Můžete vytvořit indexerů, které používají více argumentů. Kromě toho tyto argumenty nejsou omezeny na být stejného typu. Pojďme se podívat na dva příklady.   

První příklad ukazuje třídu, která generuje hodnoty pro skupinu Mandelbrot. Další informace o matematiku za čtení [v tomto článku](https://en.wikipedia.org/wiki/Mandelbrot_set). Indexer používá dvě Double pro definování bod v X, Y roviny.
Přístupový objekt get vypočítá počet iterací, dokud se určuje bod tak, aby nebyl v sadě. Pokud je dosažen maximální počet iterací, bod nachází v sadě a vrátí se hodnota maxIterations třídy. (Počítače, generovány Image, který pro sadu Mandelbrot definovat barvy pro počet iterací, které jsou nezbytné k určení, že bod je mimo sadu.

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

Sada Mandelbrot definuje hodnoty v každé (x, y) koordinovat skutečných číselné hodnoty.
Který definuje slovník, který může obsahovat neomezený počet hodnot. Proto neexistuje žádné úložiště za sady. Místo toho tuto třídu vypočítá hodnotu pro každý bod, když kód volá `get` přistupujícího objektu. Neexistuje žádný použité úložiště.

Podívejme se na poslední užívání indexery, kdy indexer využívá více argumentů různých typů. Vezměte v úvahu program, který spravuje data o teplotě historických. Indexer využívá Město a datum nastavit nebo získat teploty vysoké a nízké pro toto umístění:

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

Tento příklad vytvoří indexer, který mapuje data o počasí na dva různé argumenty: města (reprezentované `string`) a data (reprezentované `DateTime`). Interní úložiště používá dvě `Dictionary` třídy, které představují dvojrozměrné slovníku. Veřejné rozhraní API už nebude představuje základní úložiště. Místo toho funkce jazyků indexerů umožňuje vytvářet veřejné rozhraní, která představuje abstrakci, i když základního úložiště musí používat různé základní typy kolekcí.

Existují dvě části tohoto kódu, který může být obeznámeni pro některé vývojáře. Tyto dvě `using` příkazy:

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

vytvoření *alias* pro Konstruovaný obecný typ. Tyto příkazy Povolit kódu později použít více popisné `DateMeasurements` a `CityDateMeasurements` názvy místo obecné konstrukce `Dictionary<DateTime, Measurements>` a `Dictionary<string, Dictionary<DateTime, Measurements> >`. Tento konstruktor vyžaduje použití názvů plně kvalifikovaný typ na pravé straně `=` přihlašování.

Druhý postup je pro odstranění vypnout části času žádné `DateTime` objekt použitý k indexu do kolekce. Rozhraní .NET framework nezahrnuje jediný typ Date.
Vývojáři `DateTime` typu, ale použít `Date` vlastnost a zkontrolujte, že některé `DateTime` objektu v daný den jsou stejné.

## <a name="summing-up"></a>Shrnutí

Indexery byste měli vytvořit kdykoli mít element jako vlastnost ve své třídě, kde tato vlastnost představuje jednu hodnotu, ale spíše kolekci hodnot, kde jednotlivé položky je identifikován sady argumentů. Tyto argumenty může jedinečně identifikovat, která položka v kolekci by se měla odkazovat.
Indexery rozšířit koncept [vlastnosti](properties.md), kdy je člen zpracován jako položku dat z vně třídy, ale jako metody na straně. Indexery povolit argumenty k nalezení konkrétní položce v vlastnost, která představuje sadu položek.
