---
title: Operace projekce (C#)
description: Přečtěte si o operacích projekce. Tyto operace transformují objekt do nového formuláře, který se často skládá jenom z vlastností, které se použijí později.
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: 289100ac9afcfc0d5b93b5f963adc0a123e0a5af
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299159"
---
# <a name="projection-operations-c"></a><span data-ttu-id="b50eb-104">Operace projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="b50eb-104">Projection Operations (C#)</span></span>
<span data-ttu-id="b50eb-105">Projekce odkazuje na operaci transformace objektu do nového formuláře, který se často skládá pouze z těchto vlastností, které budou následně použity.</span><span class="sxs-lookup"><span data-stu-id="b50eb-105">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="b50eb-106">Pomocí projekce můžete vytvořit nový typ, který je sestaven z každého objektu.</span><span class="sxs-lookup"><span data-stu-id="b50eb-106">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="b50eb-107">Můžete promítnout vlastnost a na ní provést matematickou funkci.</span><span class="sxs-lookup"><span data-stu-id="b50eb-107">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="b50eb-108">Původní objekt můžete také promítnout beze změny.</span><span class="sxs-lookup"><span data-stu-id="b50eb-108">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="b50eb-109">Standardní metody operátoru dotazu, které provádějí projekci, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="b50eb-109">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b50eb-110">Metody</span><span class="sxs-lookup"><span data-stu-id="b50eb-110">Methods</span></span>  
  
|<span data-ttu-id="b50eb-111">Název metody</span><span class="sxs-lookup"><span data-stu-id="b50eb-111">Method Name</span></span>|<span data-ttu-id="b50eb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b50eb-112">Description</span></span>|<span data-ttu-id="b50eb-113">Syntaxe výrazu dotazu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b50eb-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="b50eb-114">Další informace</span><span class="sxs-lookup"><span data-stu-id="b50eb-114">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="b50eb-115">Vyberte</span><span class="sxs-lookup"><span data-stu-id="b50eb-115">Select</span></span>|<span data-ttu-id="b50eb-116">Projekty hodnoty, které jsou založeny na transformační funkci.</span><span class="sxs-lookup"><span data-stu-id="b50eb-116">Projects values that are based on a transform function.</span></span>|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b50eb-117">Operátor SelectMany</span><span class="sxs-lookup"><span data-stu-id="b50eb-117">SelectMany</span></span>|<span data-ttu-id="b50eb-118">Projektuje sekvence hodnot, které jsou založeny na transformační funkci a poté jsou shrnuty do jedné sekvence.</span><span class="sxs-lookup"><span data-stu-id="b50eb-118">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="b50eb-119">Použít více `from` klauzulí</span><span class="sxs-lookup"><span data-stu-id="b50eb-119">Use multiple `from` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="b50eb-120">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="b50eb-120">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="b50eb-121">Vyberte</span><span class="sxs-lookup"><span data-stu-id="b50eb-121">Select</span></span>  
 <span data-ttu-id="b50eb-122">V následujícím příkladu je použita `select` klauzule pro projekt prvního písmene z každého řetězce v seznamu řetězců.</span><span class="sxs-lookup"><span data-stu-id="b50eb-122">The following example uses the `select` clause to project the first letter from each string in a list of strings.</span></span>  
  
```csharp  
List<string> words = new List<string>() { "an", "apple", "a", "day" };  
  
var query = from word in words  
            select word.Substring(0, 1);  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    a  
    a  
    a  
    d  
*/  
```  
  
### <a name="selectmany"></a><span data-ttu-id="b50eb-123">Operátor SelectMany</span><span class="sxs-lookup"><span data-stu-id="b50eb-123">SelectMany</span></span>  
 <span data-ttu-id="b50eb-124">Následující příklad používá více `from` klauzulí pro každé slovo z každého řetězce v seznamu řetězců.</span><span class="sxs-lookup"><span data-stu-id="b50eb-124">The following example uses multiple `from` clauses  to project each word from each string in a list of strings.</span></span>  
  
```csharp  
List<string> phrases = new List<string>() { "an apple a day", "the quick brown fox" };  
  
var query = from phrase in phrases  
            from word in phrase.Split(' ')  
            select word;  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    an  
    apple  
    a  
    day  
    the  
    quick  
    brown  
    fox  
*/  
```  
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="b50eb-125">Vybrat versus operátor SelectMany</span><span class="sxs-lookup"><span data-stu-id="b50eb-125">Select versus SelectMany</span></span>  
 <span data-ttu-id="b50eb-126">Jak obojí, tak `Select()` `SelectMany()` je vytvořit výslednou hodnotu (nebo hodnoty) ze zdrojových hodnot.</span><span class="sxs-lookup"><span data-stu-id="b50eb-126">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="b50eb-127">`Select()`vytvoří jednu výslednou hodnotu pro každou zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b50eb-127">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="b50eb-128">Celkový výsledek je tedy kolekce, která má stejný počet prvků jako zdrojová kolekce.</span><span class="sxs-lookup"><span data-stu-id="b50eb-128">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="b50eb-129">Naproti tomu `SelectMany()` vytvoří jeden celkový výsledek, který obsahuje zřetězené dílčí kolekce z každé zdrojové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b50eb-129">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="b50eb-130">Funkce transformace, která je předána jako argument pro, `SelectMany()` musí vracet vyčíslitelné sekvence hodnot pro každou zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b50eb-130">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="b50eb-131">Tyto vyčíslitelné sekvence jsou poté zřetězeny nástrojem `SelectMany()` , aby vytvořily jednu velkou sekvenci.</span><span class="sxs-lookup"><span data-stu-id="b50eb-131">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="b50eb-132">Následující dva ilustrace znázorňují koncepční rozdíl mezi akcemi těchto dvou metod.</span><span class="sxs-lookup"><span data-stu-id="b50eb-132">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="b50eb-133">V každém případě Předpokládejme, že funkce Selector (transformace) vybere pole květů z každé zdrojové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b50eb-133">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="b50eb-134">Tento obrázek znázorňuje, jak `Select()` vrátí kolekci, která má stejný počet prvků jako zdrojová kolekce.</span><span class="sxs-lookup"><span data-stu-id="b50eb-134">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 ![Obrázek, který zobrazuje akci výběru&#40;&#41;](./media/projection-operations/select-action-graphic.png)  
  
 <span data-ttu-id="b50eb-136">Tento obrázek znázorňuje, jak `SelectMany()` zřetězí mezilehlé pořadí polí do jedné konečné výsledné hodnoty, která obsahuje všechny hodnoty z každého mezilehlého pole.</span><span class="sxs-lookup"><span data-stu-id="b50eb-136">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 ![Obrázek znázorňující akci operátor SelectMany&#40;&#41;.](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a><span data-ttu-id="b50eb-138">Příklad kódu</span><span class="sxs-lookup"><span data-stu-id="b50eb-138">Code Example</span></span>  
 <span data-ttu-id="b50eb-139">Následující příklad porovnává chování `Select()` a `SelectMany()` .</span><span class="sxs-lookup"><span data-stu-id="b50eb-139">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="b50eb-140">Kód vytvoří "kytici" květů z každého seznamu názvů květin ve zdrojové kolekci.</span><span class="sxs-lookup"><span data-stu-id="b50eb-140">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="b50eb-141">V tomto příkladu "jediná hodnota", kterou funkce transformace používá, <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> je sám kolekcí hodnot.</span><span class="sxs-lookup"><span data-stu-id="b50eb-141">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="b50eb-142">K tomu je zapotřebí nadbytečné `foreach` smyčky pro zobrazení výčtu každého řetězce v každé dílčí sekvenci.</span><span class="sxs-lookup"><span data-stu-id="b50eb-142">This requires the extra `foreach` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
```csharp  
class Bouquet  
{  
    public List<string> Flowers { get; set; }  
}  
  
static void SelectVsSelectMany()  
{  
    List<Bouquet> bouquets = new List<Bouquet>() {  
        new Bouquet { Flowers = new List<string> { "sunflower", "daisy", "daffodil", "larkspur" }},  
        new Bouquet{ Flowers = new List<string> { "tulip", "rose", "orchid" }},  
        new Bouquet{ Flowers = new List<string> { "gladiolis", "lily", "snapdragon", "aster", "protea" }},  
        new Bouquet{ Flowers = new List<string> { "larkspur", "lilac", "iris", "dahlia" }}  
    };  
  
    // *********** Select ***********
    IEnumerable<List<string>> query1 = bouquets.Select(bq => bq.Flowers);  
  
    // ********* SelectMany *********  
    IEnumerable<string> query2 = bouquets.SelectMany(bq => bq.Flowers);  
  
    Console.WriteLine("Results by using Select():");  
    // Note the extra foreach loop here.  
    foreach (IEnumerable<String> collection in query1)  
        foreach (string item in collection)  
            Console.WriteLine(item);  
  
    Console.WriteLine("\nResults by using SelectMany():");  
    foreach (string item in query2)  
        Console.WriteLine(item);  
  
    /* This code produces the following output:  
  
       Results by using Select():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
  
       Results by using SelectMany():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
    */  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b50eb-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b50eb-143">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="b50eb-144">Přehled standardních operátorů dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="b50eb-144">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="b50eb-145">select – klauzule (C#)</span><span class="sxs-lookup"><span data-stu-id="b50eb-145">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
- [<span data-ttu-id="b50eb-146">Jak naplnit kolekce objektů z více zdrojů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b50eb-146">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="b50eb-147">Rozdělení souboru na více souborů pomocí skupin (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b50eb-147">How to split a file into many files by using groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
