---
title: "Rozdíly mezi šablonami C++ a obecnými typy C# (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aea1b51c26a8f3de56ea66b9cf89e75bfeb59d81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a><span data-ttu-id="ebbc0-102">Rozdíly mezi šablonami C++ a obecnými typy C# (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ebbc0-102">Differences Between C++ Templates and C# Generics (C# Programming Guide)</span></span>
<span data-ttu-id="ebbc0-103">Šablony obecnými typy C# a C++ jsou obě jazykové funkce, které poskytují podporu pro parametrizované typy.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-103">C# Generics and C++ templates are both language features that provide support for parameterized types.</span></span> <span data-ttu-id="ebbc0-104">Existují však mnoho rozdíly mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-104">However, there are many differences between the two.</span></span> <span data-ttu-id="ebbc0-105">Na úrovni syntaxe obecnými typy C# jsou jednodušší přístup k parametrizované typy bez složitost C++ šablon.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-105">At the syntax level, C# generics are a simpler approach to parameterized types without the complexity of C++ templates.</span></span> <span data-ttu-id="ebbc0-106">Kromě toho C# nepokouší poskytnout všechny funkce, které poskytují šablonami C++.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-106">In addition, C# does not attempt to provide all of the functionality that C++ templates provide.</span></span> <span data-ttu-id="ebbc0-107">Na úrovni implementace základní rozdíl je, že náhrady obecného typu C# jsou prováděny v době běhu a instancí objektů se tím zachovají informace obecného typu.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-107">At the implementation level, the primary difference is that C# generic type substitutions are performed at runtime and generic type information is thereby preserved for instantiated objects.</span></span> <span data-ttu-id="ebbc0-108">Další informace najdete v tématu [obecné typy v čase spuštění](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="ebbc0-108">For more information, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
 <span data-ttu-id="ebbc0-109">Tady jsou klíčové rozdíly mezi šablony C++ a obecnými typy C#:</span><span class="sxs-lookup"><span data-stu-id="ebbc0-109">The following are the key differences between C# Generics and C++ templates:</span></span>  
  
-   <span data-ttu-id="ebbc0-110">Obecnými typy C# neposkytují stejnou úroveň flexibilitu jako šablony jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-110">C# generics do not provide the same amount of flexibility as C++ templates.</span></span> <span data-ttu-id="ebbc0-111">Není například možné volat aritmetické operátory v jazyce C# obecné třídy, přestože je možné volat uživatelem definovaných operátorů.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-111">For example, it is not possible to call arithmetic operators in a C# generic class, although it is possible to call user defined operators.</span></span>  
  
-   <span data-ttu-id="ebbc0-112">C# neumožňuje parametry šablon bez typu, například `template C<int i> {}`.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-112">C# does not allow non-type template parameters, such as `template C<int i> {}`.</span></span>  
  
-   <span data-ttu-id="ebbc0-113">C# nepodporuje explicitní specializace; To znamená, vlastní implementaci šablonu pro konkrétní typ.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-113">C# does not support explicit specialization; that is, a custom implementation of a template for a specific type.</span></span>  
  
-   <span data-ttu-id="ebbc0-114">C# nepodporuje částečná specializace: vlastní implementace pro podmnožinu argumenty typu.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-114">C# does not support partial specialization: a custom implementation for a subset of the type arguments.</span></span>  
  
-   <span data-ttu-id="ebbc0-115">C# neumožňuje parametr typu, který se má použít jako základní třída pro obecný typ.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-115">C# does not allow the type parameter to be used as the base class for the generic type.</span></span>  
  
-   <span data-ttu-id="ebbc0-116">C# neumožňuje parametry typu do mají výchozí typy.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-116">C# does not allow type parameters to have default types.</span></span>  
  
-   <span data-ttu-id="ebbc0-117">V jazyce C# parametr obecného typu samotné nelze obecný, i když sestavené typy lze použít jako obecné typy.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-117">In C#, a generic type parameter cannot itself be a generic, although constructed types can be used as generics.</span></span> <span data-ttu-id="ebbc0-118">C++ povolit parametry šablony.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-118">C++ does allow template parameters.</span></span>  
  
-   <span data-ttu-id="ebbc0-119">C++ umožňuje kód, který nemusí platit pro všechny parametry typu v šabloně, která kontroluje pro konkrétní typ použít jako parametr typu.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-119">C++ allows code that might not be valid for all type parameters in the template, which is then checked for the specific type used as the type parameter.</span></span> <span data-ttu-id="ebbc0-120">C# vyžaduje kód ve třídě k zapsání tak, že bude fungovat s žádný typ, který splňuje omezení.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-120">C# requires code in a class to be written in such a way that it will work with any type that satisfies the constraints.</span></span> <span data-ttu-id="ebbc0-121">Například v jazyce C++ je možné vytvořit funkci, která používá aritmetické operátory `+` a `-` u objektů typu parametru, která způsobí chybu v době vytvoření instance šablony s typem, který nepodporuje tyto operátory.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-121">For example, in C++ it is possible to write a function that uses the arithmetic operators `+` and `-` on objects of the type parameter, which will produce an error at the time of instantiation of the template with a type that does not support these operators.</span></span> <span data-ttu-id="ebbc0-122">C# zakáže to; pouze jazykové konstrukty povolené jsou ty, které lze odvodit z omezení.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-122">C# disallows this; the only language constructs allowed are those that can be deduced from the constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebbc0-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="ebbc0-123">See Also</span></span>  
 [<span data-ttu-id="ebbc0-124">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ebbc0-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ebbc0-125">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="ebbc0-125">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="ebbc0-126">Šablony</span><span class="sxs-lookup"><span data-stu-id="ebbc0-126">Templates</span></span>](/cpp/cpp/templates-cpp)
