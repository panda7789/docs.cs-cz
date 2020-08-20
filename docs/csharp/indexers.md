---
title: Indexery
description: Přečtěte si o indexerech v jazyce C# a způsobu implementace indexovaných vlastností, což jsou vlastnosti, na které odkazuje jeden nebo více argumentů.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: 1369740404c500d8b44b4706959bf4640c26aa2d
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656108"
---
# <a name="indexers"></a><span data-ttu-id="6c486-103">Indexery</span><span class="sxs-lookup"><span data-stu-id="6c486-103">Indexers</span></span>

<span data-ttu-id="6c486-104">*Indexery* jsou podobné vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="6c486-104">*Indexers* are similar to properties.</span></span> <span data-ttu-id="6c486-105">V mnoha způsobech indexerů vytváří stejné jazykové funkce jako [vlastnosti](properties.md).</span><span class="sxs-lookup"><span data-stu-id="6c486-105">In many ways indexers build on the same language features as [properties](properties.md).</span></span> <span data-ttu-id="6c486-106">Indexery povolují *indexované* vlastnosti: vlastnosti odkazované pomocí jednoho nebo více argumentů.</span><span class="sxs-lookup"><span data-stu-id="6c486-106">Indexers enable *indexed* properties: properties referenced using one or more arguments.</span></span> <span data-ttu-id="6c486-107">Tyto argumenty poskytují index pro určitou kolekci hodnot.</span><span class="sxs-lookup"><span data-stu-id="6c486-107">Those arguments provide an index into some collection of values.</span></span>

## <a name="indexer-syntax"></a><span data-ttu-id="6c486-108">Syntaxe indexeru</span><span class="sxs-lookup"><span data-stu-id="6c486-108">Indexer Syntax</span></span>

<span data-ttu-id="6c486-109">K indexeru přistupujete pomocí názvu proměnné a hranatých závorek.</span><span class="sxs-lookup"><span data-stu-id="6c486-109">You access an indexer through a variable name and square brackets.</span></span> <span data-ttu-id="6c486-110">Argumenty indexeru umístíte do závorek:</span><span class="sxs-lookup"><span data-stu-id="6c486-110">You place the indexer arguments inside the brackets:</span></span>

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

<span data-ttu-id="6c486-111">Indexery deklarujete pomocí `this` klíčového slova jako názvu vlastnosti a deklarujete argumenty v hranatých závorkách.</span><span class="sxs-lookup"><span data-stu-id="6c486-111">You declare indexers using the `this` keyword as the property name, and declaring the arguments within square brackets.</span></span> <span data-ttu-id="6c486-112">Tato deklarace by odpovídala využití uvedenému v předchozím odstavci:</span><span class="sxs-lookup"><span data-stu-id="6c486-112">This declaration would match the usage shown in the previous paragraph:</span></span>

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

<span data-ttu-id="6c486-113">Z tohoto počátečního příkladu můžete vidět vztah mezi syntaxí pro vlastnosti a indexery.</span><span class="sxs-lookup"><span data-stu-id="6c486-113">From this initial example, you can see the relationship between the syntax for properties and for indexers.</span></span> <span data-ttu-id="6c486-114">Tato analogická průchody procházejí většinou pravidel syntaxe pro indexery.</span><span class="sxs-lookup"><span data-stu-id="6c486-114">This analogy carries through most of the syntax rules for indexers.</span></span> <span data-ttu-id="6c486-115">Indexery můžou mít libovolný platný modifikátor přístupu (Public, Protected Internal, Protected, Internal, private nebo Private Protected).</span><span class="sxs-lookup"><span data-stu-id="6c486-115">Indexers can have any valid access modifiers (public, protected internal, protected, internal, private or private protected).</span></span> <span data-ttu-id="6c486-116">Můžou být zapečetěné, virtuální nebo abstraktní.</span><span class="sxs-lookup"><span data-stu-id="6c486-116">They may be sealed, virtual, or abstract.</span></span> <span data-ttu-id="6c486-117">Stejně jako u vlastností můžete určit různé modifikátory přístupu pro přístupové objekty get a Set v indexeru.</span><span class="sxs-lookup"><span data-stu-id="6c486-117">As with properties, you can specify different access modifiers for the get and set accessors in an indexer.</span></span>
<span data-ttu-id="6c486-118">Můžete také zadat indexery jen pro čtení (vynecháním přístupového objektu set) nebo indexerů jen pro zápis (vynecháním přístupového objektu Get).</span><span class="sxs-lookup"><span data-stu-id="6c486-118">You may also specify read-only indexers (by omitting the set accessor), or write-only indexers (by omitting the get accessor).</span></span>

<span data-ttu-id="6c486-119">Můžete použít téměř všechno, co se naučíte pracovat s vlastnostmi pro indexery.</span><span class="sxs-lookup"><span data-stu-id="6c486-119">You can apply almost everything you learn from working with properties to indexers.</span></span> <span data-ttu-id="6c486-120">Jedinou výjimkou z tohoto pravidla jsou *automaticky implementované vlastnosti*.</span><span class="sxs-lookup"><span data-stu-id="6c486-120">The only exception to that rule is *auto implemented properties*.</span></span> <span data-ttu-id="6c486-121">Kompilátor nemůže vždy vygenerovat správné úložiště pro indexer.</span><span class="sxs-lookup"><span data-stu-id="6c486-121">The compiler cannot always generate the correct storage for an indexer.</span></span>

<span data-ttu-id="6c486-122">Přítomnost argumentů odkazujících na položku v sadě položek rozlišuje indexery od vlastností.</span><span class="sxs-lookup"><span data-stu-id="6c486-122">The presence of arguments to reference an item in a set of items distinguishes indexers from properties.</span></span> <span data-ttu-id="6c486-123">Můžete definovat více indexerů pro typ, pokud je seznam argumentů pro každý indexer jedinečný.</span><span class="sxs-lookup"><span data-stu-id="6c486-123">You may define multiple indexers on a type, as long as the argument lists for each indexer is unique.</span></span> <span data-ttu-id="6c486-124">Pojďme prozkoumat různé scénáře, kde můžete použít jeden nebo více indexerů v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="6c486-124">Let's explore different scenarios where you might use one or more indexers in a class definition.</span></span>

## <a name="scenarios"></a><span data-ttu-id="6c486-125">Scénáře</span><span class="sxs-lookup"><span data-stu-id="6c486-125">Scenarios</span></span>

<span data-ttu-id="6c486-126">*Indexery* byste definovali v typu, když jeho model rozhraní API nějaké kolekce, kde definujete argumenty této kolekce.</span><span class="sxs-lookup"><span data-stu-id="6c486-126">You would define *indexers* in your type when its API models some collection where you define the arguments to that collection.</span></span> <span data-ttu-id="6c486-127">Indexery mohou nebo nemusí být mapovány přímo na typy kolekce, které jsou součástí rozhraní .NET Core Framework.</span><span class="sxs-lookup"><span data-stu-id="6c486-127">Your indexers may or may not map directly to the collection types that are part of the .NET core framework.</span></span> <span data-ttu-id="6c486-128">Váš typ může kromě modelování kolekce obsahovat i další zodpovědnosti.</span><span class="sxs-lookup"><span data-stu-id="6c486-128">Your type may have other responsibilities in addition to modeling a collection.</span></span>
<span data-ttu-id="6c486-129">Indexery umožňují poskytovat rozhraní API, které odpovídá abstrakci typu, bez vystavení vnitřních podrobností o tom, jak se hodnoty pro tuto abstrakci ukládají nebo vypočítávají.</span><span class="sxs-lookup"><span data-stu-id="6c486-129">Indexers enable you to provide the API that matches your type's abstraction without exposing the inner details of how the values for that abstraction are stored or computed.</span></span>

<span data-ttu-id="6c486-130">Pojďme si projít některé z běžných scénářů použití *indexerů*.</span><span class="sxs-lookup"><span data-stu-id="6c486-130">Let's walk through some of the common scenarios for using *indexers*.</span></span> <span data-ttu-id="6c486-131">K [ukázkové složce pro indexery](https://github.com/dotnet/samples/tree/master/csharp/indexers)můžete získat přístup.</span><span class="sxs-lookup"><span data-stu-id="6c486-131">You can access the [sample folder for indexers](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span></span> <span data-ttu-id="6c486-132">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="6c486-132">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

### <a name="arrays-and-vectors"></a><span data-ttu-id="6c486-133">Pole a vektory</span><span class="sxs-lookup"><span data-stu-id="6c486-133">Arrays and Vectors</span></span>

<span data-ttu-id="6c486-134">Jedním z nejběžnějších scénářů pro vytváření indexerů je, že typ modeluje pole nebo vektor.</span><span class="sxs-lookup"><span data-stu-id="6c486-134">One of the most common scenarios for creating indexers is when your type models an array, or a vector.</span></span> <span data-ttu-id="6c486-135">Můžete vytvořit indexer pro modelování seřazeného seznamu dat.</span><span class="sxs-lookup"><span data-stu-id="6c486-135">You can create an indexer to model an ordered list of data.</span></span>

<span data-ttu-id="6c486-136">Výhodou vytvoření vlastního indexeru je, že můžete definovat úložiště pro tuto kolekci tak, aby vyhovovalo vašim potřebám.</span><span class="sxs-lookup"><span data-stu-id="6c486-136">The advantage of creating your own indexer is that you can define the storage for that collection to suit your needs.</span></span> <span data-ttu-id="6c486-137">Představte si situaci, kdy váš typ modeluje historická data, která jsou příliš velká pro načtení do paměti najednou.</span><span class="sxs-lookup"><span data-stu-id="6c486-137">Imagine a scenario where your type models historical data that is too large to load into memory at once.</span></span> <span data-ttu-id="6c486-138">Musíte načíst a uvolnit části kolekce na základě využití.</span><span class="sxs-lookup"><span data-stu-id="6c486-138">You need to load and unload sections of the collection based on usage.</span></span> <span data-ttu-id="6c486-139">V následujícím příkladu jsou modely tohoto chování.</span><span class="sxs-lookup"><span data-stu-id="6c486-139">The example following models this behavior.</span></span> <span data-ttu-id="6c486-140">Oznamuje, kolik datových bodů existuje.</span><span class="sxs-lookup"><span data-stu-id="6c486-140">It reports on how many data points exist.</span></span> <span data-ttu-id="6c486-141">Vytvoří stránky pro uložení částí dat na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="6c486-141">It creates pages to hold sections of the data on demand.</span></span> <span data-ttu-id="6c486-142">Odstraní stránky z paměti a uvolní tak místo pro stránky vyžadované novějšími požadavky.</span><span class="sxs-lookup"><span data-stu-id="6c486-142">It removes pages from memory to make room for pages needed by more recent requests.</span></span>

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

<span data-ttu-id="6c486-143">Můžete postupovat podle tohoto návrhu idiom a modelovat jakýkoli druh kolekce, kde jsou dobré důvody, proč nenačíst celou sadu dat do kolekce v paměti.</span><span class="sxs-lookup"><span data-stu-id="6c486-143">You can follow this design idiom to model any sort of collection where there are good reasons not to load the entire set of data into an in- memory collection.</span></span> <span data-ttu-id="6c486-144">Všimněte si, že `Page` Třída je soukromá vnořená třída, která není součástí veřejného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6c486-144">Notice that the `Page` class is a private nested class that is not part of the public interface.</span></span> <span data-ttu-id="6c486-145">Tyto podrobnosti jsou skryté od všech uživatelů této třídy.</span><span class="sxs-lookup"><span data-stu-id="6c486-145">Those details are hidden from any users of this class.</span></span>

### <a name="dictionaries"></a><span data-ttu-id="6c486-146">Slovníky</span><span class="sxs-lookup"><span data-stu-id="6c486-146">Dictionaries</span></span>

<span data-ttu-id="6c486-147">Dalším běžným scénářem je situace, kdy potřebujete modelovat slovník nebo mapu.</span><span class="sxs-lookup"><span data-stu-id="6c486-147">Another common scenario is when you need to model a dictionary or a map.</span></span> <span data-ttu-id="6c486-148">Tento scénář je v případě, že váš typ ukládá hodnoty na základě klíče, obvykle textových klíčů.</span><span class="sxs-lookup"><span data-stu-id="6c486-148">This scenario is when your type stores values based on key, typically text keys.</span></span> <span data-ttu-id="6c486-149">Tento příklad vytvoří slovník, který mapuje argumenty příkazového řádku na [výrazy lambda](delegates-overview.md) , které spravují tyto možnosti.</span><span class="sxs-lookup"><span data-stu-id="6c486-149">This example creates a dictionary that maps command line arguments to [lambda expressions](delegates-overview.md) that manage those options.</span></span> <span data-ttu-id="6c486-150">Následující příklad ukazuje dvě třídy: `ArgsActions` třídu, která mapuje parametr příkazového řádku na `Action` delegáta a `ArgsProcessor` který používá `ArgsActions` ke spuštění každé `Action` , když dojde k této možnosti.</span><span class="sxs-lookup"><span data-stu-id="6c486-150">The following example shows two classes: an `ArgsActions` class that maps a command line option to an `Action` delegate, and an `ArgsProcessor` that uses the `ArgsActions` to execute each `Action` when it encounters that option.</span></span>

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

<span data-ttu-id="6c486-151">V tomto příkladu je `ArgsAction` kolekce úzce mapována na podkladovou kolekci.</span><span class="sxs-lookup"><span data-stu-id="6c486-151">In this example, the `ArgsAction` collection maps closely to the underlying collection.</span></span>
<span data-ttu-id="6c486-152">`get`Určuje, zda byla daná možnost nakonfigurována.</span><span class="sxs-lookup"><span data-stu-id="6c486-152">The `get` determines if a given option has been configured.</span></span> <span data-ttu-id="6c486-153">V takovém případě vrátí `Action` přidruženou k této možnosti.</span><span class="sxs-lookup"><span data-stu-id="6c486-153">If so, it returns the `Action` associated with that option.</span></span> <span data-ttu-id="6c486-154">V takovém případě vrátí hodnotu `Action` , která neprovede žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="6c486-154">If not, it returns an `Action` that does nothing.</span></span> <span data-ttu-id="6c486-155">Veřejný přistupující objekt nezahrnuje `set` přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="6c486-155">The public accessor does not include a `set` accessor.</span></span> <span data-ttu-id="6c486-156">Místo toho návrh pomocí veřejné metody pro nastavení možností.</span><span class="sxs-lookup"><span data-stu-id="6c486-156">Rather, the design using a public method for setting options.</span></span>

### <a name="multi-dimensional-maps"></a><span data-ttu-id="6c486-157">Multidimenzionální mapy</span><span class="sxs-lookup"><span data-stu-id="6c486-157">Multi-Dimensional Maps</span></span>

<span data-ttu-id="6c486-158">Můžete vytvořit indexery, které používají více argumentů.</span><span class="sxs-lookup"><span data-stu-id="6c486-158">You can create indexers that use multiple arguments.</span></span> <span data-ttu-id="6c486-159">Kromě toho nejsou tyto argumenty omezeny na stejný typ.</span><span class="sxs-lookup"><span data-stu-id="6c486-159">In addition, those arguments are not constrained to be the same type.</span></span> <span data-ttu-id="6c486-160">Pojďme se podívat na dva příklady.</span><span class="sxs-lookup"><span data-stu-id="6c486-160">Let's look at two examples.</span></span>

<span data-ttu-id="6c486-161">První příklad ukazuje třídu, která generuje hodnoty pro Mandelbrot sadu.</span><span class="sxs-lookup"><span data-stu-id="6c486-161">The first example shows a class that generates values for a Mandelbrot set.</span></span> <span data-ttu-id="6c486-162">Další informace o matematikě za sadou najdete v [tomto článku](https://en.wikipedia.org/wiki/Mandelbrot_set).</span><span class="sxs-lookup"><span data-stu-id="6c486-162">For more information on the mathematics behind the set, read [this article](https://en.wikipedia.org/wiki/Mandelbrot_set).</span></span>
<span data-ttu-id="6c486-163">Indexer používá dvě dvojité čárky k definování bodu v rovině X, Y.</span><span class="sxs-lookup"><span data-stu-id="6c486-163">The indexer uses two doubles to define a point in the X, Y plane.</span></span>
<span data-ttu-id="6c486-164">Přistupující objekt get vypočítá počet iterací, dokud není v sadě zjištěn bod.</span><span class="sxs-lookup"><span data-stu-id="6c486-164">The get accessor computes the number of iterations until a point is determined to be not in the set.</span></span> <span data-ttu-id="6c486-165">Pokud je dosaženo maximálního počtu iterací, je bod v sadě a vrátí se hodnota maxIterations třídy.</span><span class="sxs-lookup"><span data-stu-id="6c486-165">If the maximum iterations is reached, the point is in the set, and the class's maxIterations value is returned.</span></span> <span data-ttu-id="6c486-166">(Počítače generované obrázky, které jsou populární pro Mandelbrot sadu, definují barvy pro počet iterací potřebných k určení, jestli je bod mimo sadu.</span><span class="sxs-lookup"><span data-stu-id="6c486-166">(The computer generated images popularized for the Mandelbrot set define colors for the number of iterations necessary to determine that a point is outside the set.</span></span>

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

<span data-ttu-id="6c486-167">Mandelbrot sada definuje hodnoty v každé souřadnici (x, y) pro hodnoty reálného čísla.</span><span class="sxs-lookup"><span data-stu-id="6c486-167">The Mandelbrot Set defines values at every (x,y) coordinate for real number values.</span></span>
<span data-ttu-id="6c486-168">Který definuje slovník, který by mohl obsahovat nekonečný počet hodnot.</span><span class="sxs-lookup"><span data-stu-id="6c486-168">That defines a dictionary that could contain an infinite number of values.</span></span> <span data-ttu-id="6c486-169">Proto neexistuje žádné úložiště za sadou.</span><span class="sxs-lookup"><span data-stu-id="6c486-169">Therefore, there is no storage behind the set.</span></span> <span data-ttu-id="6c486-170">Místo toho tato třída vypočítá hodnotu pro každý bod, když kód volá `get` přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="6c486-170">Instead, this class computes the value for each point when code calls the `get` accessor.</span></span> <span data-ttu-id="6c486-171">Nepoužívá se žádné základní úložiště.</span><span class="sxs-lookup"><span data-stu-id="6c486-171">There's no underlying storage used.</span></span>

<span data-ttu-id="6c486-172">Pojďme se podívat na poslední použití indexerů, kde indexer přijímá více argumentů různých typů.</span><span class="sxs-lookup"><span data-stu-id="6c486-172">Let's examine one last use of indexers, where the indexer takes multiple arguments of different types.</span></span> <span data-ttu-id="6c486-173">Vezměte v úvahu program, který spravuje historická data o teplotě.</span><span class="sxs-lookup"><span data-stu-id="6c486-173">Consider a program that manages historical temperature data.</span></span> <span data-ttu-id="6c486-174">Tento indexer používá město a datum k nastavení nebo získání vysoké a nízké teploty pro toto umístění:</span><span class="sxs-lookup"><span data-stu-id="6c486-174">This indexer uses a city and a date to set or get the high and low temperatures for that location:</span></span>

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

<span data-ttu-id="6c486-175">Tento příklad vytvoří indexer, který mapuje data o počasí ve dvou různých argumentech: město (reprezentované a `string` ) a datum (reprezentované a `DateTime` ).</span><span class="sxs-lookup"><span data-stu-id="6c486-175">This example creates an indexer that maps weather data on two different arguments: a city (represented by a `string`) and a date (represented by a `DateTime`).</span></span> <span data-ttu-id="6c486-176">Interní úložiště používá dvě `Dictionary` třídy pro reprezentaci dvojrozměrného slovníku.</span><span class="sxs-lookup"><span data-stu-id="6c486-176">The internal storage uses two `Dictionary` classes to represent the two-dimensional dictionary.</span></span> <span data-ttu-id="6c486-177">Veřejné rozhraní API už nepředstavuje základní úložiště.</span><span class="sxs-lookup"><span data-stu-id="6c486-177">The public API no longer represents the underlying storage.</span></span> <span data-ttu-id="6c486-178">Spíše funkce jazyka indexerů vám umožní vytvořit veřejné rozhraní, které představuje vaši abstrakci, i když základní úložiště musí používat jiné typy základních kolekcí.</span><span class="sxs-lookup"><span data-stu-id="6c486-178">Rather, the language features of indexers enables you to create a public interface that represents your abstraction, even though the underlying storage must use different core collection types.</span></span>

<span data-ttu-id="6c486-179">Existují dvě části tohoto kódu, které mohou být někteří vývojáři Neobeznámeni.</span><span class="sxs-lookup"><span data-stu-id="6c486-179">There are two parts of this code that may be unfamiliar to some developers.</span></span> <span data-ttu-id="6c486-180">Tyto dvě `using` direktivy:</span><span class="sxs-lookup"><span data-stu-id="6c486-180">These two `using` directives:</span></span>

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

<span data-ttu-id="6c486-181">vytvoří *alias* pro konstruovaný obecný typ.</span><span class="sxs-lookup"><span data-stu-id="6c486-181">create an *alias* for a constructed generic type.</span></span> <span data-ttu-id="6c486-182">Tyto příkazy umožňují kód později použít výstižnější `DateMeasurements` a `CityDateMeasurements` názvy namísto obecného konstrukce `Dictionary<DateTime, Measurements>` a `Dictionary<string, Dictionary<DateTime, Measurements> >` .</span><span class="sxs-lookup"><span data-stu-id="6c486-182">Those statements enable the code later to use the more descriptive `DateMeasurements` and `CityDateMeasurements` names instead of the generic construction of `Dictionary<DateTime, Measurements>` and `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span></span>
<span data-ttu-id="6c486-183">Tento konstruktor vyžaduje použití plně kvalifikovaného názvu typu na pravé straně `=` znaménka.</span><span class="sxs-lookup"><span data-stu-id="6c486-183">This construct does require using the fully qualified type names on the right side of the `=` sign.</span></span>

<span data-ttu-id="6c486-184">Druhým postupem je obložení časových částí libovolného `DateTime` objektu, který se používá k indexování do kolekcí.</span><span class="sxs-lookup"><span data-stu-id="6c486-184">The second technique is to strip off the time portions of any `DateTime` object used to index into the collections.</span></span> <span data-ttu-id="6c486-185">Rozhraní .NET nezahrnuje typ pouze datum.</span><span class="sxs-lookup"><span data-stu-id="6c486-185">.NET doesn't include a date-only type.</span></span>
<span data-ttu-id="6c486-186">Vývojáři používají `DateTime` typ, ale pomocí `Date` vlastnosti zajistěte, aby libovolný `DateTime` objekt z daného dne byl stejný.</span><span class="sxs-lookup"><span data-stu-id="6c486-186">Developers use the `DateTime` type, but use the `Date` property to ensure that any `DateTime` object from that day are equal.</span></span>

## <a name="summing-up"></a><span data-ttu-id="6c486-187">Sčítání</span><span class="sxs-lookup"><span data-stu-id="6c486-187">Summing Up</span></span>

<span data-ttu-id="6c486-188">Indexery byste měli vytvořit kdykoli, když máte element, který je ve vaší třídě, kde tato vlastnost představuje nejedinou hodnotu, ale spíše kolekci hodnot, kde je každá jednotlivá položka identifikována sadou argumentů.</span><span class="sxs-lookup"><span data-stu-id="6c486-188">You should create indexers anytime you have a property-like element in your class where that property represents not a single value, but rather a collection of values where each individual item is identified by a set of arguments.</span></span> <span data-ttu-id="6c486-189">Tyto argumenty mohou jednoznačně určit, která položka v kolekci má být odkazována.</span><span class="sxs-lookup"><span data-stu-id="6c486-189">Those arguments can uniquely identify which item in the collection should be referenced.</span></span>
<span data-ttu-id="6c486-190">Indexery rozšiřuje koncept [vlastností](properties.md), kde se člen považuje za datovou položku z vnějšku třídy, ale jako metodu v rámci.</span><span class="sxs-lookup"><span data-stu-id="6c486-190">Indexers extend the concept of [properties](properties.md), where a member is treated like a data item from outside the class, but like a method on the inside.</span></span> <span data-ttu-id="6c486-191">Indexery umožňují argumentům vyhledat jednu položku ve vlastnosti, která představuje sadu položek.</span><span class="sxs-lookup"><span data-stu-id="6c486-191">Indexers allow arguments to find a single item in a property that represents a set of items.</span></span>
