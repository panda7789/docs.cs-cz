---
title: 'Postupy: Načtení sestavení do kontextu pouze pro reflexi'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, reflection-only loader context
- assemblies [.NET Framework], loading for reflection
- attributes [.NET Framework], retrieving
- assemblies [.NET Framework], reflection-only loader context
- reflection-only loader context
ms.assetid: 9818b660-52f5-423d-a9af-e75163aa7068
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6ab0224dd0452003f1d43a314d03aaca0fe04fda
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a><span data-ttu-id="d1098-102">Postupy: Načtení sestavení do kontextu pouze pro reflexi</span><span class="sxs-lookup"><span data-stu-id="d1098-102">How to: Load Assemblies into the Reflection-Only Context</span></span>
<span data-ttu-id="d1098-103">Kontext načítání pouze pro reflexi umožňuje zkontrolovat sestavení zkompilovat pro jiné platformy, nebo pro jiné verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d1098-103">The reflection-only load context allows you to examine assemblies compiled for other platforms or for other versions of the .NET Framework.</span></span> <span data-ttu-id="d1098-104">Kód načtený do tohoto kontextu mohou být hodnoceny pouze; nelze provést.</span><span class="sxs-lookup"><span data-stu-id="d1098-104">Code loaded into this context can only be examined; it cannot be executed.</span></span> <span data-ttu-id="d1098-105">To znamená, že objekty nelze vytvořit, protože konstruktory nelze provést.</span><span class="sxs-lookup"><span data-stu-id="d1098-105">This means that objects cannot be created, because constructors cannot be executed.</span></span> <span data-ttu-id="d1098-106">Protože kód nelze provést, nejsou automaticky načíst závislosti.</span><span class="sxs-lookup"><span data-stu-id="d1098-106">Because the code cannot be executed, dependencies are not automatically loaded.</span></span> <span data-ttu-id="d1098-107">Pokud potřebujete posoudit, je nutné načíst je sami.</span><span class="sxs-lookup"><span data-stu-id="d1098-107">If you need to examine them, you must load them yourself.</span></span>  
  
### <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a><span data-ttu-id="d1098-108">Načtení sestavení do kontextu pouze pro reflexi zatížení</span><span class="sxs-lookup"><span data-stu-id="d1098-108">To load an assembly into the reflection-only load context</span></span>  
  
1.  <span data-ttu-id="d1098-109">Použití <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> přetížení metody se načíst sestavení zadaný zobrazovaný název, nebo <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metoda načíst sestavení zadané cesty.</span><span class="sxs-lookup"><span data-stu-id="d1098-109">Use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> method overload to load the assembly given its display name, or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> method to load the assembly given its path.</span></span> <span data-ttu-id="d1098-110">Pokud je sestavení binární bitovou kopii, použijte <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="d1098-110">If the assembly is a binary image, use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> method overload.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d1098-111">Kontext pouze pro reflexi nelze použít k načtení verzi mscorlib.dll z verze rozhraní .NET Framework, než verze v kontextu spuštění.</span><span class="sxs-lookup"><span data-stu-id="d1098-111">You cannot use the reflection-only context to load a version of mscorlib.dll from a version of the .NET Framework other than the version in the execution context.</span></span>  
  
2.  <span data-ttu-id="d1098-112">Pokud má sestavení závislosti, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> metoda je nenačte.</span><span class="sxs-lookup"><span data-stu-id="d1098-112">If the assembly has dependencies, the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> method does not load them.</span></span> <span data-ttu-id="d1098-113">Pokud potřebujete posoudit, je nutné načíst je sami.</span><span class="sxs-lookup"><span data-stu-id="d1098-113">If you need to examine them, you must load them yourself.</span></span>  
  
3.  <span data-ttu-id="d1098-114">Určit, zda je sestavení do kontextu pouze pro reflexi načíst pomocí sestavení <xref:System.Reflection.Assembly.ReflectionOnly%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d1098-114">Determine whether an assembly is loaded into the reflection-only context by using the assembly's <xref:System.Reflection.Assembly.ReflectionOnly%2A> property.</span></span>  
  
4.  <span data-ttu-id="d1098-115">Pokud atributy se používají k sestavení nebo typy v sestavení, zkontrolujte pomocí těchto atributů <xref:System.Reflection.CustomAttributeData> třída zajistit, že žádné pokusu o spuštění kódu v kontextu pouze pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="d1098-115">If attributes have been applied to the assembly or to types in the assembly, examine those attributes by using the <xref:System.Reflection.CustomAttributeData> class to ensure that no attempt is made to execute code in the reflection-only context.</span></span> <span data-ttu-id="d1098-116">Použijte odpovídající přetížení <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metoda získat <xref:System.Reflection.CustomAttributeData> objekty, které představují atributy použité na sestavení, člen, modul nebo parametr.</span><span class="sxs-lookup"><span data-stu-id="d1098-116">Use the appropriate overload of the <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method to obtain <xref:System.Reflection.CustomAttributeData> objects representing the attributes applied to an assembly, member, module, or parameter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d1098-117">Atributy použité na sestavení nebo na jeho obsah může být definovaná v sestavení, nebo může být definovaná v jiném sestavení do kontextu pouze pro reflexi načteno.</span><span class="sxs-lookup"><span data-stu-id="d1098-117">Attributes applied to the assembly or to its contents might be defined in the assembly, or they might be defined in another assembly loaded into the reflection-only context.</span></span> <span data-ttu-id="d1098-118">Neexistuje žádný způsob, jak předem říct, kde jsou definovány atributy.</span><span class="sxs-lookup"><span data-stu-id="d1098-118">There is no way to tell in advance where the attributes are defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1098-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1098-119">Example</span></span>  
 <span data-ttu-id="d1098-120">Následující příklad kódu ukazuje, jak prozkoumat atributy použité k sestavení do kontextu pouze pro reflexi načteno.</span><span class="sxs-lookup"><span data-stu-id="d1098-120">The following code example shows how to examine the attributes applied to an assembly loaded into the reflection-only context.</span></span>  
  
 <span data-ttu-id="d1098-121">Příklad kódu definuje vlastní atribut s dva konstruktory a jednu vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d1098-121">The code example defines a custom attribute with two constructors and one property.</span></span> <span data-ttu-id="d1098-122">Atribut se použije na sestavení, typu deklarován v sestavení, metoda typu a do parametru metody.</span><span class="sxs-lookup"><span data-stu-id="d1098-122">The attribute is applied to the assembly, to a type declared in the assembly, to a method of the type, and to a parameter of the method.</span></span> <span data-ttu-id="d1098-123">Po provedení sestavení načte samotné do kontextu pouze pro reflexi a zobrazí informace o vlastních atributů, které byly použity k němu a typy a členy, které obsahuje.</span><span class="sxs-lookup"><span data-stu-id="d1098-123">When executed, the assembly loads itself into the reflection-only context and displays information about the custom attributes that were applied to it and to the types and members it contains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1098-124">Pro zjednodušení příkladu kódu, sestavení načte a prověří sám sebe.</span><span class="sxs-lookup"><span data-stu-id="d1098-124">To simplify the code example, the assembly loads and examines itself.</span></span> <span data-ttu-id="d1098-125">Za normálních okolností by byste měli najít do stejného sestavení do kontextu spuštění a kontext pouze pro reflexi načteno.</span><span class="sxs-lookup"><span data-stu-id="d1098-125">Normally, you would not expect to find the same assembly loaded into both the execution context and the reflection-only context.</span></span>  
  
 [!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
 [!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
 [!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d1098-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1098-126">See Also</span></span>  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>  
 <xref:System.Reflection.Assembly.ReflectionOnly%2A>  
 <xref:System.Reflection.CustomAttributeData>
