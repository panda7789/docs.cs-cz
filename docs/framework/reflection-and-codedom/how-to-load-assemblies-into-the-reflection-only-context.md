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
ms.openlocfilehash: 8e22dcf7db5ec2c78a79e574604e0b39b4962727
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971847"
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a><span data-ttu-id="93eab-102">Postupy: Načtení sestavení do kontextu pouze pro reflexi</span><span class="sxs-lookup"><span data-stu-id="93eab-102">How to: Load Assemblies into the Reflection-Only Context</span></span>

<span data-ttu-id="93eab-103">Kontext zatížení pouze pro reflexi umožňuje kontrolovat sestavení kompilovaná pro jiné platformy nebo pro jiné verze .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="93eab-103">The reflection-only load context allows you to examine assemblies compiled for other platforms or for other versions of the .NET Framework.</span></span> <span data-ttu-id="93eab-104">Kód načtený do tohoto kontextu lze prozkoumat pouze; nedá se spustit.</span><span class="sxs-lookup"><span data-stu-id="93eab-104">Code loaded into this context can only be examined; it cannot be executed.</span></span> <span data-ttu-id="93eab-105">To znamená, že objekty nelze vytvořit, protože nelze provést konstruktory.</span><span class="sxs-lookup"><span data-stu-id="93eab-105">This means that objects cannot be created, because constructors cannot be executed.</span></span> <span data-ttu-id="93eab-106">Vzhledem k tomu, že kód nelze provést, závislosti nejsou automaticky načteny.</span><span class="sxs-lookup"><span data-stu-id="93eab-106">Because the code cannot be executed, dependencies are not automatically loaded.</span></span> <span data-ttu-id="93eab-107">Pokud je potřebujete ověřit, musíte je načíst sami.</span><span class="sxs-lookup"><span data-stu-id="93eab-107">If you need to examine them, you must load them yourself.</span></span>

## <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a><span data-ttu-id="93eab-108">Načtení sestavení do kontextu načtení pouze pro reflexi</span><span class="sxs-lookup"><span data-stu-id="93eab-108">To load an assembly into the reflection-only load context</span></span>

1. <span data-ttu-id="93eab-109">K načtení sestavení podle jeho zobrazovaného názvu použijte přetížení <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metody,nebometodupronačtenísestavení,kterédanoucestuzadala.<xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29></span><span class="sxs-lookup"><span data-stu-id="93eab-109">Use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> method overload to load the assembly given its display name, or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> method to load the assembly given its path.</span></span> <span data-ttu-id="93eab-110">Pokud je sestavení binární image, použijte <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="93eab-110">If the assembly is a binary image, use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> method overload.</span></span>

    > [!NOTE]
    > <span data-ttu-id="93eab-111">Kontext pouze pro reflexi nelze použít pro načtení verze knihovny mscorlib. dll z verze .NET Framework kromě verze v kontextu spuštění.</span><span class="sxs-lookup"><span data-stu-id="93eab-111">You cannot use the reflection-only context to load a version of mscorlib.dll from a version of the .NET Framework other than the version in the execution context.</span></span>

2. <span data-ttu-id="93eab-112">Pokud sestavení obsahuje závislosti, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> metoda je nenačte.</span><span class="sxs-lookup"><span data-stu-id="93eab-112">If the assembly has dependencies, the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> method does not load them.</span></span> <span data-ttu-id="93eab-113">Pokud je potřebujete ověřit, musíte je načíst sami.</span><span class="sxs-lookup"><span data-stu-id="93eab-113">If you need to examine them, you must load them yourself.</span></span>

3. <span data-ttu-id="93eab-114">Určete, zda je sestavení načteno do kontextu pouze pro reflexi pomocí <xref:System.Reflection.Assembly.ReflectionOnly%2A> vlastnosti sestavení.</span><span class="sxs-lookup"><span data-stu-id="93eab-114">Determine whether an assembly is loaded into the reflection-only context by using the assembly's <xref:System.Reflection.Assembly.ReflectionOnly%2A> property.</span></span>

4. <span data-ttu-id="93eab-115">Pokud byly atributy použity na sestavení nebo na typy v sestavení, zkontrolujte tyto atributy pomocí <xref:System.Reflection.CustomAttributeData> třídy, aby se zajistilo, že není proveden žádný pokus o spuštění kódu v kontextu pouze pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="93eab-115">If attributes have been applied to the assembly or to types in the assembly, examine those attributes by using the <xref:System.Reflection.CustomAttributeData> class to ensure that no attempt is made to execute code in the reflection-only context.</span></span> <span data-ttu-id="93eab-116">Použijte příslušné přetížení <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metody pro získání <xref:System.Reflection.CustomAttributeData> objektů představujících atributy použité pro sestavení, člena, modul nebo parametr.</span><span class="sxs-lookup"><span data-stu-id="93eab-116">Use the appropriate overload of the <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method to obtain <xref:System.Reflection.CustomAttributeData> objects representing the attributes applied to an assembly, member, module, or parameter.</span></span>

    > [!NOTE]
    > <span data-ttu-id="93eab-117">Atributy použité pro sestavení nebo jejich obsah mohou být definovány v sestavení nebo mohou být definovány v jiném sestavení načteno do kontextu pouze pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="93eab-117">Attributes applied to the assembly or to its contents might be defined in the assembly, or they might be defined in another assembly loaded into the reflection-only context.</span></span> <span data-ttu-id="93eab-118">Neexistuje žádný způsob, jak sdělit předem, kde jsou definovány atributy.</span><span class="sxs-lookup"><span data-stu-id="93eab-118">There is no way to tell in advance where the attributes are defined.</span></span>

## <a name="example"></a><span data-ttu-id="93eab-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="93eab-119">Example</span></span>

<span data-ttu-id="93eab-120">Následující příklad kódu ukazuje, jak ověřit atributy použité pro sestavení načtené do kontextu pouze pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="93eab-120">The following code example shows how to examine the attributes applied to an assembly loaded into the reflection-only context.</span></span>

<span data-ttu-id="93eab-121">Příklad kódu definuje vlastní atribut se dvěma konstruktory a jednou vlastností.</span><span class="sxs-lookup"><span data-stu-id="93eab-121">The code example defines a custom attribute with two constructors and one property.</span></span> <span data-ttu-id="93eab-122">Atribut se aplikuje na sestavení, na typ deklarovaný v sestavení, na metodu typu a na parametr metody.</span><span class="sxs-lookup"><span data-stu-id="93eab-122">The attribute is applied to the assembly, to a type declared in the assembly, to a method of the type, and to a parameter of the method.</span></span> <span data-ttu-id="93eab-123">Po spuštění sestavení se načte do kontextu pouze pro reflexi a zobrazí informace o vlastních atributech, které byly na něj aplikovány, a o typech a členech, které obsahuje.</span><span class="sxs-lookup"><span data-stu-id="93eab-123">When executed, the assembly loads itself into the reflection-only context and displays information about the custom attributes that were applied to it and to the types and members it contains.</span></span>

> [!NOTE]
> <span data-ttu-id="93eab-124">Pro zjednodušení příkladu kódu sestavení načítá a kontroluje sám sebe.</span><span class="sxs-lookup"><span data-stu-id="93eab-124">To simplify the code example, the assembly loads and examines itself.</span></span> <span data-ttu-id="93eab-125">Za normálních okolností neočekáváte, aby bylo stejné sestavení načteno do kontextu spuštění i kontextu pouze pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="93eab-125">Normally, you would not expect to find the same assembly loaded into both the execution context and the reflection-only context.</span></span>

[!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
[!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
[!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]

## <a name="see-also"></a><span data-ttu-id="93eab-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93eab-126">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- <xref:System.Reflection.Assembly.ReflectionOnly%2A>
- <xref:System.Reflection.CustomAttributeData>
