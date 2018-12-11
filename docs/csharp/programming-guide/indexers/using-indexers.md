---
title: Použití indexerů - C# Průvodce programováním
ms.custom: seodec18
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: ad5c6f68f5eb2f62d7c6f389e374e1b2db5417c6
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241915"
---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="c6c46-102">Použití indexerů (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="c6c46-102">Using indexers (C# Programming Guide)</span></span>

<span data-ttu-id="c6c46-103">Indexery jsou syntaktické pohodlí, které vám umožní vytvořit [třídy](../../../csharp/language-reference/keywords/class.md), [struktura](../../../csharp/language-reference/keywords/struct.md), nebo [rozhraní](../../../csharp/language-reference/keywords/interface.md) , klientské aplikace můžou k stejně jako pole.</span><span class="sxs-lookup"><span data-stu-id="c6c46-103">Indexers are a syntactic convenience that enable you to create a [class](../../../csharp/language-reference/keywords/class.md), [struct](../../../csharp/language-reference/keywords/struct.md), or [interface](../../../csharp/language-reference/keywords/interface.md) that client applications can access just as an array.</span></span> <span data-ttu-id="c6c46-104">Indexery jsou nejčastěji implementovány v typech, jejichž primárním účelem je k zapouzdření vnitřní kolekce nebo pole.</span><span class="sxs-lookup"><span data-stu-id="c6c46-104">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="c6c46-105">Předpokládejme například, že máte třídu `TempRecord` , která představuje teploty v Farenheit zjištěná v různých časech 10 během období 24 hodin.</span><span class="sxs-lookup"><span data-stu-id="c6c46-105">For example, suppose you have a class `TempRecord` that represents the temperature in Farenheit as recorded at 10 different times during a 24 hour period.</span></span> <span data-ttu-id="c6c46-106">Třída obsahuje pole `temps` typu `float[]` k uložení teplotní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c6c46-106">The class contains an array `temps` of type `float[]` to store the temperature values.</span></span> <span data-ttu-id="c6c46-107">Implementací indexer v této třídě klienti mají přístup k teploty v `TempRecord` instance jako `float temp = tr[4]` místo jako `float temp = tr.temps[4]`.</span><span class="sxs-lookup"><span data-stu-id="c6c46-107">By implementing an indexer in this class, clients can access the temperatures in a `TempRecord` instance as `float temp = tr[4]` instead of as `float temp = tr.temps[4]`.</span></span> <span data-ttu-id="c6c46-108">Notace indexeru nejen zjednodušuje syntaxi pro klientské aplikace; také udržuje třídy a jejím účelem intuitivnější pro ostatní vývojáři mohli pochopit.</span><span class="sxs-lookup"><span data-stu-id="c6c46-108">The indexer notation not only simplifies the syntax for client applications; it also makes the class and its purpose more intuitive for other developers to understand.</span></span>  
  
<span data-ttu-id="c6c46-109">Chcete-li deklarovat indexer na třídě nebo struktuře, použijte [to](../../../csharp/language-reference/keywords/this.md) – klíčové slovo, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c6c46-109">To declare an indexer on a class or struct, use the [this](../../../csharp/language-reference/keywords/this.md) keyword, as the following example shows:</span></span>

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a><span data-ttu-id="c6c46-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6c46-110">Remarks</span></span>

<span data-ttu-id="c6c46-111">Typ indexeru a jeho parametry musí být přinejmenším stejně dostupná jako samotný indexeru.</span><span class="sxs-lookup"><span data-stu-id="c6c46-111">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="c6c46-112">Další informace o úrovní přístupu najdete v tématu [modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="c6c46-112">For more information about accessibility levels, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="c6c46-113">Další informace o tom, jak používat indexery s rozhraním najdete v tématu [rozhraní indexery](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="c6c46-113">For more information about how to use indexers with an interface, see [Interface Indexers](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md).</span></span>  
  
 <span data-ttu-id="c6c46-114">Podpis indexeru se skládá z počet a typy formálních parametrů.</span><span class="sxs-lookup"><span data-stu-id="c6c46-114">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="c6c46-115">Neobsahuje typ indexeru nebo názvy formálních parametrů.</span><span class="sxs-lookup"><span data-stu-id="c6c46-115">It doesn't include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="c6c46-116">Je-li deklarována více než jeden indexeru ve stejné třídě, musí mít různé podpisy.</span><span class="sxs-lookup"><span data-stu-id="c6c46-116">If you declare more than one indexer in the same class, they must have different signatures.</span></span>  
  
 <span data-ttu-id="c6c46-117">Není to indexerem hodnota klasifikováno jako proměnné. Proto nemůžete předat hodnotu indexer jako [ref](../../../csharp/language-reference/keywords/ref.md) nebo [si](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametru.</span><span class="sxs-lookup"><span data-stu-id="c6c46-117">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>  
  
 <span data-ttu-id="c6c46-118">Chcete-li poskytnout indexer s názvem, který můžete použít jiné jazyky, použijte <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, jak je vidět v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c6c46-118">To provide the indexer with a name that other languages can use, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, as the following example shows:</span></span>  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

<span data-ttu-id="c6c46-119">Indexer bude mít název `TheItem`.</span><span class="sxs-lookup"><span data-stu-id="c6c46-119">This indexer will have the name `TheItem`.</span></span> <span data-ttu-id="c6c46-120">Neposkytují atribut name s žádným `Item` výchozí název.</span><span class="sxs-lookup"><span data-stu-id="c6c46-120">Not providing the name attribute would make `Item` the default name.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="c6c46-121">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="c6c46-121">Example 1</span></span>  
  
<span data-ttu-id="c6c46-122">Následující příklad ukazuje, jak deklarovat soukromé pole `temps`a indexer.</span><span class="sxs-lookup"><span data-stu-id="c6c46-122">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="c6c46-123">Indexer umožňuje přímý přístup k instanci `tempRecord[i]`.</span><span class="sxs-lookup"><span data-stu-id="c6c46-123">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="c6c46-124">Je deklarovat pole jako alternativu k použití indexeru [veřejné](../../../csharp/language-reference/keywords/public.md) člena a přistupovat k jejím členům `tempRecord.temps[i]`, přímo.</span><span class="sxs-lookup"><span data-stu-id="c6c46-124">The alternative to using the indexer is to declare the array as a [public](../../../csharp/language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>  
  
 <span data-ttu-id="c6c46-125">Všimněte si, že při přístupu indexer vyhodnocování, například v `Console.Write` příkazu [získat](../../../csharp/language-reference/keywords/get.md) přístupového objektu je vyvolán.</span><span class="sxs-lookup"><span data-stu-id="c6c46-125">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../../csharp/language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="c6c46-126">Proto pokud žádná `get` přistupující objekt existuje, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="c6c46-126">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>  
  
[!code-csharp[csProgGuideIndexers#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_1.cs)]  
  
## <a name="indexing-using-other-values"></a><span data-ttu-id="c6c46-127">Indexování s využitím jiné hodnoty</span><span class="sxs-lookup"><span data-stu-id="c6c46-127">Indexing using other values</span></span>

<span data-ttu-id="c6c46-128">C# neomezuje typ indexu na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="c6c46-128">C# doesn't limit the index type to integer.</span></span> <span data-ttu-id="c6c46-129">Například může být vhodné použít řetězec s indexeru.</span><span class="sxs-lookup"><span data-stu-id="c6c46-129">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="c6c46-130">Pomocí hledání řetězce v kolekci a vrátí odpovídající hodnotu, může implementovat takové indexer.</span><span class="sxs-lookup"><span data-stu-id="c6c46-130">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="c6c46-131">Jako přístupové objekty mohou být přetíženy, řetězce a celá čísla verzí můžou existovat vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="c6c46-131">As accessors can be overloaded, the string and integer versions can co-exist.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="c6c46-132">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="c6c46-132">Example 2</span></span>  
  
<span data-ttu-id="c6c46-133">Následující příklad deklaruje třídu, která ukládá dny v týdnu.</span><span class="sxs-lookup"><span data-stu-id="c6c46-133">The following example declares a class that stores the days of the week.</span></span> <span data-ttu-id="c6c46-134">A `get` přistupující objekt přebírá řetězec názvu dne a vrátí odpovídající celé číslo.</span><span class="sxs-lookup"><span data-stu-id="c6c46-134">A `get` accessor takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="c6c46-135">Například vrátí hodnotu 0, "Neděle", "Pondělí" vrátí hodnotu 1 a tak dále.</span><span class="sxs-lookup"><span data-stu-id="c6c46-135">For example, "Sunday" returns 0, "Monday" returns 1, and so on.</span></span>  
  
[!code-csharp[csProgGuideIndexers#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_2.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="c6c46-136">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="c6c46-136">Robust programming</span></span>

 <span data-ttu-id="c6c46-137">Existují dva hlavní způsoby, ve kterých se může zlepšit zabezpečení a spolehlivost indexery:</span><span class="sxs-lookup"><span data-stu-id="c6c46-137">There are two main ways in which the security and reliability of indexers can be improved:</span></span>  
  
- <span data-ttu-id="c6c46-138">Nezapomeňte zahrnout nějaký typ strategie zpracování chyb pro zpracování riziko klientský kód předá hodnotu neplatný index.</span><span class="sxs-lookup"><span data-stu-id="c6c46-138">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="c6c46-139">V prvním příkladu výše v tomto tématu poskytuje třídu TempRecord vlastnost Length, která umožňuje klientské kód pro ověření vstupu před předáním to indexerem.</span><span class="sxs-lookup"><span data-stu-id="c6c46-139">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="c6c46-140">Můžete také vložit kód uvnitř samotného indexeru pro zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="c6c46-140">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="c6c46-141">Ujistěte se, k dokumentaci pro uživatele žádné výjimky, které můžete vyvolat uvnitř indexer přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="c6c46-141">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>  
  
- <span data-ttu-id="c6c46-142">Nastavte přístupnost [získat](../../../csharp/language-reference/keywords/get.md) a [nastavit](../../../csharp/language-reference/keywords/set.md) přistupující objekty být omezení je přijatelné.</span><span class="sxs-lookup"><span data-stu-id="c6c46-142">Set the accessibility of the [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="c6c46-143">To je důležité pro `set` přístupového objektu v konkrétní.</span><span class="sxs-lookup"><span data-stu-id="c6c46-143">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="c6c46-144">Další informace najdete v tématu [omezení přístupnosti přístupového objektu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="c6c46-144">For more information, see [Restricting Accessor Accessibility](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6c46-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6c46-145">See also</span></span>

- [<span data-ttu-id="c6c46-146">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c6c46-146">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c6c46-147">Indexery</span><span class="sxs-lookup"><span data-stu-id="c6c46-147">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
- [<span data-ttu-id="c6c46-148">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c6c46-148">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
