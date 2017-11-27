---
title: Indexery
description: "Další informace o indexery C# a jak implementovat indexovaných vlastností, které jsou vlastnosti odkazovat pomocí jednoho nebo více argumentů."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: 32e090524f414ef93b8481a8ad356b313191d8b9
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2017
---
# <a name="indexers"></a>Indexery

*Indexery* jsou podobná vlastnosti. V mnoha směrech indexery sestavení na stejné funkce jazyka jako [vlastnosti](properties.md). Povolit indexery *indexované* vlastnosti: vlastnosti odkazovat pomocí jednoho nebo více argumentů. Těchto argumentů zadejte index do některé kolekce hodnot.

## <a name="indexer-syntax"></a>Indexer syntaxe

Indexer přistupujete prostřednictvím název proměnné a hranaté závorky. Umístěte argumenty indexer v závorkách:

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

Deklarovat indexery pomocí `this` – klíčové slovo jako název vlastnosti a deklarace argumenty v rámci hranaté závorky. Toto prohlášení odpovídá využití uvedené v předchozím odstavci:

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

Z tohoto příkladu počáteční uvidíte vztah mezi syntaxe pro vlastnosti a indexery. Tato analogie představuje prostřednictvím většiny pravidel syntaxe pro indexování. Indexery může mít libovolný platný přístup modifikátory (veřejné, chráněné interní, chráněné, interní, privátní nebo privátní chráněné). Se může být zapečetěné, virtuální nebo abstraktní. Stejně jako u vlastnosti, můžete zadat jiný přístup modifikátory pro get a nastavit accesssors v indexer.
Můžete také určit indexery jen pro čtení (Díky vynechání přistupující objekt set), nebo jen pro zápis indexery (Díky vynechání přistupující objekt get).

Můžete použít prakticky vše, co zjistíte z práce s vlastností indexery. Jedinou výjimkou tohoto pravidla je *automaticky implementované vlastnosti*. Kompilátor nemůže vždy generovat správné úložiště pro indexer.

Přítomnost argumenty, chcete-li položku v sadě položek indexery odlišuje od vlastnosti. Několik indexerů může definovat podle typu, tak dlouho, dokud argument uvádí pro každý indexeru je jedinečný. Podíváme se různé scénáře kde můžete použít jeden nebo více indexery v definici třídy. 

## <a name="scenarios"></a>Scénáře

Můžete nadefinovat *indexery* v vašeho typu při jeho API modelů některé kolekce, ve které definujete argumenty, které do této kolekce. Vaše indexery může nebo nemusí mapovat přímo na typy kolekcí, které jsou součástí rozhraní .NET framework core. Typ vašeho může mít jiné odpovědnosti kromě modelování kolekce.
Indexery umožňují poskytují rozhraní API, která odpovídá typu vašeho abstrakce bez vystavení vnitřní podrobnosti o tom, jak jsou hodnoty pro tuto abstrakci uložené či počítaný.

Projděme některé z následujících běžných scénářů pro použití *indexery*. Dostanete [ukázkové složky pro indexery](https://github.com/dotnet/docs/tree/master/samples/csharp/indexers). Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

### <a name="arrays-and-vectors"></a>Pole a vektory

Jednou z nejběžnějších scénářů pro vytvoření indexery je typ vašeho modelů pole nebo vektor. Můžete vytvořit indexeru seřazený seznam dat modelu. 

Výhoda vytváření vlastní indexeru je, že můžete definovat úložiště pro tuto kolekci, aby vyhovovaly potřebám vaší. Představte si situaci, kde typ vašeho modelů historická data, která je příliš velký pro načtení do paměti najednou. Budete muset zavedení a uvolnění části kolekce na základě využití. Následující příklad modelů toto chování. Předává sestavy na tom, kolik datových bodů neexistuje. Vytváří stránky pro uložení části dat na vyžádání. Stránky se odeberou z paměti, aby uvolnil prostor pro stránky vyžaduje novější požadavky.

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

Můžete postupovat podle tohoto návrhu stylu pro modelování žádné řazení kolekce tam, kde je dobré důvodů, proč nenačte celá sada dat do kolekci v paměti. Všimněte si, že `Page` třída je privátní vnořené třídy, který není součástí veřejné rozhraní. Tyto podrobnosti jsou skryta všechny uživatele této třídy.

### <a name="dictionaries"></a>slovník

Další z typických možností je, když potřebujete modelu slovník nebo mapy. Tento scénář je, když typ vašeho uloží hodnoty na základě klíče, obvykle text klíče. Tento příklad vytvoří slovník, který mapuje argumenty příkazového řádku k [lamdba výrazy](delegates-overview.md) , spravovat tyto možnosti. Následující příklad ukazuje dvě třídy: `ArgsActions` třídu, která mapuje možnost příkazového řádku k `Action` delegovat a `ArgsProcessor` používající `ArgsActions` provést každý `Action` když zjistí tuto možnost.

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

V tomto příkladu `ArgsAction` kolekce mapuje úzce zdrojové kolekce.
`get` Určuje, pokud byla nakonfigurována danou možnost. Pokud ano, vrátí hodnotu `Action` přidružené k této možnosti. Pokud ne, vrátí hodnotu `Action` neprovede žádnou akci. Veřejné přistupujícího objektu nezahrnuje `set` přistupujícího objektu. Místo toho návrhu pomocí veřejnou metodu pro nastavení možností.

### <a name="multi-dimensional-maps"></a>Multidimenzionální mapy

Můžete vytvořit indexery, které používají více argumentů. Kromě toho tyto argumenty nejsou omezené být stejného typu. Podívejme se na dva příklady.   

První příklad ukazuje třídu, která generuje hodnoty pro sadu Mandelbrot. Další informace o Matematika za sadu číst [v tomto článku](https://en.wikipedia.org/wiki/Mandelbrot_set). Indexer používá dvě hodnoty Double pro definování bod v X, Y roviny.
Přistupující objekt get vypočítá počet iterací, dokud bod je určen tak, aby nebyl v sadě. Pokud bude dosažen maximální počet iterací, bod je v sadě a je vrácena hodnota maxIterations třídu. (Image počítače generované popularized pro sadu Mandelbrot definovat barvy pro počet opakování je třeba určit, že bod je mimo danou sadu.

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

Definuje sadu Mandelbrot hodnoty v každé (x, y) koordinaci skutečných číselné hodnoty.
Slovník, který může obsahovat libovolný počet hodnot, který definuje. Proto neexistuje žádné úložiště za sadu. Místo toho tato třída vypočítá hodnotu pro každý bod při volání kódu `get` přistupujícího objektu. Neexistuje žádná základní úložiště použít.

Podívejme se na jedno použití poslední indexery, kde indexeru trvá několik argumentů různých typů. Vezměte v úvahu program, který spravuje teploty historická data. Indexer používá města a datum nastavit nebo získat teploty vysoké a nízké pro toto umístění:

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

Tento příklad vytvoří indexer, který mapuje počasí data na dvou různých argumenty: Město (reprezentována `string`) a datum (reprezentována `DateTime`). Interní úložiště používá dva `Dictionary` třídy představující dvourozměrná slovníku. Veřejné rozhraní API už představuje základní úložiště. Místo toho funkce jazyka indexery umožňuje vytvářet veřejné rozhraní, které představuje abstrakce, i když příslušné úložiště musí používat jiný základní typy kolekcí.

Existují dvě části tohoto kódu, který může být obeznámeni některé vývojářům. Tyto dva `using` příkazy:

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

vytvoření *alias* pro vytvořený obecného typu. Tyto příkazy Povolit kód, abyste mohli používat více popisný `DateMeasurements` a `CityDateMeasurements` názvy místo obecné konstrukce `Dictionary<DateTime, Measurements>` a `Dictionary<string, Dictionary<DateTime, Measurements> >`. Tento konstruktor nevyžaduje, použijte plně kvalifikovaný typ názvy na pravé straně `=` přihlášení.

Druhý způsob spočívá je oddělit vypnout části času každého `DateTime` objekt použitý index do kolekce. Rozhraní .NET framework nezahrnuje pouze typ datum.
Vývojáři použít `DateTime` typu, ale použít `Date` vlastnost zajistit, aby všechny `DateTime` objekt z daný den jsou stejné.

## <a name="summing-up"></a>Shrnutí

Měli byste vytvořit indexery, můžete kdykoli máte prvek jako vlastnost ve třídě, přičemž tuto vlastnost představuje jednu hodnotu, ale spíš kolekci hodnot, kde jednotlivé položky je identifikována sadu argumentů. Tyto argumenty může jedinečně identifikovat, která položka v kolekci by měla odkazovat.
Indexery rozšířit koncept [vlastnosti](properties.md), kde je členem zacházet jako položku dat z mimo třídu, ale jako metody na straně. Indexery povolit argumenty najít jednu položku ve vlastnosti, která představuje sadu položek.
