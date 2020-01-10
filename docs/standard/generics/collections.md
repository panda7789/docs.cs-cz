---
title: Obecné kolekce na platformě .NET
ms.date: 02/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET], collections
- generic collections [.NET]
- generic types [.NET]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
ms.openlocfilehash: dce0e38b0198396ec0dbc3ced7f2f59c2b112b56
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708407"
---
# <a name="generic-collections-in-net"></a><span data-ttu-id="439af-102">Obecné kolekce v .NET</span><span class="sxs-lookup"><span data-stu-id="439af-102">Generic collections in .NET</span></span>

 <span data-ttu-id="439af-103">Knihovna tříd .NET poskytuje řadu obecných tříd kolekcí v oborech názvů <xref:System.Collections.Generic> a <xref:System.Collections.ObjectModel>.</span><span class="sxs-lookup"><span data-stu-id="439af-103">The .NET class library provides a number of generic collection classes in the <xref:System.Collections.Generic> and <xref:System.Collections.ObjectModel> namespaces.</span></span> <span data-ttu-id="439af-104">Podrobnější informace o těchto třídách naleznete v tématu [běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md).</span><span class="sxs-lookup"><span data-stu-id="439af-104">For more detailed information about these classes, see [Commonly Used Collection Types](../../../docs/standard/collections/commonly-used-collection-types.md).</span></span>  
  
## <a name="systemcollectionsgeneric"></a><span data-ttu-id="439af-105">System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="439af-105">System.Collections.Generic</span></span>

 <span data-ttu-id="439af-106">Mnohé z obecných typů kolekcí jsou přímé analogické pro neobecné typy.</span><span class="sxs-lookup"><span data-stu-id="439af-106">Many of the generic collection types are direct analogs of nongeneric types.</span></span> <span data-ttu-id="439af-107"><xref:System.Collections.Generic.Dictionary%602> je obecná verze <xref:System.Collections.Hashtable>; místo <xref:System.Collections.DictionaryEntry>používá obecnou strukturu <xref:System.Collections.Generic.KeyValuePair%602> pro výčet.</span><span class="sxs-lookup"><span data-stu-id="439af-107"><xref:System.Collections.Generic.Dictionary%602> is a generic version of <xref:System.Collections.Hashtable>; it uses the generic structure <xref:System.Collections.Generic.KeyValuePair%602> for enumeration instead of <xref:System.Collections.DictionaryEntry>.</span></span>  
  
 <span data-ttu-id="439af-108"><xref:System.Collections.Generic.List%601> je obecná verze <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="439af-108"><xref:System.Collections.Generic.List%601> is a generic version of <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="439af-109">Existují obecné třídy <xref:System.Collections.Generic.Queue%601> a <xref:System.Collections.Generic.Stack%601>, které odpovídají neobecným verzím.</span><span class="sxs-lookup"><span data-stu-id="439af-109">There are generic <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601> classes that correspond to the nongeneric versions.</span></span>  
  
 <span data-ttu-id="439af-110">Existují obecné a neobecné verze <xref:System.Collections.Generic.SortedList%602>.</span><span class="sxs-lookup"><span data-stu-id="439af-110">There are generic and nongeneric versions of <xref:System.Collections.Generic.SortedList%602>.</span></span> <span data-ttu-id="439af-111">Obě verze jsou hybridy slovníku a seznamu.</span><span class="sxs-lookup"><span data-stu-id="439af-111">Both versions are hybrids of a dictionary and a list.</span></span> <span data-ttu-id="439af-112"><xref:System.Collections.Generic.SortedDictionary%602> obecná třída je čistě slovník a nemá žádné neobecné protějšky.</span><span class="sxs-lookup"><span data-stu-id="439af-112">The <xref:System.Collections.Generic.SortedDictionary%602> generic class is a pure dictionary and has no nongeneric counterpart.</span></span>  
  
 <span data-ttu-id="439af-113"><xref:System.Collections.Generic.LinkedList%601> obecná třída je skutečný propojený seznam.</span><span class="sxs-lookup"><span data-stu-id="439af-113">The <xref:System.Collections.Generic.LinkedList%601> generic class is a true linked list.</span></span> <span data-ttu-id="439af-114">Nemá žádný obecný protějšek.</span><span class="sxs-lookup"><span data-stu-id="439af-114">It has no nongeneric counterpart.</span></span>  
  
## <a name="systemcollectionsobjectmodel"></a><span data-ttu-id="439af-115">System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="439af-115">System.Collections.ObjectModel</span></span>

 <span data-ttu-id="439af-116">Obecná třída <xref:System.Collections.ObjectModel.Collection%601> poskytuje základní třídu pro odvození vlastních typů obecných kolekcí.</span><span class="sxs-lookup"><span data-stu-id="439af-116">The <xref:System.Collections.ObjectModel.Collection%601> generic class provides a base class for deriving your own generic collection types.</span></span> <span data-ttu-id="439af-117">Třída <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> poskytuje snadný způsob, jak vytvořit kolekci jen pro čtení z libovolného typu, který implementuje <xref:System.Collections.Generic.IList%601> obecné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="439af-117">The <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class provides an easy way to produce a read-only collection from any type that implements the <xref:System.Collections.Generic.IList%601> generic interface.</span></span> <span data-ttu-id="439af-118"><xref:System.Collections.ObjectModel.KeyedCollection%602> obecná třída poskytuje způsob, jak ukládat objekty, které obsahují vlastní klíče.</span><span class="sxs-lookup"><span data-stu-id="439af-118">The <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class provides a way to store objects that contain their own keys.</span></span>  
  
## <a name="other-generic-types"></a><span data-ttu-id="439af-119">Jiné obecné typy</span><span class="sxs-lookup"><span data-stu-id="439af-119">Other generic types</span></span>

 <span data-ttu-id="439af-120"><xref:System.Nullable%601> Obecná struktura umožňuje používat typy hodnot, jako by mohly být přiřazeny `null`.</span><span class="sxs-lookup"><span data-stu-id="439af-120">The <xref:System.Nullable%601> generic structure allows you to use value types as if they could be assigned `null`.</span></span> <span data-ttu-id="439af-121">To může být užitečné při práci s databázovými dotazy, kde mohou chybět pole, která obsahují hodnotové typy.</span><span class="sxs-lookup"><span data-stu-id="439af-121">This can be useful when working with database queries, where fields that contain value types can be missing.</span></span> <span data-ttu-id="439af-122">Parametr obecného typu může být libovolný typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="439af-122">The generic type parameter can be any value type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="439af-123">V C# a Visual Basic není nutné <xref:System.Nullable%601> explicitně používat, protože jazyk obsahuje syntaxi pro typy s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="439af-123">In C# and Visual Basic, it is not necessary to use <xref:System.Nullable%601> explicitly because the language has syntax for nullable types.</span></span> <span data-ttu-id="439af-124">Viz typy [hodnot s možnou hodnotouC# null (referenční)](../../csharp/language-reference/builtin-types/nullable-value-types.md) a typy s [možnou hodnotou null (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="439af-124">See [Nullable value types (C# reference)](../../csharp/language-reference/builtin-types/nullable-value-types.md) and [Nullable value types (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span></span>
  
 <span data-ttu-id="439af-125"><xref:System.ArraySegment%601> Obecná struktura poskytuje způsob, jak omezit rozsah prvků v rámci jednorozměrného pole libovolného typu, který je založený na nule.</span><span class="sxs-lookup"><span data-stu-id="439af-125">The <xref:System.ArraySegment%601> generic structure provides a way to delimit a range of elements within a one-dimensional, zero-based array of any type.</span></span> <span data-ttu-id="439af-126">Parametr obecného typu je typ prvků pole.</span><span class="sxs-lookup"><span data-stu-id="439af-126">The generic type parameter is the type of the array's elements.</span></span>  
  
 <span data-ttu-id="439af-127"><xref:System.EventHandler%601> obecný delegát eliminuje nutnost deklarovat typ delegáta pro zpracování událostí, pokud událost následuje vzor zpracování událostí, který používá .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="439af-127">The <xref:System.EventHandler%601> generic delegate eliminates the need to declare a delegate type to handle events, if your event follows the event-handling pattern used by the .NET Framework.</span></span> <span data-ttu-id="439af-128">Předpokládejme například, že jste vytvořili třídu `MyEventArgs` odvozenou z <xref:System.EventArgs>a chcete uchovávat data pro vaši událost.</span><span class="sxs-lookup"><span data-stu-id="439af-128">For example, suppose you have created a `MyEventArgs` class, derived from <xref:System.EventArgs>, to hold the data for your event.</span></span> <span data-ttu-id="439af-129">Následně můžete deklarovat událost následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="439af-129">You can then declare the event as follows:</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="439af-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="439af-130">See also</span></span>

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [<span data-ttu-id="439af-131">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="439af-131">Generics</span></span>](../../../docs/standard/generics/index.md)
- [<span data-ttu-id="439af-132">Obecné delegáty pro manipulaci s poli a seznamy</span><span class="sxs-lookup"><span data-stu-id="439af-132">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [<span data-ttu-id="439af-133">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="439af-133">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)
