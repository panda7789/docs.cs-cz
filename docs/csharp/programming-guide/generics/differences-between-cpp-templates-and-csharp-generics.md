---
title: Rozdíly mezi C++ šablonami C# a obecnými C# typy – Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: b794666501fb27d2f73a6050f85df3725050982e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589863"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a><span data-ttu-id="947ba-102">Rozdíly mezi šablonami C++ a obecnými typy C# (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="947ba-102">Differences Between C++ Templates and C# Generics (C# Programming Guide)</span></span>
<span data-ttu-id="947ba-103">C#Obecné typy a C++ šablony jsou obě funkce jazyka, které poskytují podporu pro parametrizované typy.</span><span class="sxs-lookup"><span data-stu-id="947ba-103">C# Generics and C++ templates are both language features that provide support for parameterized types.</span></span> <span data-ttu-id="947ba-104">Existuje však mnoho rozdílů mezi těmito dvěma.</span><span class="sxs-lookup"><span data-stu-id="947ba-104">However, there are many differences between the two.</span></span> <span data-ttu-id="947ba-105">Na úrovni syntaxe C# obecné jsou jednodušší přístup k parametrizovaným typům bez složitosti C++ šablon.</span><span class="sxs-lookup"><span data-stu-id="947ba-105">At the syntax level, C# generics are a simpler approach to parameterized types without the complexity of C++ templates.</span></span> <span data-ttu-id="947ba-106">Kromě toho C# se nepokouší poskytovat všechny funkce, které C++ poskytují šablony.</span><span class="sxs-lookup"><span data-stu-id="947ba-106">In addition, C# does not attempt to provide all of the functionality that C++ templates provide.</span></span> <span data-ttu-id="947ba-107">Na úrovni implementace je hlavním rozdílem, že C# nahrazení obecného typu jsou prováděna za běhu a informace o obecném typu jsou zachovány pro instance objektů.</span><span class="sxs-lookup"><span data-stu-id="947ba-107">At the implementation level, the primary difference is that C# generic type substitutions are performed at runtime and generic type information is thereby preserved for instantiated objects.</span></span> <span data-ttu-id="947ba-108">Další informace naleznete v tématu [Obecné typy v době běhu](./generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="947ba-108">For more information, see [Generics in the Run Time](./generics-in-the-run-time.md).</span></span>  
  
 <span data-ttu-id="947ba-109">Níže jsou uvedené klíčové rozdíly mezi C# obecnými a C++ šablonami:</span><span class="sxs-lookup"><span data-stu-id="947ba-109">The following are the key differences between C# Generics and C++ templates:</span></span>  
  
- <span data-ttu-id="947ba-110">C#Obecné typy neposkytují stejné množství flexibility jako C++ šablony.</span><span class="sxs-lookup"><span data-stu-id="947ba-110">C# generics do not provide the same amount of flexibility as C++ templates.</span></span> <span data-ttu-id="947ba-111">Například není možné volat aritmetické operátory v C# obecné třídě, i když je možné volat operátory definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="947ba-111">For example, it is not possible to call arithmetic operators in a C# generic class, although it is possible to call user defined operators.</span></span>  
  
- <span data-ttu-id="947ba-112">C#nepovoluje parametry šablony bez typu, například `template C<int i> {}`.</span><span class="sxs-lookup"><span data-stu-id="947ba-112">C# does not allow non-type template parameters, such as `template C<int i> {}`.</span></span>  
  
- <span data-ttu-id="947ba-113">C#nepodporuje explicitní specializaci; To znamená vlastní implementace šablony pro konkrétní typ.</span><span class="sxs-lookup"><span data-stu-id="947ba-113">C# does not support explicit specialization; that is, a custom implementation of a template for a specific type.</span></span>  
  
- <span data-ttu-id="947ba-114">C#nepodporuje částečnou specializaci: vlastní implementaci pro podmnožinu argumentů typu.</span><span class="sxs-lookup"><span data-stu-id="947ba-114">C# does not support partial specialization: a custom implementation for a subset of the type arguments.</span></span>  
  
- <span data-ttu-id="947ba-115">C#nepovoluje, aby byl parametr typu použit jako základní třída pro obecný typ.</span><span class="sxs-lookup"><span data-stu-id="947ba-115">C# does not allow the type parameter to be used as the base class for the generic type.</span></span>  
  
- <span data-ttu-id="947ba-116">C#nepovoluje, aby parametry typu měly výchozí typy.</span><span class="sxs-lookup"><span data-stu-id="947ba-116">C# does not allow type parameters to have default types.</span></span>  
  
- <span data-ttu-id="947ba-117">V C#, obecný parametr typu nemůže být obecný, i když konstruované typy lze použít jako obecné.</span><span class="sxs-lookup"><span data-stu-id="947ba-117">In C#, a generic type parameter cannot itself be a generic, although constructed types can be used as generics.</span></span> <span data-ttu-id="947ba-118">C++povolí parametry šablony.</span><span class="sxs-lookup"><span data-stu-id="947ba-118">C++ does allow template parameters.</span></span>  
  
- <span data-ttu-id="947ba-119">C++povoluje kód, který nemusí být platný pro všechny parametry typu v šabloně, která je poté kontrolována pro konkrétní typ použitý jako parametr typu.</span><span class="sxs-lookup"><span data-stu-id="947ba-119">C++ allows code that might not be valid for all type parameters in the template, which is then checked for the specific type used as the type parameter.</span></span> <span data-ttu-id="947ba-120">C#vyžaduje, aby kód ve třídě byl napsán takovým způsobem, který bude fungovat s jakýmkoli typem, který splňuje omezení.</span><span class="sxs-lookup"><span data-stu-id="947ba-120">C# requires code in a class to be written in such a way that it will work with any type that satisfies the constraints.</span></span> <span data-ttu-id="947ba-121">Například C++ je možné napsat funkci, která používá aritmetické operátory `+` a `-` objekty parametru typu, čímž dojde k chybě v době vytváření instance šablony s typem, který není podporovat tyto operátory.</span><span class="sxs-lookup"><span data-stu-id="947ba-121">For example, in C++ it is possible to write a function that uses the arithmetic operators `+` and `-` on objects of the type parameter, which will produce an error at the time of instantiation of the template with a type that does not support these operators.</span></span> <span data-ttu-id="947ba-122">C#nepovoluje se. jsou povoleny pouze jazykové konstrukce, které lze odvodit z omezení.</span><span class="sxs-lookup"><span data-stu-id="947ba-122">C# disallows this; the only language constructs allowed are those that can be deduced from the constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="947ba-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="947ba-123">See also</span></span>

- [<span data-ttu-id="947ba-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="947ba-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="947ba-125">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="947ba-125">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="947ba-126">Šablony</span><span class="sxs-lookup"><span data-stu-id="947ba-126">Templates</span></span>](/cpp/cpp/templates-cpp)
