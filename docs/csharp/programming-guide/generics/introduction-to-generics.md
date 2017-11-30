---
title: "Úvod do obecných typů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ec4fe9cc9fe7bf868fcc8afe4dc4e4234241e352
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-generics-c-programming-guide"></a><span data-ttu-id="56e95-102">Úvod do obecných typů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="56e95-102">Introduction to Generics (C# Programming Guide)</span></span>
<span data-ttu-id="56e95-103">Obecné třídy a metody kombinovat – opětovné použití, bezpečnost typů a efektivitu způsobem, který nelze jejich neobecné protějšky.</span><span class="sxs-lookup"><span data-stu-id="56e95-103">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="56e95-104">Obecné typy jsou nejčastěji používá s kolekcí a metody, které pracovat s nimi.</span><span class="sxs-lookup"><span data-stu-id="56e95-104">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="56e95-105">Knihovna tříd rozhraní .NET Framework verze 2.0 poskytuje nový obor názvů, <xref:System.Collections.Generic>, která obsahuje několik nové třídy kolekcí založených na obecné.</span><span class="sxs-lookup"><span data-stu-id="56e95-105">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="56e95-106">Je doporučeno, všechny aplikace, která cílí [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 2.0 a vyšší použít nové třídy obecnou kolekci místo starší svými protějšky neobecnou například <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="56e95-106">It is recommended that all applications that target the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="56e95-107">Další informace najdete v tématu [obecné typy v knihovně tříd rozhraní .NET Framework](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).</span><span class="sxs-lookup"><span data-stu-id="56e95-107">For more information, see [Generics in the .NET Framework Class Library](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).</span></span>  
  
 <span data-ttu-id="56e95-108">Samozřejmě můžete také vytvořit vlastní obecné typy a metody, které poskytují vlastní zobecněn řešení a vzory návrhu, které jsou bezpečnost typů a efektivní.</span><span class="sxs-lookup"><span data-stu-id="56e95-108">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="56e95-109">Následující příklad kódu ukazuje jednoduchý obecné třídy-list pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="56e95-109">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="56e95-110">(Ve většině případů byste měli použít <xref:System.Collections.Generic.List%601> poskytuje knihovna tříd rozhraní .NET Framework místo vytvoření vlastní třídy.) Parametr typu `T` se používá na různých místech, kde na konkrétní typ. by obvykle bylo použito k označení typ položky uložené v seznamu.</span><span class="sxs-lookup"><span data-stu-id="56e95-110">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="56e95-111">Použije se následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="56e95-111">It is used in the following ways:</span></span>  
  
-   <span data-ttu-id="56e95-112">Jako typ parametru metody v `AddHead` metoda.</span><span class="sxs-lookup"><span data-stu-id="56e95-112">As the type of a method parameter in the `AddHead` method.</span></span>  
  
-   <span data-ttu-id="56e95-113">Jako návratový typ veřejná metoda `GetNext` a `Data` vlastnost vnořeného `Node` třídy.</span><span class="sxs-lookup"><span data-stu-id="56e95-113">As the return type of the public method `GetNext` and the `Data` property in the nested `Node` class.</span></span>  
  
-   <span data-ttu-id="56e95-114">Jako typ privátního člena dat ve vnořené třídy.</span><span class="sxs-lookup"><span data-stu-id="56e95-114">As the type of the private member data in the nested class.</span></span>  
  
 <span data-ttu-id="56e95-115">Upozorňujeme, že je k dispozici pro vnořeného T `Node` třídy.</span><span class="sxs-lookup"><span data-stu-id="56e95-115">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="56e95-116">Když `GenericList<T>` je vytvořena s konkrétní typu, například jako `GenericList<int>`, každý výskyt `T` nahradí `int`.</span><span class="sxs-lookup"><span data-stu-id="56e95-116">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]  
  
 <span data-ttu-id="56e95-117">Následující příklad kódu ukazuje, jak kód klienta používá obecná `GenericList<T>` třídy můžete vytvořit seznam celých čísel.</span><span class="sxs-lookup"><span data-stu-id="56e95-117">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="56e95-118">Jednoduše změnou argument typu následující kód mohl snadno změnit vytvořit seznam řetězců nebo jiných vlastního typu:</span><span class="sxs-lookup"><span data-stu-id="56e95-118">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="56e95-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="56e95-119">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="56e95-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="56e95-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="56e95-121">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="56e95-121">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
