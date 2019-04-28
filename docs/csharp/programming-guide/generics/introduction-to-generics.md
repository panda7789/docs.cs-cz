---
title: Úvod do obecných typů - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
ms.openlocfilehash: d09cc686e934f722193cb4671d25671f7f4ef5f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61679788"
---
# <a name="introduction-to-generics-c-programming-guide"></a><span data-ttu-id="48f27-102">Úvod do obecných typů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="48f27-102">Introduction to Generics (C# Programming Guide)</span></span>
<span data-ttu-id="48f27-103">Obecné třídy a metody opětovné použití, bezpečnost typů a efektivitu tak, aby jejich obecné protějšky nelze kombinovat.</span><span class="sxs-lookup"><span data-stu-id="48f27-103">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="48f27-104">Obecné typy se nejčastěji používají s kolekcí a metody, které pracují s nimi.</span><span class="sxs-lookup"><span data-stu-id="48f27-104">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="48f27-105">Knihovna tříd rozhraní .NET Framework verze 2.0 obsahuje nový obor názvů <xref:System.Collections.Generic>, která obsahuje několik nových obecné kolekce tříd.</span><span class="sxs-lookup"><span data-stu-id="48f27-105">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="48f27-106">Doporučuje se, že všechny aplikace, jejichž cílem rozhraní .NET Framework 2.0 a pozdější použití nové obecné kolekce tříd, namísto starší jejich obecné protějšky například <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="48f27-106">It is recommended that all applications that target the .NET Framework 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="48f27-107">Další informace najdete v tématu [obecné typy v .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="48f27-107">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="48f27-108">Samozřejmě můžete také vytvořit vlastní obecné typy a metody, které poskytují vlastní generalizované řešení a vzorů návrhu, které jsou typově bezpečné a efektivní.</span><span class="sxs-lookup"><span data-stu-id="48f27-108">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="48f27-109">Následující příklad kódu ukazuje jednoduchý obecné třídy propojené seznamy pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="48f27-109">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="48f27-110">(Ve většině případů byste měli použít <xref:System.Collections.Generic.List%601> poskytovaných knihovnou tříd rozhraní .NET Framework místo vytvoření vlastní třídy.) Parametr typu `T` se používá v několika umístěních, kde konkrétního typu implementujícího typ by obvykle použít k označení typu položky uložené v seznamu.</span><span class="sxs-lookup"><span data-stu-id="48f27-110">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="48f27-111">Používá se následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="48f27-111">It is used in the following ways:</span></span>  
  
- <span data-ttu-id="48f27-112">Jako typ parametru metody `AddHead` metody.</span><span class="sxs-lookup"><span data-stu-id="48f27-112">As the type of a method parameter in the `AddHead` method.</span></span>  
  
- <span data-ttu-id="48f27-113">Jako návratový typ `Data` vlastnost ve vnořeném `Node` třídy.</span><span class="sxs-lookup"><span data-stu-id="48f27-113">As the return type of the `Data` property in the nested `Node` class.</span></span>  
  
- <span data-ttu-id="48f27-114">Jako typ soukromému členu `data` ve vnořené třídě.</span><span class="sxs-lookup"><span data-stu-id="48f27-114">As the type of the private member `data` in the nested class.</span></span>  
  
 <span data-ttu-id="48f27-115">Všimněte si, že je k dispozici ve vnořeném T `Node` třídy.</span><span class="sxs-lookup"><span data-stu-id="48f27-115">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="48f27-116">Když `GenericList<T>` je vytvořena instance s konkrétního typu implementujícího typ, třeba jako `GenericList<int>`, každý výskyt `T` bude nahrazena adresou `int`.</span><span class="sxs-lookup"><span data-stu-id="48f27-116">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 <span data-ttu-id="48f27-117">Následující příklad kódu ukazuje, jak kód klienta používá Obecné `GenericList<T>` třídy za účelem vytvoření seznamu celých čísel.</span><span class="sxs-lookup"><span data-stu-id="48f27-117">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="48f27-118">Jednoduše tak, že změníte typ argumentu, následující kód by mohl snadno upravit tak, aby vytvořit seznam řetězců nebo jiný vlastní typ:</span><span class="sxs-lookup"><span data-stu-id="48f27-118">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="48f27-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48f27-119">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="48f27-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="48f27-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="48f27-121">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="48f27-121">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
