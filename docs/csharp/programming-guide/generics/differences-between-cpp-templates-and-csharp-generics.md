---
title: Rozdíly mezi šablonami C++ a obecnými typy C# – Průvodce programováním v C#
description: Přečtěte si o rozdílech mezi šablonami C++ a obecnými typy C#. Oba jsou jazykové funkce, které poskytují podporu pro parametrizované typy.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: f405e2d4bef730317703b3b8470edef5b89f0bed
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301928"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a><span data-ttu-id="cc975-104">Rozdíly mezi šablonami C++ a obecnými typy C# (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="cc975-104">Differences Between C++ Templates and C# Generics (C# Programming Guide)</span></span>
<span data-ttu-id="cc975-105">Obecné typy a šablony jazyka C++ jsou funkce jazyka, které poskytují podporu pro parametrizované typy.</span><span class="sxs-lookup"><span data-stu-id="cc975-105">C# Generics and C++ templates are both language features that provide support for parameterized types.</span></span> <span data-ttu-id="cc975-106">Existuje však mnoho rozdílů mezi těmito dvěma.</span><span class="sxs-lookup"><span data-stu-id="cc975-106">However, there are many differences between the two.</span></span> <span data-ttu-id="cc975-107">Na úrovni syntaxe jsou obecné typy C# jednodušší přístup k parametrizovaným typům bez složitosti šablon jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="cc975-107">At the syntax level, C# generics are a simpler approach to parameterized types without the complexity of C++ templates.</span></span> <span data-ttu-id="cc975-108">Kromě toho C# nepokusí o poskytnutí všech funkcí, které poskytují šablony jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="cc975-108">In addition, C# does not attempt to provide all of the functionality that C++ templates provide.</span></span> <span data-ttu-id="cc975-109">Na úrovni implementace je hlavním rozdílem, že nahrazení obecného typu jazyka C# jsou prováděna za běhu a informace o obecném typu jsou zachovány pro instance objektů.</span><span class="sxs-lookup"><span data-stu-id="cc975-109">At the implementation level, the primary difference is that C# generic type substitutions are performed at runtime and generic type information is thereby preserved for instantiated objects.</span></span> <span data-ttu-id="cc975-110">Další informace naleznete v tématu [Obecné typy v době běhu](./generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="cc975-110">For more information, see [Generics in the Run Time](./generics-in-the-run-time.md).</span></span>  
  
 <span data-ttu-id="cc975-111">Níže jsou uvedené klíčové rozdíly mezi obecnými typy C# a šablonami jazyka C++:</span><span class="sxs-lookup"><span data-stu-id="cc975-111">The following are the key differences between C# Generics and C++ templates:</span></span>  
  
- <span data-ttu-id="cc975-112">Obecné typy jazyka C# neposkytují stejné množství flexibility jako šablony jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="cc975-112">C# generics do not provide the same amount of flexibility as C++ templates.</span></span> <span data-ttu-id="cc975-113">Například není možné volat aritmetické operátory v obecné třídě C#, i když je možné volat operátory definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="cc975-113">For example, it is not possible to call arithmetic operators in a C# generic class, although it is possible to call user defined operators.</span></span>  
  
- <span data-ttu-id="cc975-114">Jazyk C# nepovoluje parametry šablony bez typu, například `template C<int i> {}` .</span><span class="sxs-lookup"><span data-stu-id="cc975-114">C# does not allow non-type template parameters, such as `template C<int i> {}`.</span></span>  
  
- <span data-ttu-id="cc975-115">Jazyk C# nepodporuje explicitní specializaci; To znamená vlastní implementace šablony pro konkrétní typ.</span><span class="sxs-lookup"><span data-stu-id="cc975-115">C# does not support explicit specialization; that is, a custom implementation of a template for a specific type.</span></span>  
  
- <span data-ttu-id="cc975-116">Jazyk C# nepodporuje částečnou specializaci: vlastní implementaci pro podmnožinu argumentů typu.</span><span class="sxs-lookup"><span data-stu-id="cc975-116">C# does not support partial specialization: a custom implementation for a subset of the type arguments.</span></span>  
  
- <span data-ttu-id="cc975-117">Jazyk C# nepovoluje, aby byl parametr typu použit jako základní třída pro obecný typ.</span><span class="sxs-lookup"><span data-stu-id="cc975-117">C# does not allow the type parameter to be used as the base class for the generic type.</span></span>  
  
- <span data-ttu-id="cc975-118">Jazyk C# nepovoluje, aby parametry typu měly výchozí typy.</span><span class="sxs-lookup"><span data-stu-id="cc975-118">C# does not allow type parameters to have default types.</span></span>  
  
- <span data-ttu-id="cc975-119">V jazyce C# nemůže být parametr obecného typu sám obecný, i když konstruované typy lze použít jako obecné.</span><span class="sxs-lookup"><span data-stu-id="cc975-119">In C#, a generic type parameter cannot itself be a generic, although constructed types can be used as generics.</span></span> <span data-ttu-id="cc975-120">Jazyk C++ povoluje parametry šablony.</span><span class="sxs-lookup"><span data-stu-id="cc975-120">C++ does allow template parameters.</span></span>  
  
- <span data-ttu-id="cc975-121">Jazyk C++ umožňuje kód, který nemusí být platný pro všechny parametry typu v šabloně, která je poté kontrolována pro konkrétní typ použitý jako parametr typu.</span><span class="sxs-lookup"><span data-stu-id="cc975-121">C++ allows code that might not be valid for all type parameters in the template, which is then checked for the specific type used as the type parameter.</span></span> <span data-ttu-id="cc975-122">Jazyk C# vyžaduje, aby kód ve třídě byl napsán takovým způsobem, který bude fungovat s jakýmkoli typem, který splňuje omezení.</span><span class="sxs-lookup"><span data-stu-id="cc975-122">C# requires code in a class to be written in such a way that it will work with any type that satisfies the constraints.</span></span> <span data-ttu-id="cc975-123">Například v jazyce C++ je možné napsat funkci, která používá aritmetické operátory `+` a `-` objekty parametru typu, což způsobí chybu v době vytváření instance šablony s typem, který tyto operátory nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="cc975-123">For example, in C++ it is possible to write a function that uses the arithmetic operators `+` and `-` on objects of the type parameter, which will produce an error at the time of instantiation of the template with a type that does not support these operators.</span></span> <span data-ttu-id="cc975-124">C# to nepovoluje; jsou povoleny pouze jazykové konstrukce, které lze odvodit z omezení.</span><span class="sxs-lookup"><span data-stu-id="cc975-124">C# disallows this; the only language constructs allowed are those that can be deduced from the constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc975-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc975-125">See also</span></span>

- [<span data-ttu-id="cc975-126">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="cc975-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cc975-127">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="cc975-127">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="cc975-128">Šablony</span><span class="sxs-lookup"><span data-stu-id="cc975-128">Templates</span></span>](/cpp/cpp/templates-cpp)
