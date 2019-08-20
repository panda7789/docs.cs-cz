---
title: Operace projekce (C#)
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: 4b34f3e578e746d75bdad7baaf731d743830713c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591558"
---
# <a name="projection-operations-c"></a><span data-ttu-id="d4144-102">Operace projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="d4144-102">Projection Operations (C#)</span></span>
<span data-ttu-id="d4144-103">Projekce odkazuje na operaci transformace objektu do nového formuláře, který se často skládá pouze z těchto vlastností, které budou následně použity.</span><span class="sxs-lookup"><span data-stu-id="d4144-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="d4144-104">Pomocí projekce můžete vytvořit nový typ, který je sestaven z každého objektu.</span><span class="sxs-lookup"><span data-stu-id="d4144-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="d4144-105">Můžete promítnout vlastnost a na ní provést matematickou funkci.</span><span class="sxs-lookup"><span data-stu-id="d4144-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="d4144-106">Původní objekt můžete také promítnout beze změny.</span><span class="sxs-lookup"><span data-stu-id="d4144-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="d4144-107">Standardní metody operátoru dotazu, které provádějí projekci, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="d4144-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d4144-108">Metody</span><span class="sxs-lookup"><span data-stu-id="d4144-108">Methods</span></span>  
  
|<span data-ttu-id="d4144-109">Název metody</span><span class="sxs-lookup"><span data-stu-id="d4144-109">Method Name</span></span>|<span data-ttu-id="d4144-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d4144-110">Description</span></span>|<span data-ttu-id="d4144-111">C#Syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="d4144-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="d4144-112">Další informace</span><span class="sxs-lookup"><span data-stu-id="d4144-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="d4144-113">Vyberte</span><span class="sxs-lookup"><span data-stu-id="d4144-113">Select</span></span>|<span data-ttu-id="d4144-114">Projekty hodnoty, které jsou založeny na transformační funkci.</span><span class="sxs-lookup"><span data-stu-id="d4144-114">Projects values that are based on a transform function.</span></span>|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d4144-115">Operátor SelectMany</span><span class="sxs-lookup"><span data-stu-id="d4144-115">SelectMany</span></span>|<span data-ttu-id="d4144-116">Projektuje sekvence hodnot, které jsou založeny na transformační funkci a poté jsou shrnuty do jedné sekvence.</span><span class="sxs-lookup"><span data-stu-id="d4144-116">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="d4144-117">Použít více `from` klauzulí</span><span class="sxs-lookup"><span data-stu-id="d4144-117">Use multiple `from` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="d4144-118">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="d4144-118">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="d4144-119">Vyberte</span><span class="sxs-lookup"><span data-stu-id="d4144-119">Select</span></span>  
 <span data-ttu-id="d4144-120">V následujícím příkladu je použita `select` klauzule pro projekt prvního písmene z každého řetězce v seznamu řetězců.</span><span class="sxs-lookup"><span data-stu-id="d4144-120">The following example uses the `select` clause to project the first letter from each string in a list of strings.</span></span>  
  
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
  
### <a name="selectmany"></a><span data-ttu-id="d4144-121">Operátor SelectMany</span><span class="sxs-lookup"><span data-stu-id="d4144-121">SelectMany</span></span>  
 <span data-ttu-id="d4144-122">Následující příklad používá více `from` klauzulí pro každé slovo z každého řetězce v seznamu řetězců.</span><span class="sxs-lookup"><span data-stu-id="d4144-122">The following example uses multiple `from` clauses  to project each word from each string in a list of strings.</span></span>  
  
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
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="d4144-123">Vybrat versus operátor SelectMany</span><span class="sxs-lookup"><span data-stu-id="d4144-123">Select versus SelectMany</span></span>  
 <span data-ttu-id="d4144-124">Jak obojí `Select()` , `SelectMany()` tak je vytvořit výslednou hodnotu (nebo hodnoty) ze zdrojových hodnot.</span><span class="sxs-lookup"><span data-stu-id="d4144-124">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="d4144-125">`Select()`vytvoří jednu výslednou hodnotu pro každou zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d4144-125">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="d4144-126">Celkový výsledek je tedy kolekce, která má stejný počet prvků jako zdrojová kolekce.</span><span class="sxs-lookup"><span data-stu-id="d4144-126">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="d4144-127">Naproti tomu `SelectMany()` vytvoří jeden celkový výsledek, který obsahuje zřetězené dílčí kolekce z každé zdrojové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d4144-127">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="d4144-128">Funkce transformace, která je předána jako argument pro `SelectMany()` , musí vracet vyčíslitelné sekvence hodnot pro každou zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d4144-128">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="d4144-129">Tyto vyčíslitelné sekvence jsou poté zřetězeny nástrojem `SelectMany()` , aby vytvořily jednu velkou sekvenci.</span><span class="sxs-lookup"><span data-stu-id="d4144-129">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="d4144-130">Následující dva ilustrace znázorňují koncepční rozdíl mezi akcemi těchto dvou metod.</span><span class="sxs-lookup"><span data-stu-id="d4144-130">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="d4144-131">V každém případě Předpokládejme, že funkce Selector (transformace) vybere pole květů z každé zdrojové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d4144-131">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="d4144-132">Tento obrázek znázorňuje, jak `Select()` vrátí kolekci, která má stejný počet prvků jako zdrojová kolekce.</span><span class="sxs-lookup"><span data-stu-id="d4144-132">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 ![Obrázek, který zobrazuje akci výběru&#40;&#41;](./media/projection-operations/select-action-graphic.png)  
  
 <span data-ttu-id="d4144-134">Tento obrázek znázorňuje, jak `SelectMany()` zřetězí mezilehlé pořadí polí do jedné konečné výsledné hodnoty, která obsahuje všechny hodnoty z každého mezilehlého pole.</span><span class="sxs-lookup"><span data-stu-id="d4144-134">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 ![Obrázek znázorňující akci operátor SelectMany&#40;&#41;](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a><span data-ttu-id="d4144-136">Příklad kódu</span><span class="sxs-lookup"><span data-stu-id="d4144-136">Code Example</span></span>  
 <span data-ttu-id="d4144-137">Následující příklad porovnává chování `Select()` a. `SelectMany()`</span><span class="sxs-lookup"><span data-stu-id="d4144-137">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="d4144-138">Kód vytvoří "kytici" květů z každého seznamu názvů květin ve zdrojové kolekci.</span><span class="sxs-lookup"><span data-stu-id="d4144-138">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="d4144-139">V tomto příkladu "jediná hodnota", kterou funkce <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> transformace používá, je sám kolekcí hodnot.</span><span class="sxs-lookup"><span data-stu-id="d4144-139">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="d4144-140">K tomu je zapotřebí `foreach` nadbytečné smyčky pro zobrazení výčtu každého řetězce v každé dílčí sekvenci.</span><span class="sxs-lookup"><span data-stu-id="d4144-140">This requires the extra `foreach` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d4144-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4144-141">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="d4144-142">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="d4144-142">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="d4144-143">select – klauzule</span><span class="sxs-lookup"><span data-stu-id="d4144-143">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
- [<span data-ttu-id="d4144-144">Postupy: Naplnit kolekce objektů z více zdrojů (LINQ)C#()</span><span class="sxs-lookup"><span data-stu-id="d4144-144">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="d4144-145">Postupy: Rozdělení souboru na více souborů pomocí skupin (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d4144-145">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
