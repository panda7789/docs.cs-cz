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
# <a name="indexers"></a><span data-ttu-id="d77bf-103">Indexery</span><span class="sxs-lookup"><span data-stu-id="d77bf-103">Indexers</span></span>

<span data-ttu-id="d77bf-104">*Indexery* jsou podobné vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="d77bf-104">*Indexers* are similar to properties.</span></span> <span data-ttu-id="d77bf-105">V mnoha ohledech indexery stavět na stejné jazykové funkce jako [vlastnosti](properties.md).</span><span class="sxs-lookup"><span data-stu-id="d77bf-105">In many ways indexers build on the same language features as [properties](properties.md).</span></span> <span data-ttu-id="d77bf-106">Indexery umožňují *indexované* vlastnosti: vlastnosti odkazované pomocí jednoho nebo více argumentů.</span><span class="sxs-lookup"><span data-stu-id="d77bf-106">Indexers enable *indexed* properties: properties referenced using one or more arguments.</span></span> <span data-ttu-id="d77bf-107">Tyto argumenty poskytují index do některé kolekce hodnot.</span><span class="sxs-lookup"><span data-stu-id="d77bf-107">Those arguments provide an index into some collection of values.</span></span>

## <a name="indexer-syntax"></a><span data-ttu-id="d77bf-108">Syntaxe indexeru</span><span class="sxs-lookup"><span data-stu-id="d77bf-108">Indexer Syntax</span></span>

<span data-ttu-id="d77bf-109">K indexeru přistupujete prostřednictvím názvu proměnné a hranatých závorek.</span><span class="sxs-lookup"><span data-stu-id="d77bf-109">You access an indexer through a variable name and square brackets.</span></span> <span data-ttu-id="d77bf-110">Argumenty indexeru umístíte do závorek:</span><span class="sxs-lookup"><span data-stu-id="d77bf-110">You place the indexer arguments inside the brackets:</span></span>

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

<span data-ttu-id="d77bf-111">Deklarujete `this` indexery pomocí klíčového slova jako název vlastnosti a deklaruje argumenty v rámci hranaté závorky.</span><span class="sxs-lookup"><span data-stu-id="d77bf-111">You declare indexers using the `this` keyword as the property name, and declaring the arguments within square brackets.</span></span> <span data-ttu-id="d77bf-112">Toto prohlášení by odpovídalo použití uvedenému v předchozím odstavci:</span><span class="sxs-lookup"><span data-stu-id="d77bf-112">This declaration would match the usage shown in the previous paragraph:</span></span>

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

<span data-ttu-id="d77bf-113">Z tohoto počátečního příkladu můžete zobrazit vztah mezi syntaxí pro vlastnosti a indexery.</span><span class="sxs-lookup"><span data-stu-id="d77bf-113">From this initial example, you can see the relationship between the syntax for properties and for indexers.</span></span> <span data-ttu-id="d77bf-114">Tato analogie nese přes většinu syntaxe pravidla pro indexery.</span><span class="sxs-lookup"><span data-stu-id="d77bf-114">This analogy carries through most of the syntax rules for indexers.</span></span> <span data-ttu-id="d77bf-115">Indexery mohou mít všechny platné modifikátory přístupu (veřejné, chráněné interní, chráněné, interní, soukromé nebo soukromé chráněné.</span><span class="sxs-lookup"><span data-stu-id="d77bf-115">Indexers can have any valid access modifiers (public, protected internal, protected, internal, private or private protected).</span></span> <span data-ttu-id="d77bf-116">Mohou být zapečetěné, virtuální nebo abstraktní.</span><span class="sxs-lookup"><span data-stu-id="d77bf-116">They may be sealed, virtual, or abstract.</span></span> <span data-ttu-id="d77bf-117">Stejně jako u vlastností můžete určit různé modifikátory přístupu pro přístupové objekty get a set v indexeru.</span><span class="sxs-lookup"><span data-stu-id="d77bf-117">As with properties, you can specify different access modifiers for the get and set accessors in an indexer.</span></span>
<span data-ttu-id="d77bf-118">Můžete také zadat indexery jen pro čtení (vynecháním přístupového zařízení set) nebo indexery pouze pro zápis (vynecháním přístupového orátele get).</span><span class="sxs-lookup"><span data-stu-id="d77bf-118">You may also specify read-only indexers (by omitting the set accessor), or write-only indexers (by omitting the get accessor).</span></span>

<span data-ttu-id="d77bf-119">Můžete použít téměř vše, co se naučíte z práce s vlastnostmi na indexery.</span><span class="sxs-lookup"><span data-stu-id="d77bf-119">You can apply almost everything you learn from working with properties to indexers.</span></span> <span data-ttu-id="d77bf-120">Jedinou výjimkou z tohoto pravidla jsou *automaticky implementované vlastnosti*.</span><span class="sxs-lookup"><span data-stu-id="d77bf-120">The only exception to that rule is *auto implemented properties*.</span></span> <span data-ttu-id="d77bf-121">Kompilátor nemůže vždy generovat správné úložiště pro indexer.</span><span class="sxs-lookup"><span data-stu-id="d77bf-121">The compiler cannot always generate the correct storage for an indexer.</span></span>

<span data-ttu-id="d77bf-122">Přítomnost argumentů odkazna položku v sadě položek odlišuje indexery od vlastností.</span><span class="sxs-lookup"><span data-stu-id="d77bf-122">The presence of arguments to reference an item in a set of items distinguishes indexers from properties.</span></span> <span data-ttu-id="d77bf-123">Můžete definovat více indexerů na typu, tak dlouho, dokud seznamy argumentů pro každý indexer je jedinečný.</span><span class="sxs-lookup"><span data-stu-id="d77bf-123">You may define multiple indexers on a type, as long as the argument lists for each indexer is unique.</span></span> <span data-ttu-id="d77bf-124">Pojďme prozkoumat různé scénáře, kde můžete použít jeden nebo více indexerů v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="d77bf-124">Let's explore different scenarios where you might use one or more indexers in a class definition.</span></span>

## <a name="scenarios"></a><span data-ttu-id="d77bf-125">Scénáře</span><span class="sxs-lookup"><span data-stu-id="d77bf-125">Scenarios</span></span>

<span data-ttu-id="d77bf-126">Byste definovat *indexery* v typu, když jeho rozhraní API modely některé kolekce, kde definujete argumenty pro tuto kolekci.</span><span class="sxs-lookup"><span data-stu-id="d77bf-126">You would define *indexers* in your type when its API models some collection where you define the arguments to that collection.</span></span> <span data-ttu-id="d77bf-127">Indexery může nebo nemusí mapovat přímo na typy kolekce, které jsou součástí rozhraní .NET core framework.</span><span class="sxs-lookup"><span data-stu-id="d77bf-127">Your indexers may or may not map directly to the collection types that are part of the .NET core framework.</span></span> <span data-ttu-id="d77bf-128">Váš typ může mít další odpovědnosti kromě modelování kolekce.</span><span class="sxs-lookup"><span data-stu-id="d77bf-128">Your type may have other responsibilities in addition to modeling a collection.</span></span>
<span data-ttu-id="d77bf-129">Indexery umožňují poskytnout rozhraní API, které odpovídá abstrakce vašeho typu bez vystavení vnitřní podrobnosti o tom, jak jsou uloženy nebo vypočítány hodnoty pro abstrakce.</span><span class="sxs-lookup"><span data-stu-id="d77bf-129">Indexers enable you to provide the API that matches your type's abstraction without exposing the inner details of how the values for that abstraction are stored or computed.</span></span>

<span data-ttu-id="d77bf-130">Pojďme projít některé běžné scénáře pro použití *indexery*.</span><span class="sxs-lookup"><span data-stu-id="d77bf-130">Let's walk through some of the common scenarios for using *indexers*.</span></span> <span data-ttu-id="d77bf-131">Můžete získat přístup ke [vzorové složce indexerů](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span><span class="sxs-lookup"><span data-stu-id="d77bf-131">You can access the [sample folder for indexers](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span></span> <span data-ttu-id="d77bf-132">Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="d77bf-132">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="arrays-and-vectors"></a><span data-ttu-id="d77bf-133">Pole a vektory</span><span class="sxs-lookup"><span data-stu-id="d77bf-133">Arrays and Vectors</span></span>

<span data-ttu-id="d77bf-134">Jedním z nejběžnějších scénářů pro vytváření indexerů je, když váš typ modely pole nebo vektor.</span><span class="sxs-lookup"><span data-stu-id="d77bf-134">One of the most common scenarios for creating indexers is when your type models an array, or a vector.</span></span> <span data-ttu-id="d77bf-135">Můžete vytvořit indexer pro modelování seřazeného seznamu dat.</span><span class="sxs-lookup"><span data-stu-id="d77bf-135">You can create an indexer to model an ordered list of data.</span></span>

<span data-ttu-id="d77bf-136">Výhodou vytvoření vlastního indexeru je, že můžete definovat úložiště pro tuto kolekci tak, aby vyhovovalo vašim potřebám.</span><span class="sxs-lookup"><span data-stu-id="d77bf-136">The advantage of creating your own indexer is that you can define the storage for that collection to suit your needs.</span></span> <span data-ttu-id="d77bf-137">Představte si scénář, kde váš typ modely historických dat, která je příliš velká pro načtení do paměti najednou.</span><span class="sxs-lookup"><span data-stu-id="d77bf-137">Imagine a scenario where your type models historical data that is too large to load into memory at once.</span></span> <span data-ttu-id="d77bf-138">Je třeba načíst a uvolnit části kolekce na základě využití.</span><span class="sxs-lookup"><span data-stu-id="d77bf-138">You need to load and unload sections of the collection based on usage.</span></span> <span data-ttu-id="d77bf-139">Příklad následující modely toto chování.</span><span class="sxs-lookup"><span data-stu-id="d77bf-139">The example following models this behavior.</span></span> <span data-ttu-id="d77bf-140">Informuje o tom, kolik datových bodů existuje.</span><span class="sxs-lookup"><span data-stu-id="d77bf-140">It reports on how many data points exist.</span></span> <span data-ttu-id="d77bf-141">Vytvoří stránky pro uložení částí dat na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="d77bf-141">It creates pages to hold sections of the data on demand.</span></span> <span data-ttu-id="d77bf-142">Odstraňuje stránky z paměti, aby se uvolnilo místo pro stránky potřebné novějšími požadavky.</span><span class="sxs-lookup"><span data-stu-id="d77bf-142">It removes pages from memory to make room for pages needed by more recent requests.</span></span>

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

<span data-ttu-id="d77bf-143">Můžete sledovat tento návrh idiom modelovat jakýkoli druh kolekce, kde existují dobré důvody, proč nenačíst celou sadu dat do kolekce v paměti.</span><span class="sxs-lookup"><span data-stu-id="d77bf-143">You can follow this design idiom to model any sort of collection where there are good reasons not to load the entire set of data into an in- memory collection.</span></span> <span data-ttu-id="d77bf-144">Všimněte `Page` si, že třída je soukromá vnořená třída, která není součástí veřejného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d77bf-144">Notice that the `Page` class is a private nested class that is not part of the public interface.</span></span> <span data-ttu-id="d77bf-145">Tyto podrobnosti jsou skryty před všemi uživateli této třídy.</span><span class="sxs-lookup"><span data-stu-id="d77bf-145">Those details are hidden from any users of this class.</span></span>

### <a name="dictionaries"></a><span data-ttu-id="d77bf-146">Slovníky</span><span class="sxs-lookup"><span data-stu-id="d77bf-146">Dictionaries</span></span>

<span data-ttu-id="d77bf-147">Dalším běžným scénářem je, když potřebujete modelovat slovník nebo mapu.</span><span class="sxs-lookup"><span data-stu-id="d77bf-147">Another common scenario is when you need to model a dictionary or a map.</span></span> <span data-ttu-id="d77bf-148">Tento scénář je, když váš typ ukládá hodnoty na základě klíče, obvykle textové klíče.</span><span class="sxs-lookup"><span data-stu-id="d77bf-148">This scenario is when your type stores values based on key, typically text keys.</span></span> <span data-ttu-id="d77bf-149">Tento příklad vytvoří slovník, který mapuje argumenty příkazového řádku na [výrazy lambda,](delegates-overview.md) které tyto možnosti spravují.</span><span class="sxs-lookup"><span data-stu-id="d77bf-149">This example creates a dictionary that maps command line arguments to [lambda expressions](delegates-overview.md) that manage those options.</span></span> <span data-ttu-id="d77bf-150">Následující příklad ukazuje dvě `ArgsActions` třídy: třída, která `Action` mapuje možnost `ArgsProcessor` příkazového `ArgsActions` řádku `Action` delegátovi a která používá ke spuštění každé z nich, když narazí na tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="d77bf-150">The following example shows two classes: an `ArgsActions` class that maps a command line option to an `Action` delegate, and an `ArgsProcessor` that uses the `ArgsActions` to execute each `Action` when it encounters that option.</span></span>

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

<span data-ttu-id="d77bf-151">V tomto příkladu `ArgsAction` kolekce mapuje úzce základní kolekce.</span><span class="sxs-lookup"><span data-stu-id="d77bf-151">In this example, the `ArgsAction` collection maps closely to the underlying collection.</span></span>
<span data-ttu-id="d77bf-152">Určuje, `get` zda byla nakonfigurována daná možnost.</span><span class="sxs-lookup"><span data-stu-id="d77bf-152">The `get` determines if a given option has been configured.</span></span> <span data-ttu-id="d77bf-153">Pokud ano, vrátí `Action` přidružené s tou možností.</span><span class="sxs-lookup"><span data-stu-id="d77bf-153">If so, it returns the `Action` associated with that option.</span></span> <span data-ttu-id="d77bf-154">Pokud ne, vrátí, `Action` který neprovede nic.</span><span class="sxs-lookup"><span data-stu-id="d77bf-154">If not, it returns an `Action` that does nothing.</span></span> <span data-ttu-id="d77bf-155">Veřejný přistupující odkaz `set` neobsahuje přistupující ho.</span><span class="sxs-lookup"><span data-stu-id="d77bf-155">The public accessor does not include a `set` accessor.</span></span> <span data-ttu-id="d77bf-156">Spíše návrh pomocí veřejné metody pro nastavení možností.</span><span class="sxs-lookup"><span data-stu-id="d77bf-156">Rather, the design using a public method for setting options.</span></span>

### <a name="multi-dimensional-maps"></a><span data-ttu-id="d77bf-157">Vícerozměrné mapy</span><span class="sxs-lookup"><span data-stu-id="d77bf-157">Multi-Dimensional Maps</span></span>

<span data-ttu-id="d77bf-158">Můžete vytvořit indexery, které používají více argumentů.</span><span class="sxs-lookup"><span data-stu-id="d77bf-158">You can create indexers that use multiple arguments.</span></span> <span data-ttu-id="d77bf-159">Kromě toho tyto argumenty nejsou omezeny být stejného typu.</span><span class="sxs-lookup"><span data-stu-id="d77bf-159">In addition, those arguments are not constrained to be the same type.</span></span> <span data-ttu-id="d77bf-160">Podívejme se na dva příklady.</span><span class="sxs-lookup"><span data-stu-id="d77bf-160">Let's look at two examples.</span></span>

<span data-ttu-id="d77bf-161">První příklad ukazuje třídu, která generuje hodnoty pro sadu Mandelbrot.</span><span class="sxs-lookup"><span data-stu-id="d77bf-161">The first example shows a class that generates values for a Mandelbrot set.</span></span> <span data-ttu-id="d77bf-162">Další informace o matematice za sadou naleznete v [tomto článku](https://en.wikipedia.org/wiki/Mandelbrot_set).</span><span class="sxs-lookup"><span data-stu-id="d77bf-162">For more information on the mathematics behind the set, read [this article](https://en.wikipedia.org/wiki/Mandelbrot_set).</span></span>
<span data-ttu-id="d77bf-163">Indexer používá dvě dvojníky k definování bodu v rovině X, Y.</span><span class="sxs-lookup"><span data-stu-id="d77bf-163">The indexer uses two doubles to define a point in the X, Y plane.</span></span>
<span data-ttu-id="d77bf-164">Get přistupující ho vypočítá počet iterací, dokud bod je určen není v sadě.</span><span class="sxs-lookup"><span data-stu-id="d77bf-164">The get accessor computes the number of iterations until a point is determined to be not in the set.</span></span> <span data-ttu-id="d77bf-165">Pokud je dosaženo maximální iterace, bod je v sadě a je vrácena hodnota maxIterations třídy.</span><span class="sxs-lookup"><span data-stu-id="d77bf-165">If the maximum iterations is reached, the point is in the set, and the class's maxIterations value is returned.</span></span> <span data-ttu-id="d77bf-166">(Počítačem generované obrázky popularizované pro sadu Mandelbrot definují barvy pro počet iterací potřebných k určení, že bod je mimo sadu.</span><span class="sxs-lookup"><span data-stu-id="d77bf-166">(The computer generated images popularized for the Mandelbrot set define colors for the number of iterations necessary to determine that a point is outside the set.</span></span>

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

<span data-ttu-id="d77bf-167">Sada Mandelbrot definuje hodnoty na každé souřadnici (x,y) pro hodnoty reálných čísel.</span><span class="sxs-lookup"><span data-stu-id="d77bf-167">The Mandelbrot Set defines values at every (x,y) coordinate for real number values.</span></span>
<span data-ttu-id="d77bf-168">To definuje slovník, který by mohl obsahovat nekonečný počet hodnot.</span><span class="sxs-lookup"><span data-stu-id="d77bf-168">That defines a dictionary that could contain an infinite number of values.</span></span> <span data-ttu-id="d77bf-169">Proto neexistuje žádné úložiště za sadu.</span><span class="sxs-lookup"><span data-stu-id="d77bf-169">Therefore, there is no storage behind the set.</span></span> <span data-ttu-id="d77bf-170">Místo toho tato třída vypočítá hodnotu pro `get` každý bod při volání kódu přistupujícího pole.</span><span class="sxs-lookup"><span data-stu-id="d77bf-170">Instead, this class computes the value for each point when code calls the `get` accessor.</span></span> <span data-ttu-id="d77bf-171">Není použito žádné podkladové úložiště.</span><span class="sxs-lookup"><span data-stu-id="d77bf-171">There's no underlying storage used.</span></span>

<span data-ttu-id="d77bf-172">Podívejme se na poslední použití indexery, kde indexer trvá více argumentů různých typů.</span><span class="sxs-lookup"><span data-stu-id="d77bf-172">Let's examine one last use of indexers, where the indexer takes multiple arguments of different types.</span></span> <span data-ttu-id="d77bf-173">Vezměme si program, který spravuje historická data teploty.</span><span class="sxs-lookup"><span data-stu-id="d77bf-173">Consider a program that manages historical temperature data.</span></span> <span data-ttu-id="d77bf-174">Tento indexer používá město a datum pro nastavení nebo získání vysokých a nízkých teplot pro toto umístění:</span><span class="sxs-lookup"><span data-stu-id="d77bf-174">This indexer uses a city and a date to set or get the high and low temperatures for that location:</span></span>

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

<span data-ttu-id="d77bf-175">Tento příklad vytvoří indexer, který mapuje data o počasí na `string`dva různé argumenty: `DateTime`město (reprezentované ) a datum (reprezentované ).</span><span class="sxs-lookup"><span data-stu-id="d77bf-175">This example creates an indexer that maps weather data on two different arguments: a city (represented by a `string`) and a date (represented by a `DateTime`).</span></span> <span data-ttu-id="d77bf-176">Vnitřní úložiště používá `Dictionary` dvě třídy představují dvojrozměrný slovník.</span><span class="sxs-lookup"><span data-stu-id="d77bf-176">The internal storage uses two `Dictionary` classes to represent the two-dimensional dictionary.</span></span> <span data-ttu-id="d77bf-177">Veřejné rozhraní API již představuje základní úložiště.</span><span class="sxs-lookup"><span data-stu-id="d77bf-177">The public API no longer represents the underlying storage.</span></span> <span data-ttu-id="d77bf-178">Spíše jazykové funkce indexerů umožňuje vytvořit veřejné rozhraní, které představuje abstrakce, i když základní úložiště musí používat různé typy základní kolekce.</span><span class="sxs-lookup"><span data-stu-id="d77bf-178">Rather, the language features of indexers enables you to create a public interface that represents your abstraction, even though the underlying storage must use different core collection types.</span></span>

<span data-ttu-id="d77bf-179">Existují dvě části tohoto kódu, které mohou být neznámé pro některé vývojáře.</span><span class="sxs-lookup"><span data-stu-id="d77bf-179">There are two parts of this code that may be unfamiliar to some developers.</span></span> <span data-ttu-id="d77bf-180">Tato `using` dvě prohlášení:</span><span class="sxs-lookup"><span data-stu-id="d77bf-180">These two `using` statements:</span></span>

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

<span data-ttu-id="d77bf-181">vytvořte *alias* pro vytvořený obecný typ.</span><span class="sxs-lookup"><span data-stu-id="d77bf-181">create an *alias* for a constructed generic type.</span></span> <span data-ttu-id="d77bf-182">Tyto příkazy umožňují kód později použít `DateMeasurements` více `CityDateMeasurements` popisné a názvy namísto obecné konstrukce `Dictionary<DateTime, Measurements>` a `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span><span class="sxs-lookup"><span data-stu-id="d77bf-182">Those statements enable the code later to use the more descriptive `DateMeasurements` and `CityDateMeasurements` names instead of the generic construction of `Dictionary<DateTime, Measurements>` and `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span></span>
<span data-ttu-id="d77bf-183">Tato konstrukce vyžaduje použití plně kvalifikovaných názvů typů `=` na pravé straně znaménko.</span><span class="sxs-lookup"><span data-stu-id="d77bf-183">This construct does require using the fully qualified type names on the right side of the `=` sign.</span></span>

<span data-ttu-id="d77bf-184">Druhá technika je odstranit časové části libovolný `DateTime` objekt, který slouží k indexování do kolekcí.</span><span class="sxs-lookup"><span data-stu-id="d77bf-184">The second technique is to strip off the time portions of any `DateTime` object used to index into the collections.</span></span> <span data-ttu-id="d77bf-185">Rozhraní .NET neobsahuje typ pouze pro datum.</span><span class="sxs-lookup"><span data-stu-id="d77bf-185">.NET doesn't include a date-only type.</span></span>
<span data-ttu-id="d77bf-186">Vývojáři `DateTime` používají typ, `Date` ale použít vlastnost `DateTime` k zajištění, že všechny objekty z tohoto dne jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="d77bf-186">Developers use the `DateTime` type, but use the `Date` property to ensure that any `DateTime` object from that day are equal.</span></span>

## <a name="summing-up"></a><span data-ttu-id="d77bf-187">Sečtením</span><span class="sxs-lookup"><span data-stu-id="d77bf-187">Summing Up</span></span>

<span data-ttu-id="d77bf-188">Indexery byste měli vytvořit kdykoli máte prvek podobný vlastnosti ve vaší třídě, kde tato vlastnost nepředstavuje jednu hodnotu, ale spíše kolekci hodnot, kde je každá jednotlivá položka identifikována sadou argumentů.</span><span class="sxs-lookup"><span data-stu-id="d77bf-188">You should create indexers anytime you have a property-like element in your class where that property represents not a single value, but rather a collection of values where each individual item is identified by a set of arguments.</span></span> <span data-ttu-id="d77bf-189">Tyto argumenty lze jednoznačně určit, která položka v kolekci by měla být odkazována.</span><span class="sxs-lookup"><span data-stu-id="d77bf-189">Those arguments can uniquely identify which item in the collection should be referenced.</span></span>
<span data-ttu-id="d77bf-190">Indexery rozšířit koncept [vlastností](properties.md), kde člen je zpracována jako datové položky mimo třídu, ale jako metoda na vnitřní straně.</span><span class="sxs-lookup"><span data-stu-id="d77bf-190">Indexers extend the concept of [properties](properties.md), where a member is treated like a data item from outside the class, but like a method on the inside.</span></span> <span data-ttu-id="d77bf-191">Indexery umožňují argumentům najít jednu položku ve vlastnosti, která představuje sadu položek.</span><span class="sxs-lookup"><span data-stu-id="d77bf-191">Indexers allow arguments to find a single item in a property that represents a set of items.</span></span>
