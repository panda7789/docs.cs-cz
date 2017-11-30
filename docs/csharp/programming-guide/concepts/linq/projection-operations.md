---
title: Operace projekce (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a05a4f228e64405ba24d967193d9e7a487ae473
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="projection-operations-c"></a><span data-ttu-id="6d94c-102">Operace projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="6d94c-102">Projection Operations (C#)</span></span>
<span data-ttu-id="6d94c-103">Projekce odkazuje na operaci transformace objekt do nový formulář, který často se skládá jenom z těchto vlastností, které budou následně použity.</span><span class="sxs-lookup"><span data-stu-id="6d94c-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="6d94c-104">Pomocí projekce můžete vytvořit nový typ, který je sestaven z každého objektu.</span><span class="sxs-lookup"><span data-stu-id="6d94c-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="6d94c-105">Můžete projektu vlastnosti a na něm provádět matematické funkce.</span><span class="sxs-lookup"><span data-stu-id="6d94c-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="6d94c-106">Můžete také promítnout původní objekt bez provedení změn.</span><span class="sxs-lookup"><span data-stu-id="6d94c-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="6d94c-107">Metody operátor standardní dotaz, které provádějí projekce jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="6d94c-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6d94c-108">Metody</span><span class="sxs-lookup"><span data-stu-id="6d94c-108">Methods</span></span>  
  
|<span data-ttu-id="6d94c-109">Název metody</span><span class="sxs-lookup"><span data-stu-id="6d94c-109">Method Name</span></span>|<span data-ttu-id="6d94c-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6d94c-110">Description</span></span>|<span data-ttu-id="6d94c-111">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6d94c-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="6d94c-112">Další informace</span><span class="sxs-lookup"><span data-stu-id="6d94c-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="6d94c-113">Vyberte</span><span class="sxs-lookup"><span data-stu-id="6d94c-113">Select</span></span>|<span data-ttu-id="6d94c-114">Projekty hodnoty, které jsou založeny na funkce transformace.</span><span class="sxs-lookup"><span data-stu-id="6d94c-114">Projects values that are based on a transform function.</span></span>|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6d94c-115">Označit více</span><span class="sxs-lookup"><span data-stu-id="6d94c-115">SelectMany</span></span>|<span data-ttu-id="6d94c-116">Projekty pořadí hodnot, které jsou založeny na funkce transformace a pak sloučí je do jedné sekvence.</span><span class="sxs-lookup"><span data-stu-id="6d94c-116">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="6d94c-117">Použití více `from` – klauzule</span><span class="sxs-lookup"><span data-stu-id="6d94c-117">Use multiple `from` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="6d94c-118">Příklady syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="6d94c-118">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="6d94c-119">Vyberte</span><span class="sxs-lookup"><span data-stu-id="6d94c-119">Select</span></span>  
 <span data-ttu-id="6d94c-120">Následující příklad používá `select` klauzule do projektu první písmeno z každé řetězec v seznamu řetězců.</span><span class="sxs-lookup"><span data-stu-id="6d94c-120">The following example uses the `select` clause to project the first letter from each string in a list of strings.</span></span>  
  
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
  
### <a name="selectmany"></a><span data-ttu-id="6d94c-121">Označit více</span><span class="sxs-lookup"><span data-stu-id="6d94c-121">SelectMany</span></span>  
 <span data-ttu-id="6d94c-122">Následující příklad používá více `from` klauzule do projektu jednotlivých slov z každé řetězec v seznamu řetězců.</span><span class="sxs-lookup"><span data-stu-id="6d94c-122">The following example uses multiple `from` clauses  to project each word from each string in a list of strings.</span></span>  
  
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
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="6d94c-123">Vyberte a označit více</span><span class="sxs-lookup"><span data-stu-id="6d94c-123">Select versus SelectMany</span></span>  
 <span data-ttu-id="6d94c-124">Pracovní i `Select()` a `SelectMany()` z hodnot zdroj je vytvořit hodnotu výsledek (nebo hodnoty).</span><span class="sxs-lookup"><span data-stu-id="6d94c-124">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="6d94c-125">`Select()`vytvoří jednu výslednou hodnotu pro každou zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6d94c-125">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="6d94c-126">Kolekce, která má stejný počet elementů jako zdrojové kolekci je proto celkový výsledek.</span><span class="sxs-lookup"><span data-stu-id="6d94c-126">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="6d94c-127">Naproti tomu `SelectMany()` vytváří jeden celkový výsledek, který obsahuje zřetězených podřízených kolekcí z každé zdrojové hodnotě.</span><span class="sxs-lookup"><span data-stu-id="6d94c-127">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="6d94c-128">Funkce transformace, který je předán jako argument pro `SelectMany()` musí vrátit vyčíslitelná pořadí hodnot pro každou hodnotu zdroje.</span><span class="sxs-lookup"><span data-stu-id="6d94c-128">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="6d94c-129">Tyto vyčíslitelná pořadí jsou pak zřetězených podle `SelectMany()` vytvoření jeden velký pořadí.</span><span class="sxs-lookup"><span data-stu-id="6d94c-129">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="6d94c-130">Následující dva obrázky ukazují koncepční rozdíl mezi tyto dvě metody akce.</span><span class="sxs-lookup"><span data-stu-id="6d94c-130">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="6d94c-131">V každém případě předpokládá, že funkce selektor (transformace) vybere pole květy z každé zdrojové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6d94c-131">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="6d94c-132">Tento obrázek znázorňuje způsob `Select()` vrátí kolekce, která má stejný počet elementů jako zdrojové kolekci.</span><span class="sxs-lookup"><span data-stu-id="6d94c-132">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 <span data-ttu-id="6d94c-133">![Koncepční obrázek akce vyberte &#40; &#41; ] (../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span><span class="sxs-lookup"><span data-stu-id="6d94c-133">![Conceptual illustration of the action of Select&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span></span>  
  
 <span data-ttu-id="6d94c-134">Tento obrázek znázorňuje způsob `SelectMany()` zřetězí zprostředkující pořadí polí do jednu hodnotu konečný výsledek, který obsahuje každou hodnotu z každé zprostředkující pole.</span><span class="sxs-lookup"><span data-stu-id="6d94c-134">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 <span data-ttu-id="6d94c-135">![Obrázek znázorňující akce označit více &#40; &#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "Označit více")</span><span class="sxs-lookup"><span data-stu-id="6d94c-135">![Graphic showing the action of SelectMany&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span></span>  
  
### <a name="code-example"></a><span data-ttu-id="6d94c-136">Příklad kódu</span><span class="sxs-lookup"><span data-stu-id="6d94c-136">Code Example</span></span>  
 <span data-ttu-id="6d94c-137">Následující příklad porovnává chování `Select()` a `SelectMany()`.</span><span class="sxs-lookup"><span data-stu-id="6d94c-137">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="6d94c-138">Kód vytvoří "bouquet" květy provedením první dvě položky z každé seznam názvů květina ve zdrojové kolekci.</span><span class="sxs-lookup"><span data-stu-id="6d94c-138">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="6d94c-139">V tomto příkladu "jedna hodnota", transformační funkce <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> používá, je sám kolekci hodnot.</span><span class="sxs-lookup"><span data-stu-id="6d94c-139">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="6d94c-140">To vyžaduje nadbytečné `foreach` smyčky, aby bylo možné vytvořit výčet každý řetězec v každé dílčí pořadí.</span><span class="sxs-lookup"><span data-stu-id="6d94c-140">This requires the extra `foreach` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6d94c-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d94c-141">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="6d94c-142">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="6d94c-142">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="6d94c-143">Select – klauzule</span><span class="sxs-lookup"><span data-stu-id="6d94c-143">select clause</span></span>](../../../../csharp/language-reference/keywords/select-clause.md)  
 [<span data-ttu-id="6d94c-144">Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="6d94c-144">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)  
 [<span data-ttu-id="6d94c-145">Postupy: rozdělení souboru na mnoho souborů pomocí skupin (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="6d94c-145">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
