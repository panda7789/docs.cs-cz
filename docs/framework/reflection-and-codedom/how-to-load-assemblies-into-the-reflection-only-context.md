---
title: 'Postupy: Načtení sestavení do kontextu pouze pro reflexi'
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8dc05d27b0316c82c5314a766fcad929dc5f3698
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793130"
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a><span data-ttu-id="390ac-102">Postupy: Načtení sestavení do kontextu pouze pro reflexi</span><span class="sxs-lookup"><span data-stu-id="390ac-102">How to: Load Assemblies into the Reflection-Only Context</span></span>
<span data-ttu-id="390ac-103">Kontext načítání pouze pro reflexi umožňuje zkoumat sestavení zkompilován pro jiné platformy nebo u jiných verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="390ac-103">The reflection-only load context allows you to examine assemblies compiled for other platforms or for other versions of the .NET Framework.</span></span> <span data-ttu-id="390ac-104">Jenom se dají prozkoumat kód načtený do tohoto kontextu; nelze provést.</span><span class="sxs-lookup"><span data-stu-id="390ac-104">Code loaded into this context can only be examined; it cannot be executed.</span></span> <span data-ttu-id="390ac-105">To znamená, že nelze vytvořit objekty, protože konstruktory nemůže být proveden.</span><span class="sxs-lookup"><span data-stu-id="390ac-105">This means that objects cannot be created, because constructors cannot be executed.</span></span> <span data-ttu-id="390ac-106">Protože kód nelze provést, nejsou automaticky nahrány závislosti.</span><span class="sxs-lookup"><span data-stu-id="390ac-106">Because the code cannot be executed, dependencies are not automatically loaded.</span></span> <span data-ttu-id="390ac-107">Pokud je potřeba je prozkoumat, je nutné načíst je sami.</span><span class="sxs-lookup"><span data-stu-id="390ac-107">If you need to examine them, you must load them yourself.</span></span>  
  
### <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a><span data-ttu-id="390ac-108">Načtení sestavení do kontextu pouze pro reflexi zatížení</span><span class="sxs-lookup"><span data-stu-id="390ac-108">To load an assembly into the reflection-only load context</span></span>  
  
1. <span data-ttu-id="390ac-109">Použití <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> přetížení metody se načíst sestavení zadané zobrazované jméno, nebo <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metodu pro načtení sestavení zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="390ac-109">Use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> method overload to load the assembly given its display name, or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> method to load the assembly given its path.</span></span> <span data-ttu-id="390ac-110">Pokud je sestavení binárního obrazu, použijte <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="390ac-110">If the assembly is a binary image, use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> method overload.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="390ac-111">Načíst verzi souboru mscorlib.dll z verze rozhraní .NET Framework než verze v kontextu spuštění nelze použít kontext pouze pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="390ac-111">You cannot use the reflection-only context to load a version of mscorlib.dll from a version of the .NET Framework other than the version in the execution context.</span></span>  
  
2. <span data-ttu-id="390ac-112">Pokud sestavení obsahuje závislosti, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> je metoda nenačte.</span><span class="sxs-lookup"><span data-stu-id="390ac-112">If the assembly has dependencies, the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> method does not load them.</span></span> <span data-ttu-id="390ac-113">Pokud je potřeba je prozkoumat, je nutné načíst je sami.</span><span class="sxs-lookup"><span data-stu-id="390ac-113">If you need to examine them, you must load them yourself.</span></span>  
  
3. <span data-ttu-id="390ac-114">Určení, zda je sestavení načteno do kontextu pouze pro reflexi pomocí sestavení <xref:System.Reflection.Assembly.ReflectionOnly%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="390ac-114">Determine whether an assembly is loaded into the reflection-only context by using the assembly's <xref:System.Reflection.Assembly.ReflectionOnly%2A> property.</span></span>  
  
4. <span data-ttu-id="390ac-115">Pokud se atributy se použily k sestavení a typy v sestavení, prozkoumejte tyto atributy s použitím <xref:System.Reflection.CustomAttributeData> třídu zajistíte, že je proveden žádný pokus o spouštění kódu v kontextu pouze pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="390ac-115">If attributes have been applied to the assembly or to types in the assembly, examine those attributes by using the <xref:System.Reflection.CustomAttributeData> class to ensure that no attempt is made to execute code in the reflection-only context.</span></span> <span data-ttu-id="390ac-116">Použijte odpovídající přetížení <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metodu k získání <xref:System.Reflection.CustomAttributeData> reprezentují atributy použité na sestavení, člen, modul nebo parametr.</span><span class="sxs-lookup"><span data-stu-id="390ac-116">Use the appropriate overload of the <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method to obtain <xref:System.Reflection.CustomAttributeData> objects representing the attributes applied to an assembly, member, module, or parameter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="390ac-117">Atributy použité na sestavení nebo k jejímu obsahu může být definované v sestavení nebo mohou být definovány v jiném sestavení načtena do kontextu pouze pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="390ac-117">Attributes applied to the assembly or to its contents might be defined in the assembly, or they might be defined in another assembly loaded into the reflection-only context.</span></span> <span data-ttu-id="390ac-118">Neexistuje žádný způsob, jak předem říct, kde jsou definovány atributy.</span><span class="sxs-lookup"><span data-stu-id="390ac-118">There is no way to tell in advance where the attributes are defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="390ac-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="390ac-119">Example</span></span>  
 <span data-ttu-id="390ac-120">Následující příklad kódu ukazuje, jak prozkoumat atributy použité u sestavení načtena do kontextu pouze pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="390ac-120">The following code example shows how to examine the attributes applied to an assembly loaded into the reflection-only context.</span></span>  
  
 <span data-ttu-id="390ac-121">Příklad kódu definuje vlastní atribut s dva konstruktory a jednu vlastnost.</span><span class="sxs-lookup"><span data-stu-id="390ac-121">The code example defines a custom attribute with two constructors and one property.</span></span> <span data-ttu-id="390ac-122">Atribut je použit k sestavení, typ deklarovaný v sestavení, metoda typu a parametru metody.</span><span class="sxs-lookup"><span data-stu-id="390ac-122">The attribute is applied to the assembly, to a type declared in the assembly, to a method of the type, and to a parameter of the method.</span></span> <span data-ttu-id="390ac-123">Při spuštění sestavení samotné načte do kontextu pouze pro reflexi a zobrazí informace o vlastních atributů, které byly použity k němu a k typům a členům, které obsahuje.</span><span class="sxs-lookup"><span data-stu-id="390ac-123">When executed, the assembly loads itself into the reflection-only context and displays information about the custom attributes that were applied to it and to the types and members it contains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="390ac-124">Pro zjednodušení příkladu kódu, sestavení načte a zkoumá samotný.</span><span class="sxs-lookup"><span data-stu-id="390ac-124">To simplify the code example, the assembly loads and examines itself.</span></span> <span data-ttu-id="390ac-125">Za normálních okolností by měli očekávat najít stejné sestavení načtena do kontextu spuštění a kontextu pouze pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="390ac-125">Normally, you would not expect to find the same assembly loaded into both the execution context and the reflection-only context.</span></span>  
  
 [!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
 [!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
 [!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="390ac-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="390ac-126">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- <xref:System.Reflection.Assembly.ReflectionOnly%2A>
- <xref:System.Reflection.CustomAttributeData>
