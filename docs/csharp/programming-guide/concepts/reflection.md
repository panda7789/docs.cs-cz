---
title: Reflexe (C#)
description: Reflexe poskytuje objekty, které popisují sestavení, moduly a typy v jazyce C#. Pokud váš kód obsahuje atributy, reflexe vám umožní přístup k nim.
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 4d4f4c082dd2d58e212bae53524e5dd4fd06fb75
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302799"
---
# <a name="reflection-c"></a><span data-ttu-id="b5204-104">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="b5204-104">Reflection (C#)</span></span>

<span data-ttu-id="b5204-105">Reflexe poskytuje objekty (typu <xref:System.Type> ), které popisují sestavení, moduly a typy.</span><span class="sxs-lookup"><span data-stu-id="b5204-105">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules, and types.</span></span> <span data-ttu-id="b5204-106">Můžete použít reflexi k dynamickému vytvoření instance typu, svázání typu s existujícím objektem nebo získat typ z existujícího objektu a vyvolat jeho metody nebo získat přístup k jeho polím a vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="b5204-106">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="b5204-107">Pokud používáte atributy v kódu, reflexe vám umožní přístup k nim.</span><span class="sxs-lookup"><span data-stu-id="b5204-107">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="b5204-108">Další informace najdete v tématu [atributy](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="b5204-108">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>

<span data-ttu-id="b5204-109">Tady je jednoduchý příklad reflexe pomocí <xref:System.Object.GetType> metody zděděné všemi typy ze `Object` základní třídy – pro získání typu proměnné:</span><span class="sxs-lookup"><span data-stu-id="b5204-109">Here's a simple example of reflection using the <xref:System.Object.GetType> method - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>

> [!NOTE]
> <span data-ttu-id="b5204-110">Ujistěte se, že jste přidali `using System;` a `using System.Reflection;` v horní části souboru *. cs* .</span><span class="sxs-lookup"><span data-stu-id="b5204-110">Make sure you add `using System;` and `using System.Reflection;` at the top of your *.cs* file.</span></span>

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

<span data-ttu-id="b5204-111">Výstup je: `System.Int32` .</span><span class="sxs-lookup"><span data-stu-id="b5204-111">The output is: `System.Int32`.</span></span>

<span data-ttu-id="b5204-112">Následující příklad používá reflexi k získání úplného názvu načteného sestavení.</span><span class="sxs-lookup"><span data-stu-id="b5204-112">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

<span data-ttu-id="b5204-113">Výstup je: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e` .</span><span class="sxs-lookup"><span data-stu-id="b5204-113">The output is: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span></span>

> [!NOTE]
> <span data-ttu-id="b5204-114">Klíčová slova jazyka C# `protected` a `internal` nemají žádný význam v Il a nejsou použity v rozhraních API reflexe.</span><span class="sxs-lookup"><span data-stu-id="b5204-114">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="b5204-115">Odpovídající výrazy v IL jsou *rodina* a *sestavení*.</span><span class="sxs-lookup"><span data-stu-id="b5204-115">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="b5204-116">K identifikaci `internal` metody pomocí reflexe použijte <xref:System.Reflection.MethodBase.IsAssembly%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b5204-116">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="b5204-117">K identifikaci `protected internal` metody použijte <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A> .</span><span class="sxs-lookup"><span data-stu-id="b5204-117">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>

## <a name="reflection-overview"></a><span data-ttu-id="b5204-118">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="b5204-118">Reflection overview</span></span>

<span data-ttu-id="b5204-119">Reflexe je užitečná v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="b5204-119">Reflection is useful in the following situations:</span></span>

- <span data-ttu-id="b5204-120">Pokud budete mít přístup k atributům v metadatech vašeho programu.</span><span class="sxs-lookup"><span data-stu-id="b5204-120">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="b5204-121">Další informace najdete v tématu [načítání informací uložených v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b5204-121">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>
- <span data-ttu-id="b5204-122">Pro zkoumání a vytváření instancí typů v sestavení.</span><span class="sxs-lookup"><span data-stu-id="b5204-122">For examining and instantiating types in an assembly.</span></span>
- <span data-ttu-id="b5204-123">Pro vytváření nových typů za běhu.</span><span class="sxs-lookup"><span data-stu-id="b5204-123">For building new types at runtime.</span></span> <span data-ttu-id="b5204-124">Použijte třídy v <xref:System.Reflection.Emit> .</span><span class="sxs-lookup"><span data-stu-id="b5204-124">Use classes in <xref:System.Reflection.Emit>.</span></span>
- <span data-ttu-id="b5204-125">Pro provádění pozdní vazby získáte přístup k metodám typů vytvořeným v době běhu.</span><span class="sxs-lookup"><span data-stu-id="b5204-125">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="b5204-126">Viz téma [Dynamické načítání a používání typů](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="b5204-126">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>

## <a name="related-sections"></a><span data-ttu-id="b5204-127">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b5204-127">Related sections</span></span>

<span data-ttu-id="b5204-128">Další informace najdete tady:</span><span class="sxs-lookup"><span data-stu-id="b5204-128">For more information:</span></span>

- [<span data-ttu-id="b5204-129">Reflexe</span><span class="sxs-lookup"><span data-stu-id="b5204-129">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="b5204-130">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="b5204-130">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="b5204-131">Reflexe a obecné typy</span><span class="sxs-lookup"><span data-stu-id="b5204-131">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [<span data-ttu-id="b5204-132">Načítání informací uložených v atributech</span><span class="sxs-lookup"><span data-stu-id="b5204-132">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a><span data-ttu-id="b5204-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5204-133">See also</span></span>

- [<span data-ttu-id="b5204-134">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b5204-134">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b5204-135">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="b5204-135">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
