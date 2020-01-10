---
title: Použití indexerů – C# Průvodce programováním
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: bf290681395460bec10be45c4eaa1f165e453caf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75702893"
---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="a4a5c-102">Použití indexerů (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="a4a5c-102">Using indexers (C# Programming Guide)</span></span>

<span data-ttu-id="a4a5c-103">Indexery jsou syntaktické pohodlí, které umožňují vytvořit [třídu](../../language-reference/keywords/class.md), [strukturu](../../language-reference/keywords/struct.md)nebo [rozhraní](../../language-reference/keywords/interface.md) , které mohou klientské aplikace přistupovat pouze jako pole.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-103">Indexers are a syntactic convenience that enable you to create a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/keywords/struct.md), or [interface](../../language-reference/keywords/interface.md) that client applications can access just as an array.</span></span> <span data-ttu-id="a4a5c-104">Indexery se nejčastěji implementují v typech, jejichž primární účel je zapouzdření interní kolekce nebo pole.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-104">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="a4a5c-105">Předpokládejme například, že máte třídu `TempRecord`, která představuje teplotu ve stupních Fahrenheita zaznamenanou v 10 různých časech během 24 hodin.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-105">For example, suppose you have a class `TempRecord` that represents the temperature in Fahrenheit as recorded at 10 different times during a 24 hour period.</span></span> <span data-ttu-id="a4a5c-106">Třída obsahuje pole `temps` typu `float[]` pro uložení hodnot teploty.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-106">The class contains an array `temps` of type `float[]` to store the temperature values.</span></span> <span data-ttu-id="a4a5c-107">Implementací indexeru v této třídě mají klienti přístup k teplotám v instanci `TempRecord` jako `float temp = tr[4]` namísto `float temp = tr.temps[4]`.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-107">By implementing an indexer in this class, clients can access the temperatures in a `TempRecord` instance as `float temp = tr[4]` instead of as `float temp = tr.temps[4]`.</span></span> <span data-ttu-id="a4a5c-108">Zápis indexeru zjednodušuje syntaxi pro klientské aplikace. také umožňuje, aby byla třída a její účel intuitivnějšíější, aby bylo možné porozumět ostatním vývojářům.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-108">The indexer notation not only simplifies the syntax for client applications; it also makes the class and its purpose more intuitive for other developers to understand.</span></span>  
  
<span data-ttu-id="a4a5c-109">Chcete-li deklarovat indexer pro třídu nebo strukturu, použijte klíčové slovo [This](../../language-reference/keywords/this.md) , jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="a4a5c-109">To declare an indexer on a class or struct, use the [this](../../language-reference/keywords/this.md) keyword, as the following example shows:</span></span>

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a><span data-ttu-id="a4a5c-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4a5c-110">Remarks</span></span>

<span data-ttu-id="a4a5c-111">Typ indexeru a typ jeho parametrů musí být alespoň tak přístupný jako indexovací člen.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-111">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="a4a5c-112">Další informace o úrovních dostupnosti najdete v tématu [modifikátory přístupu](../../language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="a4a5c-112">For more information about accessibility levels, see [Access Modifiers](../../language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="a4a5c-113">Další informace o použití indexerů s rozhraním naleznete v tématu [indexery rozhraní](./indexers-in-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="a4a5c-113">For more information about how to use indexers with an interface, see [Interface Indexers](./indexers-in-interfaces.md).</span></span>  
  
 <span data-ttu-id="a4a5c-114">Signatura indexeru se skládá z počtu a typů jeho formálních parametrů.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-114">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="a4a5c-115">Nezahrnuje typ indexeru ani názvy formálních parametrů.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-115">It doesn't include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="a4a5c-116">Pokud deklarujete více než jednoho indexeru ve stejné třídě, musí mít jiné signatury.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-116">If you declare more than one indexer in the same class, they must have different signatures.</span></span>  
  
 <span data-ttu-id="a4a5c-117">Hodnota indexeru není klasifikována jako proměnná; Proto nemůžete předat hodnotu indexeru jako parametr [ref](../../language-reference/keywords/ref.md) nebo [out](../../language-reference/keywords/out-parameter-modifier.md) .</span><span class="sxs-lookup"><span data-stu-id="a4a5c-117">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>  
  
 <span data-ttu-id="a4a5c-118">Chcete-li poskytnout indexer s názvem, který mohou použít jiné jazyky, použijte <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="a4a5c-118">To provide the indexer with a name that other languages can use, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, as the following example shows:</span></span>  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

<span data-ttu-id="a4a5c-119">Tento indexer bude mít název `TheItem`.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-119">This indexer will have the name `TheItem`.</span></span> <span data-ttu-id="a4a5c-120">Neposkytnutí atributu name by `Item` výchozí název.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-120">Not providing the name attribute would make `Item` the default name.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="a4a5c-121">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="a4a5c-121">Example 1</span></span>  
  
<span data-ttu-id="a4a5c-122">Následující příklad ukazuje, jak deklarovat pole soukromého pole, `temps`a indexer.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-122">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="a4a5c-123">Indexer umožňuje přímý přístup k instanci `tempRecord[i]`.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-123">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="a4a5c-124">Alternativou k použití indexeru je deklarovat pole jako [veřejný](../../language-reference/keywords/public.md) člen a přistupovat ke svým členům, `tempRecord.temps[i]`přímo.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-124">The alternative to using the indexer is to declare the array as a [public](../../language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>  
  
 <span data-ttu-id="a4a5c-125">Všimněte si, že při vyhodnocení přístupu indexeru, například v příkazu `Console.Write`, je vyvolán přistupující objekt [Get](../../language-reference/keywords/get.md) .</span><span class="sxs-lookup"><span data-stu-id="a4a5c-125">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="a4a5c-126">Proto pokud neexistuje žádný přistupující objekt `get`, dojde k chybě při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-126">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#1)]  
  
## <a name="indexing-using-other-values"></a><span data-ttu-id="a4a5c-127">Indexování pomocí jiných hodnot</span><span class="sxs-lookup"><span data-stu-id="a4a5c-127">Indexing using other values</span></span>

<span data-ttu-id="a4a5c-128">C#neomezuje typ parametru indexeru na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-128">C# doesn't limit the indexer parameter type to integer.</span></span> <span data-ttu-id="a4a5c-129">Může být například užitečné použít řetězec s indexerem.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-129">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="a4a5c-130">Takový indexer může být implementován vyhledáním řetězce v kolekci a vrácením příslušné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-130">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="a4a5c-131">Protože přistupující objekty mohou být přetíženy, může řetězec a celočíselná verze existovat souběžně.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-131">As accessors can be overloaded, the string and integer versions can co-exist.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="a4a5c-132">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="a4a5c-132">Example 2</span></span>  
  
<span data-ttu-id="a4a5c-133">Následující příklad deklaruje třídu, která ukládá dny v týdnu.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-133">The following example declares a class that stores the days of the week.</span></span> <span data-ttu-id="a4a5c-134">Přistupující objekt `get` přebírá řetězec, název dne a vrátí odpovídající celé číslo.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-134">A `get` accessor takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="a4a5c-135">Například "neděle" vrátí 0, "pondělí" vrátí 1 a tak dále.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-135">For example, "Sunday" returns 0, "Monday" returns 1, and so on.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a4a5c-136">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="a4a5c-136">Robust programming</span></span>

 <span data-ttu-id="a4a5c-137">Existují dva hlavní způsoby, jak lze zlepšit zabezpečení a spolehlivost indexerů:</span><span class="sxs-lookup"><span data-stu-id="a4a5c-137">There are two main ways in which the security and reliability of indexers can be improved:</span></span>  
  
- <span data-ttu-id="a4a5c-138">Nezapomeňte začlenit nějaký typ strategie zpracování chyb pro zpracování pravděpodobnosti, že klientský kód projde neplatnou hodnotou indexu.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-138">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="a4a5c-139">V prvním příkladu výše v tomto tématu Třída TempRecord poskytuje vlastnost length, která umožňuje kódu klienta ověřit vstup před jeho předáním indexeru.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-139">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="a4a5c-140">Kód pro zpracování chyb můžete také vložit do samotného indexeru.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-140">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="a4a5c-141">Nezapomeňte uživatelům zdokumentovat všechny výjimky, které jste vyvolali uvnitř přístupového objektu indexeru.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-141">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>  
  
- <span data-ttu-id="a4a5c-142">Nastavte přístupnost přístupových objektů [Get](../../language-reference/keywords/get.md) a [set](../../language-reference/keywords/set.md) jako omezujících oprávnění, která jsou přiměřená.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-142">Set the accessibility of the [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="a4a5c-143">To je důležité zejména pro přistupující objekt `set`.</span><span class="sxs-lookup"><span data-stu-id="a4a5c-143">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="a4a5c-144">Další informace najdete v tématu [Omezení přístupnosti přístupového objektu](../classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="a4a5c-144">For more information, see [Restricting Accessor Accessibility](../classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4a5c-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4a5c-145">See also</span></span>

- [<span data-ttu-id="a4a5c-146">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a4a5c-146">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a4a5c-147">Indexery</span><span class="sxs-lookup"><span data-stu-id="a4a5c-147">Indexers</span></span>](./index.md)
- [<span data-ttu-id="a4a5c-148">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a4a5c-148">Properties</span></span>](../classes-and-structs/properties.md)
