---
title: Použití indexerů – Průvodce programováním v C#
ms.date: 07/15/2020
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: e742e4dd5ea92ec3baf37c915e024e713022b7b6
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416232"
---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="c2456-102">Použití indexerů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="c2456-102">Using indexers (C# Programming Guide)</span></span>

<span data-ttu-id="c2456-103">Indexery jsou syntaktické pohodlí, které umožňují vytvořit [třídu](../../language-reference/keywords/class.md), [strukturu](../../language-reference/builtin-types/struct.md)nebo [rozhraní](../../language-reference/keywords/interface.md) , ke kterým můžou klientské aplikace přistupovat jako k poli.</span><span class="sxs-lookup"><span data-stu-id="c2456-103">Indexers are a syntactic convenience that enable you to create a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) that client applications can access as an array.</span></span> <span data-ttu-id="c2456-104">Kompilátor vygeneruje `Item` vlastnost (nebo případně pojmenovanou vlastnost, pokud existuje <xref:System.Runtime.CompilerServices.IndexerNameAttribute> ) a příslušné přístupové metody.</span><span class="sxs-lookup"><span data-stu-id="c2456-104">The compiler will generate an `Item` property (or an alternatively named property if <xref:System.Runtime.CompilerServices.IndexerNameAttribute> is present), and the appropriate accessor methods.</span></span> <span data-ttu-id="c2456-105">Indexery se nejčastěji implementují v typech, jejichž primární účel je zapouzdření interní kolekce nebo pole.</span><span class="sxs-lookup"><span data-stu-id="c2456-105">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="c2456-106">Předpokládejme například, že máte třídu `TempRecord` , která představuje teplotu ve stupních Fahrenheita zaznamenanou v 10 různých časech během 24 hodin.</span><span class="sxs-lookup"><span data-stu-id="c2456-106">For example, suppose you have a class `TempRecord` that represents the temperature in Fahrenheit as recorded at 10 different times during a 24-hour period.</span></span> <span data-ttu-id="c2456-107">Třída obsahuje `temps` pole typu `float[]` pro uložení hodnot teploty.</span><span class="sxs-lookup"><span data-stu-id="c2456-107">The class contains a `temps` array of type `float[]` to store the temperature values.</span></span> <span data-ttu-id="c2456-108">Implementací indexeru v této třídě mají klienti přístup k teplotám v instanci, `TempRecord` jako `float temp = tempRecord[4]` místo jako `float temp = tempRecord.temps[4]` .</span><span class="sxs-lookup"><span data-stu-id="c2456-108">By implementing an indexer in this class, clients can access the temperatures in a `TempRecord` instance as `float temp = tempRecord[4]` instead of as `float temp = tempRecord.temps[4]`.</span></span> <span data-ttu-id="c2456-109">Zápis indexeru zjednodušuje syntaxi pro klientské aplikace. poskytuje také třídu a její účel intuitivnější pro jiné vývojáře, aby porozuměli.</span><span class="sxs-lookup"><span data-stu-id="c2456-109">The indexer notation not only simplifies the syntax for client applications; it also makes the class, and its purpose more intuitive for other developers to understand.</span></span>

<span data-ttu-id="c2456-110">Chcete-li deklarovat indexer pro třídu nebo strukturu, použijte klíčové slovo [This](../../language-reference/keywords/this.md) , jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="c2456-110">To declare an indexer on a class or struct, use the [this](../../language-reference/keywords/this.md) keyword, as the following example shows:</span></span>

```csharp
// Indexer declaration
public int this[int index]
{
    // get and set accessors
}
```

> [!IMPORTANT]
> <span data-ttu-id="c2456-111">Deklarace indexeru automaticky vygeneruje vlastnost s názvem `Item` na objektu.</span><span class="sxs-lookup"><span data-stu-id="c2456-111">Declaring an indexer will automatically generate a property named `Item` on the object.</span></span> <span data-ttu-id="c2456-112">`Item`Vlastnost není přímo přístupná z [výrazu přístupu členů](../../language-reference/operators/member-access-operators.md#member-access-expression-)instance.</span><span class="sxs-lookup"><span data-stu-id="c2456-112">The `Item` property is not directly accessible from the instance [member access expression](../../language-reference/operators/member-access-operators.md#member-access-expression-).</span></span> <span data-ttu-id="c2456-113">Pokud navíc `Item` do objektu s indexerem přidáte vlastní vlastnost, zobrazí se [Chyba kompilátoru CS0102](../../misc/cs0102.md).</span><span class="sxs-lookup"><span data-stu-id="c2456-113">Additionally, if you add your own `Item` property to an object with an indexer, you'll get a [CS0102 compiler error](../../misc/cs0102.md).</span></span> <span data-ttu-id="c2456-114">Chcete-li se této chybě vyhnout, použijte příkaz <xref:System.Runtime.CompilerServices.IndexerNameAttribute> Přejmenovat indexer, jak je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="c2456-114">To avoid this error, use the <xref:System.Runtime.CompilerServices.IndexerNameAttribute> rename the indexer as detailed below.</span></span>

## <a name="remarks"></a><span data-ttu-id="c2456-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2456-115">Remarks</span></span>

<span data-ttu-id="c2456-116">Typ indexeru a typ jeho parametrů musí být alespoň tak přístupný jako indexovací člen.</span><span class="sxs-lookup"><span data-stu-id="c2456-116">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="c2456-117">Další informace o úrovních dostupnosti najdete v tématu [modifikátory přístupu](../../language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="c2456-117">For more information about accessibility levels, see [Access Modifiers](../../language-reference/keywords/access-modifiers.md).</span></span>

<span data-ttu-id="c2456-118">Další informace o použití indexerů s rozhraním naleznete v tématu [indexery rozhraní](./indexers-in-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="c2456-118">For more information about how to use indexers with an interface, see [Interface Indexers](./indexers-in-interfaces.md).</span></span>

<span data-ttu-id="c2456-119">Signatura indexeru se skládá z počtu a typů jeho formálních parametrů.</span><span class="sxs-lookup"><span data-stu-id="c2456-119">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="c2456-120">Nezahrnuje typ indexeru ani názvy formálních parametrů.</span><span class="sxs-lookup"><span data-stu-id="c2456-120">It doesn't include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="c2456-121">Pokud deklarujete více než jednoho indexeru ve stejné třídě, musí mít jiné signatury.</span><span class="sxs-lookup"><span data-stu-id="c2456-121">If you declare more than one indexer in the same class, they must have different signatures.</span></span>

<span data-ttu-id="c2456-122">Hodnota indexeru není klasifikována jako proměnná; Proto nemůžete předat hodnotu indexeru jako parametr [ref](../../language-reference/keywords/ref.md) nebo [out](../../language-reference/keywords/out-parameter-modifier.md) .</span><span class="sxs-lookup"><span data-stu-id="c2456-122">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>

<span data-ttu-id="c2456-123">Chcete-li poskytnout indexer s názvem, který mohou použít jiné jazyky, použijte <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType> , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c2456-123">To provide the indexer with a name that other languages can use, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, as the following example shows:</span></span>

```csharp
// Indexer declaration
[System.Runtime.CompilerServices.IndexerName("TheItem")]
public int this[int index]
{
    // get and set accessors
}
```

<span data-ttu-id="c2456-124">Tento indexer bude mít název `TheItem` , protože ho přepíše atribut názvu indexeru.</span><span class="sxs-lookup"><span data-stu-id="c2456-124">This indexer will have the name `TheItem`, as it is overridden by the indexer name attribute.</span></span> <span data-ttu-id="c2456-125">Ve výchozím nastavení je název indexeru `Item` .</span><span class="sxs-lookup"><span data-stu-id="c2456-125">By default, the indexer name is `Item`.</span></span>

## <a name="example-1"></a><span data-ttu-id="c2456-126">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="c2456-126">Example 1</span></span>

<span data-ttu-id="c2456-127">Následující příklad ukazuje, jak deklarovat pole soukromého pole, `temps` a indexer.</span><span class="sxs-lookup"><span data-stu-id="c2456-127">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="c2456-128">Indexer umožňuje přímý přístup k instanci `tempRecord[i]` .</span><span class="sxs-lookup"><span data-stu-id="c2456-128">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="c2456-129">Alternativou k použití indexeru je deklarovat pole jako [veřejný](../../language-reference/keywords/public.md) člen a přistupovat ke svým členům, `tempRecord.temps[i]` přímo.</span><span class="sxs-lookup"><span data-stu-id="c2456-129">The alternative to using the indexer is to declare the array as a [public](../../language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>

:::code language="csharp" source="snippets/Temperatures/TempRecord.cs":::

<span data-ttu-id="c2456-130">Všimněte si, že když je vyhodnocen přístup indexeru, například v `Console.Write` příkazu, je vyvolán přistupující objekt [Get](../../language-reference/keywords/get.md) .</span><span class="sxs-lookup"><span data-stu-id="c2456-130">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="c2456-131">Proto pokud neexistuje žádný `get` přistupující objekt, dojde k chybě při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="c2456-131">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>

:::code language="csharp" source="snippets/Temperatures/Program.cs":::

## <a name="indexing-using-other-values"></a><span data-ttu-id="c2456-132">Indexování pomocí jiných hodnot</span><span class="sxs-lookup"><span data-stu-id="c2456-132">Indexing using other values</span></span>

<span data-ttu-id="c2456-133">C# neomezuje typ parametru indexeru na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="c2456-133">C# doesn't limit the indexer parameter type to integer.</span></span> <span data-ttu-id="c2456-134">Může být například užitečné použít řetězec s indexerem.</span><span class="sxs-lookup"><span data-stu-id="c2456-134">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="c2456-135">Takový indexer může být implementován vyhledáním řetězce v kolekci a vrácením příslušné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c2456-135">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="c2456-136">V případě, že jsou přístupové objekty přetíženy, může řetězec a celočíselná verze existovat současně.</span><span class="sxs-lookup"><span data-stu-id="c2456-136">As accessors can be overloaded, the string and integer versions can coexist.</span></span>

## <a name="example-2"></a><span data-ttu-id="c2456-137">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="c2456-137">Example 2</span></span>

<span data-ttu-id="c2456-138">Následující příklad deklaruje třídu, která ukládá dny v týdnu.</span><span class="sxs-lookup"><span data-stu-id="c2456-138">The following example declares a class that stores the days of the week.</span></span> <span data-ttu-id="c2456-139">`get`Přistupující objekt přebírá řetězec, název dne a vrátí odpovídající celé číslo.</span><span class="sxs-lookup"><span data-stu-id="c2456-139">A `get` accessor takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="c2456-140">Například "neděle" vrátí 0, "pondělí" vrátí 1 a tak dále.</span><span class="sxs-lookup"><span data-stu-id="c2456-140">For example, "Sunday" returns 0, "Monday" returns 1, and so on.</span></span>

:::code language="csharp" source="snippets/StringIndexers/DayCollection.cs":::

### <a name="consuming-example-2"></a><span data-ttu-id="c2456-141">Spotřebovává se příklad 2</span><span class="sxs-lookup"><span data-stu-id="c2456-141">Consuming example 2</span></span>

:::code language="csharp" source="snippets/StringIndexers/Program.cs":::

## <a name="example-3"></a><span data-ttu-id="c2456-142">Příklad 3</span><span class="sxs-lookup"><span data-stu-id="c2456-142">Example 3</span></span>

<span data-ttu-id="c2456-143">Následující příklad deklaruje třídu, která ukládá dny v týdnu pomocí <xref:System.DayOfWeek?displayProperty=fullName> výčtu.</span><span class="sxs-lookup"><span data-stu-id="c2456-143">The following example declares a class that stores the days of the week using the <xref:System.DayOfWeek?displayProperty=fullName> enum.</span></span> <span data-ttu-id="c2456-144">`get`Přistupující objekt přebírá `DayOfWeek` hodnotu Day a vrátí odpovídající celé číslo.</span><span class="sxs-lookup"><span data-stu-id="c2456-144">A `get` accessor takes a `DayOfWeek`, the value of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="c2456-145">Například vrátí hodnotu `DayOfWeek.Sunday` 0, `DayOfWeek.Monday` vrátí 1 a tak dále.</span><span class="sxs-lookup"><span data-stu-id="c2456-145">For example, `DayOfWeek.Sunday` returns 0, `DayOfWeek.Monday` returns 1, and so on.</span></span>

:::code language="csharp" source="snippets/DayOfWeekIndexers/DayOfWeekCollection.cs":::

### <a name="consuming-example-3"></a><span data-ttu-id="c2456-146">Spotřebovává se příklad 3</span><span class="sxs-lookup"><span data-stu-id="c2456-146">Consuming example 3</span></span>

:::code language="csharp" source="snippets/DayOfWeekIndexers/Program.cs":::

## <a name="robust-programming"></a><span data-ttu-id="c2456-147">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="c2456-147">Robust programming</span></span>

<span data-ttu-id="c2456-148">Existují dva hlavní způsoby, jak lze zlepšit zabezpečení a spolehlivost indexerů:</span><span class="sxs-lookup"><span data-stu-id="c2456-148">There are two main ways in which the security and reliability of indexers can be improved:</span></span>

- <span data-ttu-id="c2456-149">Nezapomeňte začlenit nějaký typ strategie zpracování chyb pro zpracování pravděpodobnosti, že klientský kód projde neplatnou hodnotou indexu.</span><span class="sxs-lookup"><span data-stu-id="c2456-149">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="c2456-150">V prvním příkladu výše v tomto tématu Třída TempRecord poskytuje vlastnost length, která umožňuje kódu klienta ověřit vstup před jeho předáním indexeru.</span><span class="sxs-lookup"><span data-stu-id="c2456-150">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="c2456-151">Kód pro zpracování chyb můžete také vložit do samotného indexeru.</span><span class="sxs-lookup"><span data-stu-id="c2456-151">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="c2456-152">Nezapomeňte uživatelům zdokumentovat všechny výjimky, které jste vyvolali uvnitř přístupového objektu indexeru.</span><span class="sxs-lookup"><span data-stu-id="c2456-152">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>

- <span data-ttu-id="c2456-153">Nastavte přístupnost přístupových objektů [Get](../../language-reference/keywords/get.md) a [set](../../language-reference/keywords/set.md) jako omezujících oprávnění, která jsou přiměřená.</span><span class="sxs-lookup"><span data-stu-id="c2456-153">Set the accessibility of the [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="c2456-154">To je důležité pro `set` přistupující objekt, zejména.</span><span class="sxs-lookup"><span data-stu-id="c2456-154">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="c2456-155">Další informace najdete v tématu [Omezení přístupnosti přístupového objektu](../classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="c2456-155">For more information, see [Restricting Accessor Accessibility](../classes-and-structs/restricting-accessor-accessibility.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c2456-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2456-156">See also</span></span>

- [<span data-ttu-id="c2456-157">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="c2456-157">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c2456-158">Indexery</span><span class="sxs-lookup"><span data-stu-id="c2456-158">Indexers</span></span>](./index.md)
- [<span data-ttu-id="c2456-159">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c2456-159">Properties</span></span>](../classes-and-structs/properties.md)
