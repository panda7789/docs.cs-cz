---
title: Struktury – C# Průvodce
description: Přečtěte si o typu struktury a způsobu jejich vytváření.
ms.date: 10/12/2016
ms.technology: csharp-fundamentals
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: 540742ea6a215e09f0cc31b218ac10fbf6192352
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503988"
---
# <a name="structs"></a><span data-ttu-id="e16be-103">Struktury</span><span class="sxs-lookup"><span data-stu-id="e16be-103">Structs</span></span>

<span data-ttu-id="e16be-104">*Struktura* je typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e16be-104">A *struct* is a value type.</span></span> <span data-ttu-id="e16be-105">Při vytvoření struktury obsahuje proměnná, ke které je přiřazena struktura, vlastní data struktury.</span><span class="sxs-lookup"><span data-stu-id="e16be-105">When a struct is created, the variable to which the struct is assigned holds the struct's actual data.</span></span> <span data-ttu-id="e16be-106">Když je struktura přiřazena nové proměnné, je zkopírována.</span><span class="sxs-lookup"><span data-stu-id="e16be-106">When the struct is assigned to a new variable, it is copied.</span></span> <span data-ttu-id="e16be-107">Nová proměnná a původní proměnná proto obsahují dvě samostatné kopie stejných dat.</span><span class="sxs-lookup"><span data-stu-id="e16be-107">The new variable and the original variable therefore contain two separate copies of the same data.</span></span> <span data-ttu-id="e16be-108">Změny provedené v jedné kopii nemají vliv na ostatní kopírování.</span><span class="sxs-lookup"><span data-stu-id="e16be-108">Changes made to one copy do not affect the other copy.</span></span>

<span data-ttu-id="e16be-109">Proměnné typu hodnoty přímo obsahují jejich hodnoty, což znamená, že je paměť přidělena vloženému v jakémkoli kontextu, kdy je proměnná deklarována.</span><span class="sxs-lookup"><span data-stu-id="e16be-109">Value type variables directly contain their values, which means that the memory is allocated inline in whatever context the variable is declared.</span></span> <span data-ttu-id="e16be-110">Neexistuje žádné samostatné přidělení haldy nebo režie uvolňování paměti pro proměnné typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e16be-110">There is no separate heap allocation or garbage collection overhead for value-type variables.</span></span>

<span data-ttu-id="e16be-111">Existují dvě kategorie typů hodnot: [struct](language-reference/keywords/struct.md) a [Enum](language-reference/builtin-types/enum.md).</span><span class="sxs-lookup"><span data-stu-id="e16be-111">There are two categories of value types: [struct](language-reference/keywords/struct.md) and [enum](language-reference/builtin-types/enum.md).</span></span>

<span data-ttu-id="e16be-112">Předdefinované číselné typy jsou struktury a mají vlastnosti a metody, ke kterým máte přístup:</span><span class="sxs-lookup"><span data-stu-id="e16be-112">The built-in numeric types are structs, and they have properties and methods that you can access:</span></span>

[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]

<span data-ttu-id="e16be-113">Ale deklarujete a přiřadíte jim hodnoty, jako kdyby byly jednoduché neagregované typy:</span><span class="sxs-lookup"><span data-stu-id="e16be-113">But you declare and assign values to them as if they were simple non-aggregate types:</span></span>

[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)]

<span data-ttu-id="e16be-114">Typy hodnot jsou *zapečetěné*, což znamená, že nemůžete odvodit typ z <xref:System.Int32>a nemůžete definovat strukturu, která by dědila z jakékoli uživatelsky definované třídy nebo struktury, protože struktura může dědit pouze z <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="e16be-114">Value types are *sealed*, which means, for example, that you cannot derive a type from <xref:System.Int32>, and you cannot define a struct to inherit from any user-defined class or struct because a struct can only inherit from <xref:System.ValueType>.</span></span> <span data-ttu-id="e16be-115">Struktura však může implementovat jedno nebo více rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e16be-115">However, a struct can implement one or more interfaces.</span></span> <span data-ttu-id="e16be-116">Typ struktury můžete přetypovat na typ rozhraní; To způsobí, že operace *zabalení* zabalí strukturu uvnitř objektu typu reference na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="e16be-116">You can cast a struct type to an interface type; this causes a *boxing* operation to wrap the struct inside a reference type object on the managed heap.</span></span> <span data-ttu-id="e16be-117">K operacím zabalení dojde, když předáte typ hodnoty metodě, která přijímá <xref:System.Object> jako vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="e16be-117">Boxing operations occur when you pass a value type to a method that takes an <xref:System.Object> as an input parameter.</span></span> <span data-ttu-id="e16be-118">Další informace naleznete v tématu [zabalení a rozbalení](./programming-guide/types/boxing-and-unboxing.md ).</span><span class="sxs-lookup"><span data-stu-id="e16be-118">For more information, see [Boxing and Unboxing](./programming-guide/types/boxing-and-unboxing.md ).</span></span>

<span data-ttu-id="e16be-119">Klíčové slovo [struct](./language-reference/keywords/struct.md) můžete použít k vytvoření vlastních typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="e16be-119">You use the [struct](./language-reference/keywords/struct.md) keyword to create your own custom value types.</span></span> <span data-ttu-id="e16be-120">Struktura se obvykle používá jako kontejner pro malou sadu souvisejících proměnných, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e16be-120">Typically, a struct is used as a container for a small set of related variables, as shown in the following example:</span></span>

[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]

<span data-ttu-id="e16be-121">Další informace o typech hodnot v .NET Framework naleznete v tématu [Common Type System](../standard/common-type-system.md).</span><span class="sxs-lookup"><span data-stu-id="e16be-121">For more information about value types in the .NET Framework, see [Common Type System](../standard/common-type-system.md).</span></span>

<span data-ttu-id="e16be-122">Struktury sdílejí většinu stejné syntaxe jako třídy, i když jsou struktury více omezené než třídy:</span><span class="sxs-lookup"><span data-stu-id="e16be-122">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>

- <span data-ttu-id="e16be-123">V rámci deklarace struktury nelze pole inicializovat, pokud nejsou deklarována jako `const` nebo `static`.</span><span class="sxs-lookup"><span data-stu-id="e16be-123">Within a struct declaration, fields cannot be initialized unless they are declared as `const` or `static`.</span></span>

- <span data-ttu-id="e16be-124">Struktura nemůže deklarovat konstruktor bez parametrů (konstruktor bez parametrů) nebo finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="e16be-124">A struct cannot declare a parameterless constructor (a constructor without parameters) or a finalizer.</span></span>

- <span data-ttu-id="e16be-125">Struktury se zkopírují při přiřazení.</span><span class="sxs-lookup"><span data-stu-id="e16be-125">Structs are copied on assignment.</span></span> <span data-ttu-id="e16be-126">Když je struktura přiřazena nové proměnné, zkopírují se všechna data a jakákoli změna nové kopie nemění data původní kopie.</span><span class="sxs-lookup"><span data-stu-id="e16be-126">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="e16be-127">To je důležité pamatovat při práci s kolekcemi typů hodnot, jako je slovník < String, myStruct >.</span><span class="sxs-lookup"><span data-stu-id="e16be-127">This is important to remember when working with collections of value types such as Dictionary<string, myStruct>.</span></span>

- <span data-ttu-id="e16be-128">Struktury jsou typy hodnot a třídy jsou odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="e16be-128">Structs are value types and classes are reference types.</span></span>

- <span data-ttu-id="e16be-129">Na rozdíl od tříd lze vytvořit instanci struktur bez použití operátoru `new`.</span><span class="sxs-lookup"><span data-stu-id="e16be-129">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>

- <span data-ttu-id="e16be-130">Struktury mohou deklarovat konstruktory, které mají parametry.</span><span class="sxs-lookup"><span data-stu-id="e16be-130">Structs can declare constructors that have parameters.</span></span>

- <span data-ttu-id="e16be-131">Struktura nemůže dědit z jiné struktury nebo třídy a nemůže být základem třídy.</span><span class="sxs-lookup"><span data-stu-id="e16be-131">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="e16be-132">Všechny struktury dědí přímo z <xref:System.ValueType>, které dědí z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="e16be-132">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>

- <span data-ttu-id="e16be-133">Struktura, jako je třída, může implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e16be-133">A struct, like a class, can implement interfaces.</span></span>

## <a name="nullable-value-types"></a><span data-ttu-id="e16be-134">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="e16be-134">Nullable value types</span></span>

<span data-ttu-id="e16be-135">Typy běžných hodnot nemohou mít hodnotu [null](language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="e16be-135">Ordinary value types cannot have a value of [null](language-reference/keywords/null.md).</span></span> <span data-ttu-id="e16be-136">Můžete však vytvořit typy hodnot s možnou hodnotou null, a to tak, že po typu napřipojíte `?`.</span><span class="sxs-lookup"><span data-stu-id="e16be-136">However, you can create nullable value types by affixing a `?` after the type.</span></span> <span data-ttu-id="e16be-137">Například `int?` je `int` typ, který může mít také hodnotu [null](./language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="e16be-137">For example, `int?` is an `int` type that can also have the value [null](./language-reference/keywords/null.md).</span></span> <span data-ttu-id="e16be-138">Typy s možnou hodnotou null jsou instancemi obecného typu struktury <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="e16be-138">Nullable value types are instances of the generic struct type <xref:System.Nullable%601>.</span></span> <span data-ttu-id="e16be-139">Typy hodnot s možnou hodnotou null jsou zvláště užitečné při předávání dat do a z databází, ve kterých mohou být číselné hodnoty null nebo nedefinovány.</span><span class="sxs-lookup"><span data-stu-id="e16be-139">Nullable value types are especially useful when you are passing data to and from databases in which numeric values might be null or undefined.</span></span> <span data-ttu-id="e16be-140">Další informace naleznete v tématu [typy hodnot s možnou hodnotou null](language-reference/builtin-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="e16be-140">For more information, see [Nullable value types](language-reference/builtin-types/nullable-value-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e16be-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="e16be-141">See also</span></span>

- [<span data-ttu-id="e16be-142">Třídy</span><span class="sxs-lookup"><span data-stu-id="e16be-142">Classes</span></span>](programming-guide/classes-and-structs/classes.md)
- [<span data-ttu-id="e16be-143">Základní typy</span><span class="sxs-lookup"><span data-stu-id="e16be-143">Basic Types</span></span>](basic-types.md)
