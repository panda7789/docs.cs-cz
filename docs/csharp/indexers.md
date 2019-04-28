---
title: Indexery
description: Další informace o C# indexery a jak implementovat indexovaných vlastností, které jsou vlastnosti odkazovat pomocí jedné nebo více argumentů.
ms.date: 06/20/2016
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: a13163cb6bd835dfdd16c83c905c134eb8a86e7d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672026"
---
# <a name="indexers"></a><span data-ttu-id="7b84e-103">Indexery</span><span class="sxs-lookup"><span data-stu-id="7b84e-103">Indexers</span></span>

<span data-ttu-id="7b84e-104">*Indexery* jsou podobné vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="7b84e-104">*Indexers* are similar to properties.</span></span> <span data-ttu-id="7b84e-105">Ve spoustě ohledů indexery sestavení na stejné funkce jako jazyk [vlastnosti](properties.md).</span><span class="sxs-lookup"><span data-stu-id="7b84e-105">In many ways indexers build on the same language features as [properties](properties.md).</span></span> <span data-ttu-id="7b84e-106">Indexery povolují *indexované* vlastnosti: vlastnosti odkazovat pomocí jedné nebo více argumentů.</span><span class="sxs-lookup"><span data-stu-id="7b84e-106">Indexers enable *indexed* properties: properties referenced using one or more arguments.</span></span> <span data-ttu-id="7b84e-107">Tyto argumenty poskytuje index do některé kolekce hodnot.</span><span class="sxs-lookup"><span data-stu-id="7b84e-107">Those arguments provide an index into some collection of values.</span></span>

## <a name="indexer-syntax"></a><span data-ttu-id="7b84e-108">Syntaxe indexeru</span><span class="sxs-lookup"><span data-stu-id="7b84e-108">Indexer Syntax</span></span>

<span data-ttu-id="7b84e-109">Přístup indexeru prostřednictvím název proměnné a hranaté závorky.</span><span class="sxs-lookup"><span data-stu-id="7b84e-109">You access an indexer through a variable name and square brackets.</span></span> <span data-ttu-id="7b84e-110">Umístíte argumenty indexeru v závorkách:</span><span class="sxs-lookup"><span data-stu-id="7b84e-110">You place the indexer arguments inside the brackets:</span></span>

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

<span data-ttu-id="7b84e-111">Deklarovat pomocí indexerů `this` klíčového slova jako názvu vlastnosti a deklarační popisovač argumenty v hranatých závorkách.</span><span class="sxs-lookup"><span data-stu-id="7b84e-111">You declare indexers using the `this` keyword as the property name, and declaring the arguments within square brackets.</span></span> <span data-ttu-id="7b84e-112">Tato deklarace odpovídají využití je znázorněno v předchozím odstavci:</span><span class="sxs-lookup"><span data-stu-id="7b84e-112">This declaration would match the usage shown in the previous paragraph:</span></span>

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

<span data-ttu-id="7b84e-113">Z tohoto počátečního příkladu uvidíte vztah mezi syntaxi pro vlastnosti a indexery.</span><span class="sxs-lookup"><span data-stu-id="7b84e-113">From this initial example, you can see the relationship between the syntax for properties and for indexers.</span></span> <span data-ttu-id="7b84e-114">Tato analogie přenáší přes většinu pravidel syntaxe pro indexování.</span><span class="sxs-lookup"><span data-stu-id="7b84e-114">This analogy carries through most of the syntax rules for indexers.</span></span> <span data-ttu-id="7b84e-115">Indexery můžete mít libovolný platný přístupu modifikátory přístupu (veřejné, chráněné vnitřní, chráněný, interní, privátní nebo privátní chráněné).</span><span class="sxs-lookup"><span data-stu-id="7b84e-115">Indexers can have any valid access modifiers (public, protected internal, protected, internal, private or private protected).</span></span> <span data-ttu-id="7b84e-116">Mohou být zapečetěné, virtuální nebo abstraktní.</span><span class="sxs-lookup"><span data-stu-id="7b84e-116">They may be sealed, virtual, or abstract.</span></span> <span data-ttu-id="7b84e-117">Stejně jako u vlastnosti, můžete zadat různé přístupu modifikátory přístupu pro metodu get a přístupové objekty set v indexeru.</span><span class="sxs-lookup"><span data-stu-id="7b84e-117">As with properties, you can specify different access modifiers for the get and set accessors in an indexer.</span></span>
<span data-ttu-id="7b84e-118">Můžete také zadat indexery jen pro čtení (vynecháním přístupový objekt set) nebo pouze pro zápis indexery (vynecháním přistupující objekt get).</span><span class="sxs-lookup"><span data-stu-id="7b84e-118">You may also specify read-only indexers (by omitting the set accessor), or write-only indexers (by omitting the get accessor).</span></span>

<span data-ttu-id="7b84e-119">Můžete použít téměř vše, co jste Učte se od práce s vlastnostmi pro indexery.</span><span class="sxs-lookup"><span data-stu-id="7b84e-119">You can apply almost everything you learn from working with properties to indexers.</span></span> <span data-ttu-id="7b84e-120">Jedinou výjimkou tohoto pravidla je *automaticky implementované vlastnosti*.</span><span class="sxs-lookup"><span data-stu-id="7b84e-120">The only exception to that rule is *auto implemented properties*.</span></span> <span data-ttu-id="7b84e-121">Kompilátor nemůže vždy generovat správný úložiště pro indexer.</span><span class="sxs-lookup"><span data-stu-id="7b84e-121">The compiler cannot always generate the correct storage for an indexer.</span></span>

<span data-ttu-id="7b84e-122">Přítomnost argumenty odkažte na položku v sadě položek odlišuje od vlastnosti indexery.</span><span class="sxs-lookup"><span data-stu-id="7b84e-122">The presence of arguments to reference an item in a set of items distinguishes indexers from properties.</span></span> <span data-ttu-id="7b84e-123">Několik indexerů může definovat podle typu, jako argument uvádí pro každý indexer je jedinečný.</span><span class="sxs-lookup"><span data-stu-id="7b84e-123">You may define multiple indexers on a type, as long as the argument lists for each indexer is unique.</span></span> <span data-ttu-id="7b84e-124">Podíváme na různé scénáře ve kterém můžete použít jeden nebo více indexerů v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="7b84e-124">Let's explore different scenarios where you might use one or more indexers in a class definition.</span></span> 

## <a name="scenarios"></a><span data-ttu-id="7b84e-125">Scénáře</span><span class="sxs-lookup"><span data-stu-id="7b84e-125">Scenarios</span></span>

<span data-ttu-id="7b84e-126">Můžete definovat *indexery* v typu při jeho API modely některé kolekce, ve kterém definujete argumenty do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="7b84e-126">You would define *indexers* in your type when its API models some collection where you define the arguments to that collection.</span></span> <span data-ttu-id="7b84e-127">Vaše indexerů může nebo nemusí mapují přímo na typy kolekcí, které jsou součástí rozhraní .NET core framework.</span><span class="sxs-lookup"><span data-stu-id="7b84e-127">Your indexers may or may not map directly to the collection types that are part of the .NET core framework.</span></span> <span data-ttu-id="7b84e-128">Typ může být další úkoly, kromě modelování kolekce.</span><span class="sxs-lookup"><span data-stu-id="7b84e-128">Your type may have other responsibilities in addition to modeling a collection.</span></span>
<span data-ttu-id="7b84e-129">Indexery povolují, abychom vám poskytli rozhraní API, která odpovídá abstrakce váš typ bez vystavení vnitřní podrobnosti, jak jsou uložená nebo vypočítané hodnoty pro tento odběr.</span><span class="sxs-lookup"><span data-stu-id="7b84e-129">Indexers enable you to provide the API that matches your type's abstraction without exposing the inner details of how the values for that abstraction are stored or computed.</span></span>

<span data-ttu-id="7b84e-130">Pojďme si projít některé běžné scénáře použití *indexery*.</span><span class="sxs-lookup"><span data-stu-id="7b84e-130">Let's walk through some of the common scenarios for using *indexers*.</span></span> <span data-ttu-id="7b84e-131">Můžete přistupovat [složky s ukázkou pro indexery](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span><span class="sxs-lookup"><span data-stu-id="7b84e-131">You can access the [sample folder for indexers](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span></span> <span data-ttu-id="7b84e-132">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="7b84e-132">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="arrays-and-vectors"></a><span data-ttu-id="7b84e-133">Pole a vektorů</span><span class="sxs-lookup"><span data-stu-id="7b84e-133">Arrays and Vectors</span></span>

<span data-ttu-id="7b84e-134">Jednou z nejběžnějších scénářů pro vytváření indexerů je modely typu pole nebo vektoru.</span><span class="sxs-lookup"><span data-stu-id="7b84e-134">One of the most common scenarios for creating indexers is when your type models an array, or a vector.</span></span> <span data-ttu-id="7b84e-135">Indexer pro modelování uspořádaný seznam dat můžete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="7b84e-135">You can create an indexer to model an ordered list of data.</span></span> 

<span data-ttu-id="7b84e-136">Výhoda vytváření vlastních indexeru je, že můžete definovat úložiště pro danou kolekci tak, aby odpovídala vašim potřebám.</span><span class="sxs-lookup"><span data-stu-id="7b84e-136">The advantage of creating your own indexer is that you can define the storage for that collection to suit your needs.</span></span> <span data-ttu-id="7b84e-137">Představte si situaci, kdy váš typ modely historická data, která je příliš velký, aby najednou načíst do paměti.</span><span class="sxs-lookup"><span data-stu-id="7b84e-137">Imagine a scenario where your type models historical data that is too large to load into memory at once.</span></span> <span data-ttu-id="7b84e-138">Budete muset načtení a uvolnění oddíly kolekce na základě využití.</span><span class="sxs-lookup"><span data-stu-id="7b84e-138">You need to load and unload sections of the collection based on usage.</span></span> <span data-ttu-id="7b84e-139">Následující příklad modely toto chování.</span><span class="sxs-lookup"><span data-stu-id="7b84e-139">The example following models this behavior.</span></span> <span data-ttu-id="7b84e-140">Oznámí na existují jak mnoho datových bodů.</span><span class="sxs-lookup"><span data-stu-id="7b84e-140">It reports on how many data points exist.</span></span> <span data-ttu-id="7b84e-141">Vytvoří stránky pro uložení části dat na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="7b84e-141">It creates pages to hold sections of the data on demand.</span></span> <span data-ttu-id="7b84e-142">Odebírá stránky z paměti, aby uvolnil prostor pro stránky vyžaduje novější požadavky.</span><span class="sxs-lookup"><span data-stu-id="7b84e-142">It removes pages from memory to make room for pages needed by more recent requests.</span></span>

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

<span data-ttu-id="7b84e-143">Můžete postupovat podle tohoto idiomu návrhu modelovat jakýkoli druh kolekce Pokud existují oprávněné důvody nenačte celá sada dat do kolekce v paměti.</span><span class="sxs-lookup"><span data-stu-id="7b84e-143">You can follow this design idiom to model any sort of collection where there are good reasons not to load the entire set of data into an in- memory collection.</span></span> <span data-ttu-id="7b84e-144">Všimněte si, že `Page` třída je privátní vnořené třídy, který není součástí veřejného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7b84e-144">Notice that the `Page` class is a private nested class that is not part of the public interface.</span></span> <span data-ttu-id="7b84e-145">Tyto podrobnosti jsou skryté všichni uživatelé této třídy.</span><span class="sxs-lookup"><span data-stu-id="7b84e-145">Those details are hidden from any users of this class.</span></span>

### <a name="dictionaries"></a><span data-ttu-id="7b84e-146">slovníky</span><span class="sxs-lookup"><span data-stu-id="7b84e-146">Dictionaries</span></span>

<span data-ttu-id="7b84e-147">Další z typických možností je, když budete potřebovat k modelování slovníku nebo mapy.</span><span class="sxs-lookup"><span data-stu-id="7b84e-147">Another common scenario is when you need to model a dictionary or a map.</span></span> <span data-ttu-id="7b84e-148">Tento scénář je typ ukládá hodnoty na základě klíče, obvykle text klíče.</span><span class="sxs-lookup"><span data-stu-id="7b84e-148">This scenario is when your type stores values based on key, typically text keys.</span></span> <span data-ttu-id="7b84e-149">Tento příklad vytvoří slovník, který mapuje argumenty příkazového řádku [výrazy lambda](delegates-overview.md) , které spravují tyto možnosti.</span><span class="sxs-lookup"><span data-stu-id="7b84e-149">This example creates a dictionary that maps command line arguments to [lambda expressions](delegates-overview.md) that manage those options.</span></span> <span data-ttu-id="7b84e-150">Následující příklad ukazuje dvě třídy: `ArgsActions` třída, která mapuje možnosti příkazového řádku pro `Action` delegovat a `ArgsProcessor` , která používá `ArgsActions` ke spuštění každého `Action` při výskytu této možnosti.</span><span class="sxs-lookup"><span data-stu-id="7b84e-150">The following example shows two classes: an `ArgsActions` class that maps a command line option to an `Action` delegate, and an `ArgsProcessor` that uses the `ArgsActions` to execute each `Action` when it encounters that option.</span></span>

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

<span data-ttu-id="7b84e-151">V tomto příkladu `ArgsAction` kolekce úzce mapuje na zdrojové kolekce.</span><span class="sxs-lookup"><span data-stu-id="7b84e-151">In this example, the `ArgsAction` collection maps closely to the underlying collection.</span></span>
<span data-ttu-id="7b84e-152">`get` Určuje-li dané možnosti není nakonfigurovaná.</span><span class="sxs-lookup"><span data-stu-id="7b84e-152">The `get` determines if a given option has been configured.</span></span> <span data-ttu-id="7b84e-153">Pokud ano, vrátí `Action` přidružené k této možnosti.</span><span class="sxs-lookup"><span data-stu-id="7b84e-153">If so, it returns the `Action` associated with that option.</span></span> <span data-ttu-id="7b84e-154">Pokud ne, vrátí `Action` , který nemá žádný účinek.</span><span class="sxs-lookup"><span data-stu-id="7b84e-154">If not, it returns an `Action` that does nothing.</span></span> <span data-ttu-id="7b84e-155">Veřejný přístupový objekt neobsahuje `set` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="7b84e-155">The public accessor does not include a `set` accessor.</span></span> <span data-ttu-id="7b84e-156">Místo toho návrh s použitím veřejné metody pro nastavení možností.</span><span class="sxs-lookup"><span data-stu-id="7b84e-156">Rather, the design using a public method for setting options.</span></span>

### <a name="multi-dimensional-maps"></a><span data-ttu-id="7b84e-157">Multidimenzionální mapy</span><span class="sxs-lookup"><span data-stu-id="7b84e-157">Multi-Dimensional Maps</span></span>

<span data-ttu-id="7b84e-158">Můžete vytvořit indexerů, které používají více argumentů.</span><span class="sxs-lookup"><span data-stu-id="7b84e-158">You can create indexers that use multiple arguments.</span></span> <span data-ttu-id="7b84e-159">Kromě toho tyto argumenty nejsou omezeny na být stejného typu.</span><span class="sxs-lookup"><span data-stu-id="7b84e-159">In addition, those arguments are not constrained to be the same type.</span></span> <span data-ttu-id="7b84e-160">Pojďme se podívat na dva příklady.</span><span class="sxs-lookup"><span data-stu-id="7b84e-160">Let's look at two examples.</span></span>   

<span data-ttu-id="7b84e-161">První příklad ukazuje třídu, která generuje hodnoty pro skupinu Mandelbrot.</span><span class="sxs-lookup"><span data-stu-id="7b84e-161">The first example shows a class that generates values for a Mandelbrot set.</span></span> <span data-ttu-id="7b84e-162">Další informace o matematiku za čtení [v tomto článku](https://en.wikipedia.org/wiki/Mandelbrot_set).</span><span class="sxs-lookup"><span data-stu-id="7b84e-162">For more information on the mathematics behind the set, read [this article](https://en.wikipedia.org/wiki/Mandelbrot_set).</span></span> <span data-ttu-id="7b84e-163">Indexer používá dvě Double pro definování bod v X, Y roviny.</span><span class="sxs-lookup"><span data-stu-id="7b84e-163">The indexer uses two doubles to define a point in the X, Y plane.</span></span>
<span data-ttu-id="7b84e-164">Přístupový objekt get vypočítá počet iterací, dokud se určuje bod tak, aby nebyl v sadě.</span><span class="sxs-lookup"><span data-stu-id="7b84e-164">The get accessor computes the number of iterations until a point is determined to be not in the set.</span></span> <span data-ttu-id="7b84e-165">Pokud je dosažen maximální počet iterací, bod nachází v sadě a vrátí se hodnota maxIterations třídy.</span><span class="sxs-lookup"><span data-stu-id="7b84e-165">If the maximum iterations is reached, the point is in the set, and the class's maxIterations value is returned.</span></span> <span data-ttu-id="7b84e-166">(Počítače, generovány Image, který pro sadu Mandelbrot definovat barvy pro počet iterací, které jsou nezbytné k určení, že bod je mimo sadu.</span><span class="sxs-lookup"><span data-stu-id="7b84e-166">(The computer generated images popularized for the Mandelbrot set define colors for the number of iterations necessary to determine that a point is outside the set.</span></span>

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

<span data-ttu-id="7b84e-167">Sada Mandelbrot definuje hodnoty v každé (x, y) koordinovat skutečných číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7b84e-167">The Mandelbrot Set defines values at every (x,y) coordinate for real number values.</span></span>
<span data-ttu-id="7b84e-168">Který definuje slovník, který může obsahovat neomezený počet hodnot.</span><span class="sxs-lookup"><span data-stu-id="7b84e-168">That defines a dictionary that could contain an infinite number of values.</span></span> <span data-ttu-id="7b84e-169">Proto neexistuje žádné úložiště za sady.</span><span class="sxs-lookup"><span data-stu-id="7b84e-169">Therefore, there is no storage behind the set.</span></span> <span data-ttu-id="7b84e-170">Místo toho tuto třídu vypočítá hodnotu pro každý bod, když kód volá `get` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="7b84e-170">Instead, this class computes the value for each point when code calls the `get` accessor.</span></span> <span data-ttu-id="7b84e-171">Neexistuje žádný použité úložiště.</span><span class="sxs-lookup"><span data-stu-id="7b84e-171">There's no underlying storage used.</span></span>

<span data-ttu-id="7b84e-172">Podívejme se na poslední užívání indexery, kdy indexer využívá více argumentů různých typů.</span><span class="sxs-lookup"><span data-stu-id="7b84e-172">Let's examine one last use of indexers, where the indexer takes multiple arguments of different types.</span></span> <span data-ttu-id="7b84e-173">Vezměte v úvahu program, který spravuje data o teplotě historických.</span><span class="sxs-lookup"><span data-stu-id="7b84e-173">Consider a program that manages historical temperature data.</span></span> <span data-ttu-id="7b84e-174">Indexer využívá Město a datum nastavit nebo získat teploty vysoké a nízké pro toto umístění:</span><span class="sxs-lookup"><span data-stu-id="7b84e-174">This indexer uses a city and a date to set or get the high and low temperatures for that location:</span></span>

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

<span data-ttu-id="7b84e-175">Tento příklad vytvoří indexer, který mapuje data o počasí na dva různé argumenty: města (reprezentované `string`) a data (reprezentované `DateTime`).</span><span class="sxs-lookup"><span data-stu-id="7b84e-175">This example creates an indexer that maps weather data on two different arguments: a city (represented by a `string`) and a date (represented by a `DateTime`).</span></span> <span data-ttu-id="7b84e-176">Interní úložiště používá dvě `Dictionary` třídy, které představují dvojrozměrné slovníku.</span><span class="sxs-lookup"><span data-stu-id="7b84e-176">The internal storage uses two `Dictionary` classes to represent the two-dimensional dictionary.</span></span> <span data-ttu-id="7b84e-177">Veřejné rozhraní API už nebude představuje základní úložiště.</span><span class="sxs-lookup"><span data-stu-id="7b84e-177">The public API no longer represents the underlying storage.</span></span> <span data-ttu-id="7b84e-178">Místo toho funkce jazyků indexerů umožňuje vytvářet veřejné rozhraní, která představuje abstrakci, i když základního úložiště musí používat různé základní typy kolekcí.</span><span class="sxs-lookup"><span data-stu-id="7b84e-178">Rather, the language features of indexers enables you to create a public interface that represents your abstraction, even though the underlying storage must use different core collection types.</span></span>

<span data-ttu-id="7b84e-179">Existují dvě části tohoto kódu, který může být obeznámeni pro některé vývojáře.</span><span class="sxs-lookup"><span data-stu-id="7b84e-179">There are two parts of this code that may be unfamiliar to some developers.</span></span> <span data-ttu-id="7b84e-180">Tyto dvě `using` příkazy:</span><span class="sxs-lookup"><span data-stu-id="7b84e-180">These two `using` statements:</span></span>

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

<span data-ttu-id="7b84e-181">vytvoření *alias* pro Konstruovaný obecný typ.</span><span class="sxs-lookup"><span data-stu-id="7b84e-181">create an *alias* for a constructed generic type.</span></span> <span data-ttu-id="7b84e-182">Tyto příkazy Povolit kódu později použít více popisné `DateMeasurements` a `CityDateMeasurements` názvy místo obecné konstrukce `Dictionary<DateTime, Measurements>` a `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span><span class="sxs-lookup"><span data-stu-id="7b84e-182">Those statements enable the code later to use the more descriptive `DateMeasurements` and `CityDateMeasurements` names instead of the generic construction of `Dictionary<DateTime, Measurements>` and `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span></span> <span data-ttu-id="7b84e-183">Tento konstruktor vyžaduje použití názvů plně kvalifikovaný typ na pravé straně `=` přihlašování.</span><span class="sxs-lookup"><span data-stu-id="7b84e-183">This construct does require using the fully qualified type names on the right side of the `=` sign.</span></span>

<span data-ttu-id="7b84e-184">Druhý postup je pro odstranění vypnout části času žádné `DateTime` objekt použitý k indexu do kolekce.</span><span class="sxs-lookup"><span data-stu-id="7b84e-184">The second technique is to strip off the time portions of any `DateTime` object used to index into the collections.</span></span> <span data-ttu-id="7b84e-185">Rozhraní .NET framework nezahrnuje jediný typ Date.</span><span class="sxs-lookup"><span data-stu-id="7b84e-185">The .NET framework does not include a Date only type.</span></span>
<span data-ttu-id="7b84e-186">Vývojáři `DateTime` typu, ale použít `Date` vlastnost a zkontrolujte, že některé `DateTime` objektu v daný den jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="7b84e-186">Developers use the `DateTime` type, but use the `Date` property to ensure that any `DateTime` object from that day are equal.</span></span>

## <a name="summing-up"></a><span data-ttu-id="7b84e-187">Shrnutí</span><span class="sxs-lookup"><span data-stu-id="7b84e-187">Summing Up</span></span>

<span data-ttu-id="7b84e-188">Indexery byste měli vytvořit kdykoli mít element jako vlastnost ve své třídě, kde tato vlastnost představuje jednu hodnotu, ale spíše kolekci hodnot, kde jednotlivé položky je identifikován sady argumentů.</span><span class="sxs-lookup"><span data-stu-id="7b84e-188">You should create indexers anytime you have a property-like element in your class where that property represents not a single value, but rather a collection of values where each individual item is identified by a set of arguments.</span></span> <span data-ttu-id="7b84e-189">Tyto argumenty může jedinečně identifikovat, která položka v kolekci by se měla odkazovat.</span><span class="sxs-lookup"><span data-stu-id="7b84e-189">Those arguments can uniquely identify which item in the collection should be referenced.</span></span>
<span data-ttu-id="7b84e-190">Indexery rozšířit koncept [vlastnosti](properties.md), kdy je člen zpracován jako položku dat z vně třídy, ale jako metody na straně.</span><span class="sxs-lookup"><span data-stu-id="7b84e-190">Indexers extend the concept of [properties](properties.md), where a member is treated like a data item from outside the class, but like a method on the side.</span></span> <span data-ttu-id="7b84e-191">Indexery povolit argumenty k nalezení konkrétní položce v vlastnost, která představuje sadu položek.</span><span class="sxs-lookup"><span data-stu-id="7b84e-191">Indexers allow arguments to find a single item in a property that represents a set of items.</span></span>
