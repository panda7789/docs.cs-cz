---
title: Použití indexerů – programovací příručka jazyka C#
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 17162a0dc959a85c03a5cb5757e2b91fe10b0ab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628160"
---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="841d2-102">Použití indexerů (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="841d2-102">Using indexers (C# Programming Guide)</span></span>

<span data-ttu-id="841d2-103">Indexery jsou syntaktické pohodlí, které umožňují vytvořit [třídu](../../language-reference/keywords/class.md), [strukturu](../../language-reference/builtin-types/struct.md)nebo [rozhraní,](../../language-reference/keywords/interface.md) ke kterým mohou klientské aplikace přistupovat stejně jako pole.</span><span class="sxs-lookup"><span data-stu-id="841d2-103">Indexers are a syntactic convenience that enable you to create a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) that client applications can access just as an array.</span></span> <span data-ttu-id="841d2-104">Indexery jsou nejčastěji implementovány v typech, jejichž primárním účelem je zapouzdřit vnitřní kolekci nebo pole.</span><span class="sxs-lookup"><span data-stu-id="841d2-104">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="841d2-105">Předpokládejme například, že `TempRecord` máte třídu, která představuje teplotu ve Fahrenheitu, jak je zaznamenána v 10 různých časech během období 24 hodin.</span><span class="sxs-lookup"><span data-stu-id="841d2-105">For example, suppose you have a class `TempRecord` that represents the temperature in Fahrenheit as recorded at 10 different times during a 24 hour period.</span></span> <span data-ttu-id="841d2-106">Třída obsahuje pole `temps` typu `float[]` pro uložení hodnot teploty.</span><span class="sxs-lookup"><span data-stu-id="841d2-106">The class contains an array `temps` of type `float[]` to store the temperature values.</span></span> <span data-ttu-id="841d2-107">Implementací indexeru v této třídě mohou klienti `TempRecord` přistupovat k teplotám v instanci jako `float temp = tr[4]` namísto jako `float temp = tr.temps[4]`.</span><span class="sxs-lookup"><span data-stu-id="841d2-107">By implementing an indexer in this class, clients can access the temperatures in a `TempRecord` instance as `float temp = tr[4]` instead of as `float temp = tr.temps[4]`.</span></span> <span data-ttu-id="841d2-108">Zápis indexeru nejen zjednodušuje syntaxi pro klientské aplikace; to také dělá třídu a její účel intuitivnější pro ostatní vývojáře pochopit.</span><span class="sxs-lookup"><span data-stu-id="841d2-108">The indexer notation not only simplifies the syntax for client applications; it also makes the class and its purpose more intuitive for other developers to understand.</span></span>  
  
<span data-ttu-id="841d2-109">Chcete-li deklarovat indexer ve třídě nebo struktuře, použijte klíčové slovo [This,](../../language-reference/keywords/this.md) jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="841d2-109">To declare an indexer on a class or struct, use the [this](../../language-reference/keywords/this.md) keyword, as the following example shows:</span></span>

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a><span data-ttu-id="841d2-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="841d2-110">Remarks</span></span>

<span data-ttu-id="841d2-111">Typ indexeru a typ jeho parametrů musí být alespoň stejně přístupný jako samotný indexer.</span><span class="sxs-lookup"><span data-stu-id="841d2-111">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="841d2-112">Další informace o úrovních usnadnění naleznete [v tématu Access Modifiers](../../language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="841d2-112">For more information about accessibility levels, see [Access Modifiers](../../language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="841d2-113">Další informace o použití indexerů s rozhraním naleznete v [tématu Interface Indexers](./indexers-in-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="841d2-113">For more information about how to use indexers with an interface, see [Interface Indexers](./indexers-in-interfaces.md).</span></span>  
  
 <span data-ttu-id="841d2-114">Podpis indexeru se skládá z počtu a typů jeho formálních parametrů.</span><span class="sxs-lookup"><span data-stu-id="841d2-114">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="841d2-115">Neobsahuje typ indexeru nebo názvy formálních parametrů.</span><span class="sxs-lookup"><span data-stu-id="841d2-115">It doesn't include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="841d2-116">Pokud deklarujete více než jeden indexer ve stejné třídě, musí mít různé podpisy.</span><span class="sxs-lookup"><span data-stu-id="841d2-116">If you declare more than one indexer in the same class, they must have different signatures.</span></span>  
  
 <span data-ttu-id="841d2-117">Hodnota indexeru není klasifikována jako proměnná. proto nelze předat hodnotu indexeru jako [ref](../../language-reference/keywords/ref.md) nebo [out](../../language-reference/keywords/out-parameter-modifier.md) parametr.</span><span class="sxs-lookup"><span data-stu-id="841d2-117">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>  
  
 <span data-ttu-id="841d2-118">Chcete-li indexeru poskytnout název, který <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>mohou používat jiné jazyky, použijte , jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="841d2-118">To provide the indexer with a name that other languages can use, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, as the following example shows:</span></span>  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

<span data-ttu-id="841d2-119">Tento indexer bude `TheItem`mít název .</span><span class="sxs-lookup"><span data-stu-id="841d2-119">This indexer will have the name `TheItem`.</span></span> <span data-ttu-id="841d2-120">Nezadání atributu name `Item` by vytvořilo výchozí název.</span><span class="sxs-lookup"><span data-stu-id="841d2-120">Not providing the name attribute would make `Item` the default name.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="841d2-121">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="841d2-121">Example 1</span></span>  
  
<span data-ttu-id="841d2-122">Následující příklad ukazuje, `temps`jak deklarovat soukromé pole pole a indexer.</span><span class="sxs-lookup"><span data-stu-id="841d2-122">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="841d2-123">Indexer umožňuje přímý přístup `tempRecord[i]`k instanci .</span><span class="sxs-lookup"><span data-stu-id="841d2-123">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="841d2-124">Alternativou k použití indexeru je deklarovat pole jako `tempRecord.temps[i]` [veřejný](../../language-reference/keywords/public.md) člen a přístup k jeho členy, , přímo.</span><span class="sxs-lookup"><span data-stu-id="841d2-124">The alternative to using the indexer is to declare the array as a [public](../../language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>  
  
 <span data-ttu-id="841d2-125">Všimněte si, že při vyhodnocování `Console.Write` přístupu indexeru, například v příkazu, je vyvolán přístupový objekt [get.](../../language-reference/keywords/get.md)</span><span class="sxs-lookup"><span data-stu-id="841d2-125">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="841d2-126">Proto pokud `get` neexistuje žádný přistupující objektů, dojde k chybě v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="841d2-126">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#1)]  
  
## <a name="indexing-using-other-values"></a><span data-ttu-id="841d2-127">Indexování pomocí jiných hodnot</span><span class="sxs-lookup"><span data-stu-id="841d2-127">Indexing using other values</span></span>

<span data-ttu-id="841d2-128">C# neomezuje typ parametru indexeru na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="841d2-128">C# doesn't limit the indexer parameter type to integer.</span></span> <span data-ttu-id="841d2-129">Například může být užitečné použít řetězec s indexerem.</span><span class="sxs-lookup"><span data-stu-id="841d2-129">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="841d2-130">Takový indexer může být implementována hledáním řetězce v kolekci a vrácením příslušné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="841d2-130">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="841d2-131">Jako přístupové položky mohou být přetíženy, řetězec a celočíselné verze mohou existovat společně.</span><span class="sxs-lookup"><span data-stu-id="841d2-131">As accessors can be overloaded, the string and integer versions can co-exist.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="841d2-132">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="841d2-132">Example 2</span></span>  
  
<span data-ttu-id="841d2-133">Následující příklad deklaruje třídu, která ukládá dny v týdnu.</span><span class="sxs-lookup"><span data-stu-id="841d2-133">The following example declares a class that stores the days of the week.</span></span> <span data-ttu-id="841d2-134">Přistupující `get` pole trvá řetězec, název dne a vrátí odpovídající celé číslo.</span><span class="sxs-lookup"><span data-stu-id="841d2-134">A `get` accessor takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="841d2-135">Například "Neděle" vrátí 0, "Pondělí" vrátí 1 a tak dále.</span><span class="sxs-lookup"><span data-stu-id="841d2-135">For example, "Sunday" returns 0, "Monday" returns 1, and so on.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="841d2-136">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="841d2-136">Robust programming</span></span>

 <span data-ttu-id="841d2-137">Existují dva hlavní způsoby, jak zlepšit zabezpečení a spolehlivost indexerů:</span><span class="sxs-lookup"><span data-stu-id="841d2-137">There are two main ways in which the security and reliability of indexers can be improved:</span></span>  
  
- <span data-ttu-id="841d2-138">Nezapomeňte začlenit nějaký typ strategie zpracování chyb pro zpracování pravděpodobnosti předání kódu klienta v neplatné hodnotě indexu.</span><span class="sxs-lookup"><span data-stu-id="841d2-138">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="841d2-139">V prvním příkladu dříve v tomto tématu TempRecord třída poskytuje Length vlastnost, která umožňuje kód klienta ověřit vstup před předáním do indexeru.</span><span class="sxs-lookup"><span data-stu-id="841d2-139">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="841d2-140">Můžete také umístit kód zpracování chyb uvnitř samotného indexeru.</span><span class="sxs-lookup"><span data-stu-id="841d2-140">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="841d2-141">Ujistěte se, že dokument pro uživatele všechny výjimky, které vyvoláte uvnitř přístupu indexeru.</span><span class="sxs-lookup"><span data-stu-id="841d2-141">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>  
  
- <span data-ttu-id="841d2-142">Nastavte přístupnost [přístupových](../../language-reference/keywords/get.md) a [nastavených](../../language-reference/keywords/set.md) přístupových částí, které mají být stejně omezující jako přiměřené.</span><span class="sxs-lookup"><span data-stu-id="841d2-142">Set the accessibility of the [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="841d2-143">To je důležité `set` zejména pro přistupujícího.</span><span class="sxs-lookup"><span data-stu-id="841d2-143">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="841d2-144">Další informace naleznete v [tématu Omezení přístupnosti přístupu k přístupu](../classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="841d2-144">For more information, see [Restricting Accessor Accessibility](../classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="841d2-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="841d2-145">See also</span></span>

- [<span data-ttu-id="841d2-146">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="841d2-146">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="841d2-147">Indexery</span><span class="sxs-lookup"><span data-stu-id="841d2-147">Indexers</span></span>](./index.md)
- [<span data-ttu-id="841d2-148">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="841d2-148">Properties</span></span>](../classes-and-structs/properties.md)
