---
title: Reflexe (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: a56fb24b63e4d80dbb67b079466b67cd11672023
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74711665"
---
# <a name="reflection-c"></a><span data-ttu-id="b5ae9-102">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="b5ae9-102">Reflection (C#)</span></span>

<span data-ttu-id="b5ae9-103">Reflexe poskytuje objekty (typu), <xref:System.Type>které popisují sestavení, moduly a typy.</span><span class="sxs-lookup"><span data-stu-id="b5ae9-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules, and types.</span></span> <span data-ttu-id="b5ae9-104">Reflexe můžete použít k dynamickému vytvoření instance typu, svázání typu s existujícím objektem nebo získání typu z existujícího objektu a vyvolání jeho metod nebo přístupu k jeho polím a vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="b5ae9-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="b5ae9-105">Pokud používáte atributy v kódu, reflexe umožňuje přístup k nim.</span><span class="sxs-lookup"><span data-stu-id="b5ae9-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="b5ae9-106">Další informace naleznete v [tématu Atributy](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="b5ae9-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>

<span data-ttu-id="b5ae9-107">Zde je jednoduchý příklad reflexe <xref:System.Object.GetType> pomocí metody - zděděné všemi typy ze `Object` základní třídy - chcete-li získat typ proměnné:</span><span class="sxs-lookup"><span data-stu-id="b5ae9-107">Here's a simple example of reflection using the <xref:System.Object.GetType> method - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>

> [!NOTE]
> <span data-ttu-id="b5ae9-108">Ujistěte se, že přidáte `using System;` a `using System.Reflection;` v horní části souboru *.cs.*</span><span class="sxs-lookup"><span data-stu-id="b5ae9-108">Make sure you add `using System;` and `using System.Reflection;` at the top of your *.cs* file.</span></span>

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

<span data-ttu-id="b5ae9-109">Výstup je: `System.Int32`.</span><span class="sxs-lookup"><span data-stu-id="b5ae9-109">The output is: `System.Int32`.</span></span>

<span data-ttu-id="b5ae9-110">Následující příklad používá reflexe k získání úplného názvu načteného sestavení.</span><span class="sxs-lookup"><span data-stu-id="b5ae9-110">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

<span data-ttu-id="b5ae9-111">Výstup je: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span><span class="sxs-lookup"><span data-stu-id="b5ae9-111">The output is: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span></span>

> [!NOTE]
> <span data-ttu-id="b5ae9-112">C# klíčová `protected` slova `internal` a nemají žádný význam v IL a nejsou použity v reflexi API.</span><span class="sxs-lookup"><span data-stu-id="b5ae9-112">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="b5ae9-113">Odpovídající termíny v IL jsou *rodina* a *sestavení*.</span><span class="sxs-lookup"><span data-stu-id="b5ae9-113">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="b5ae9-114">Chcete-li `internal` identifikovat metodu <xref:System.Reflection.MethodBase.IsAssembly%2A> pomocí reflexe, použijte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b5ae9-114">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="b5ae9-115">Chcete-li `protected internal` identifikovat metodu, použijte <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="b5ae9-115">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>

## <a name="reflection-overview"></a><span data-ttu-id="b5ae9-116">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="b5ae9-116">Reflection overview</span></span>

<span data-ttu-id="b5ae9-117">Reflexe je užitečná v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="b5ae9-117">Reflection is useful in the following situations:</span></span>

- <span data-ttu-id="b5ae9-118">Pokud máte přístup k atributům v metadatech programu.</span><span class="sxs-lookup"><span data-stu-id="b5ae9-118">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="b5ae9-119">Další informace naleznete v [tématu Načítání informací uložených v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b5ae9-119">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>
- <span data-ttu-id="b5ae9-120">Pro zkoumání a vytváření konkretistů typů v sestavení.</span><span class="sxs-lookup"><span data-stu-id="b5ae9-120">For examining and instantiating types in an assembly.</span></span>
- <span data-ttu-id="b5ae9-121">Pro vytváření nových typů za běhu.</span><span class="sxs-lookup"><span data-stu-id="b5ae9-121">For building new types at runtime.</span></span> <span data-ttu-id="b5ae9-122">Použití tříd <xref:System.Reflection.Emit>v .</span><span class="sxs-lookup"><span data-stu-id="b5ae9-122">Use classes in <xref:System.Reflection.Emit>.</span></span>
- <span data-ttu-id="b5ae9-123">Pro provádění pozdní vazby, přístup k metodám na typy vytvořené v době běhu.</span><span class="sxs-lookup"><span data-stu-id="b5ae9-123">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="b5ae9-124">Podívejte se na téma [Dynamicky načítání a používání typů](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="b5ae9-124">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>

## <a name="related-sections"></a><span data-ttu-id="b5ae9-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b5ae9-125">Related sections</span></span>

<span data-ttu-id="b5ae9-126">Další informace najdete tady:</span><span class="sxs-lookup"><span data-stu-id="b5ae9-126">For more information:</span></span>

- [<span data-ttu-id="b5ae9-127">Reflexe</span><span class="sxs-lookup"><span data-stu-id="b5ae9-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="b5ae9-128">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="b5ae9-128">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="b5ae9-129">Reflexe a obecné typy</span><span class="sxs-lookup"><span data-stu-id="b5ae9-129">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [<span data-ttu-id="b5ae9-130">Načítání informací uložených v atributech</span><span class="sxs-lookup"><span data-stu-id="b5ae9-130">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a><span data-ttu-id="b5ae9-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5ae9-131">See also</span></span>

- [<span data-ttu-id="b5ae9-132">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b5ae9-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b5ae9-133">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="b5ae9-133">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
