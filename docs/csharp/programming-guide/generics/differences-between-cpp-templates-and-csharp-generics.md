---
title: Rozdíly mezi šablonami C++ a C# obecných typů - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: 0dd06aead738bb5ea1dcee7e7dade99be80582b6
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236424"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a><span data-ttu-id="fc3a3-102">Rozdíly mezi šablonami C++ a obecnými typy C# (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="fc3a3-102">Differences Between C++ Templates and C# Generics (C# Programming Guide)</span></span>
<span data-ttu-id="fc3a3-103">Šablony obecnými typy C# a C++ jsou obě vlastnosti jazyka, které poskytují podporu pro parametrizované typy.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-103">C# Generics and C++ templates are both language features that provide support for parameterized types.</span></span> <span data-ttu-id="fc3a3-104">Existují však mnoho rozdíly mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-104">However, there are many differences between the two.</span></span> <span data-ttu-id="fc3a3-105">Na úrovni syntaxe obecnými typy C# jsou jednodušší přístup k parametrizované typy bez složitosti šablon jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-105">At the syntax level, C# generics are a simpler approach to parameterized types without the complexity of C++ templates.</span></span> <span data-ttu-id="fc3a3-106">Kromě toho C# nepokouší poskytují všechny funkce, které poskytují šablony jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-106">In addition, C# does not attempt to provide all of the functionality that C++ templates provide.</span></span> <span data-ttu-id="fc3a3-107">Na úrovni implementace základní rozdíl je, že nahrazení obecného typu C# jsou prováděny v době běhu a instance objektů se tak zachovají informace obecného typu.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-107">At the implementation level, the primary difference is that C# generic type substitutions are performed at runtime and generic type information is thereby preserved for instantiated objects.</span></span> <span data-ttu-id="fc3a3-108">Další informace najdete v tématu [obecné typy v čase spuštění](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="fc3a3-108">For more information, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
 <span data-ttu-id="fc3a3-109">Toto jsou hlavní rozdíly mezi obecnými typy C# a šablony C++:</span><span class="sxs-lookup"><span data-stu-id="fc3a3-109">The following are the key differences between C# Generics and C++ templates:</span></span>  
  
-   <span data-ttu-id="fc3a3-110">Obecnými typy C# neposkytuje velkou flexibilitu jako šablony jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-110">C# generics do not provide the same amount of flexibility as C++ templates.</span></span> <span data-ttu-id="fc3a3-111">Například není možné volat aritmetických operátorů v jazyce C# generické třídě, i když je možné volat uživatelem definovaných operátorů.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-111">For example, it is not possible to call arithmetic operators in a C# generic class, although it is possible to call user defined operators.</span></span>  
  
-   <span data-ttu-id="fc3a3-112">C# nepovoluje parametry šablony bez typu, jako například `template C<int i> {}`.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-112">C# does not allow non-type template parameters, such as `template C<int i> {}`.</span></span>  
  
-   <span data-ttu-id="fc3a3-113">C# nepodporuje explicitní specializace; To znamená, vlastní implementaci šablonu pro konkrétního typu.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-113">C# does not support explicit specialization; that is, a custom implementation of a template for a specific type.</span></span>  
  
-   <span data-ttu-id="fc3a3-114">C# nepodporuje částečná specializace: vlastní implementaci pro podmnožinu argumentů typu.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-114">C# does not support partial specialization: a custom implementation for a subset of the type arguments.</span></span>  
  
-   <span data-ttu-id="fc3a3-115">C# nepovoluje parametr typu má být použit jako základní třída pro obecného typu.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-115">C# does not allow the type parameter to be used as the base class for the generic type.</span></span>  
  
-   <span data-ttu-id="fc3a3-116">C# nepovoluje typové parametry mají výchozí typy.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-116">C# does not allow type parameters to have default types.</span></span>  
  
-   <span data-ttu-id="fc3a3-117">V jazyce C# parametr obecného typu nemůže být sám obecný, i když sestavené typy slouží jako obecné typy.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-117">In C#, a generic type parameter cannot itself be a generic, although constructed types can be used as generics.</span></span> <span data-ttu-id="fc3a3-118">C++ neumožňuje parametry šablony.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-118">C++ does allow template parameters.</span></span>  
  
-   <span data-ttu-id="fc3a3-119">Jazyk C++ umožňuje kód, který nemusí platit pro všechny parametry typu v šabloně, která se pak kontroluje u konkrétní typ použitý jako parametr typu.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-119">C++ allows code that might not be valid for all type parameters in the template, which is then checked for the specific type used as the type parameter.</span></span> <span data-ttu-id="fc3a3-120">C# vyžaduje kód ve třídě má být zapsán tak, že bude fungovat s jakýmkoli typem, který splňuje omezení.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-120">C# requires code in a class to be written in such a way that it will work with any type that satisfies the constraints.</span></span> <span data-ttu-id="fc3a3-121">Například v jazyce C++ je možné psát funkce, která používá aritmetické operátory `+` a `-` u objektů parametru typu, který vygeneruje chybu v době vytváření instancí šablony s typem, který nepodporuje tyto operátory.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-121">For example, in C++ it is possible to write a function that uses the arithmetic operators `+` and `-` on objects of the type parameter, which will produce an error at the time of instantiation of the template with a type that does not support these operators.</span></span> <span data-ttu-id="fc3a3-122">C# zakazuje pouze jazykové konstrukce povolené jsou ty, které je možné odvodit z omezení.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-122">C# disallows this; the only language constructs allowed are those that can be deduced from the constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc3a3-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc3a3-123">See Also</span></span>

- [<span data-ttu-id="fc3a3-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="fc3a3-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="fc3a3-125">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="fc3a3-125">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [<span data-ttu-id="fc3a3-126">Šablony</span><span class="sxs-lookup"><span data-stu-id="fc3a3-126">Templates</span></span>](/cpp/cpp/templates-cpp)
