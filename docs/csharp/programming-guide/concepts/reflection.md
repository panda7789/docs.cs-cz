---
title: Reflexe (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: a56fb24b63e4d80dbb67b079466b67cd11672023
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711665"
---
# <a name="reflection-c"></a><span data-ttu-id="ca700-102">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="ca700-102">Reflection (C#)</span></span>

<span data-ttu-id="ca700-103">Reflexe poskytuje objekty (typu <xref:System.Type>), které popisují sestavení, moduly a typy.</span><span class="sxs-lookup"><span data-stu-id="ca700-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules, and types.</span></span> <span data-ttu-id="ca700-104">Můžete použít reflexi k dynamickému vytvoření instance typu, svázání typu s existujícím objektem nebo získat typ z existujícího objektu a vyvolat jeho metody nebo získat přístup k jeho polím a vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="ca700-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="ca700-105">Pokud používáte atributy v kódu, reflexe vám umožní přístup k nim.</span><span class="sxs-lookup"><span data-stu-id="ca700-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="ca700-106">Další informace najdete v tématu [atributy](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="ca700-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>

<span data-ttu-id="ca700-107">Tady je jednoduchý příklad reflexe pomocí metody <xref:System.Object.GetType> – zděděné všemi typy ze `Object` základní třídy – pro získání typu proměnné:</span><span class="sxs-lookup"><span data-stu-id="ca700-107">Here's a simple example of reflection using the <xref:System.Object.GetType> method - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>

> [!NOTE]
> <span data-ttu-id="ca700-108">Ujistěte se, že jste přidali `using System;` a `using System.Reflection;` v horní části souboru *. cs* .</span><span class="sxs-lookup"><span data-stu-id="ca700-108">Make sure you add `using System;` and `using System.Reflection;` at the top of your *.cs* file.</span></span>

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

<span data-ttu-id="ca700-109">Výstup je: `System.Int32`.</span><span class="sxs-lookup"><span data-stu-id="ca700-109">The output is: `System.Int32`.</span></span>

<span data-ttu-id="ca700-110">Následující příklad používá reflexi k získání úplného názvu načteného sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca700-110">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

<span data-ttu-id="ca700-111">Výstup je: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span><span class="sxs-lookup"><span data-stu-id="ca700-111">The output is: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span></span>

> [!NOTE]
> <span data-ttu-id="ca700-112">C# Klíčová slova `protected` a `internal` nemají význam v Il a nejsou použity v rozhraních API reflexe.</span><span class="sxs-lookup"><span data-stu-id="ca700-112">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="ca700-113">Odpovídající výrazy v IL jsou *rodina* a *sestavení*.</span><span class="sxs-lookup"><span data-stu-id="ca700-113">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="ca700-114">Chcete-li identifikovat metodu `internal` pomocí reflexe, použijte vlastnost <xref:System.Reflection.MethodBase.IsAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="ca700-114">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="ca700-115">K identifikaci `protected internal` metody použijte <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="ca700-115">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>

## <a name="reflection-overview"></a><span data-ttu-id="ca700-116">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="ca700-116">Reflection overview</span></span>

<span data-ttu-id="ca700-117">Reflexe je užitečná v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="ca700-117">Reflection is useful in the following situations:</span></span>

- <span data-ttu-id="ca700-118">Pokud budete mít přístup k atributům v metadatech vašeho programu.</span><span class="sxs-lookup"><span data-stu-id="ca700-118">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="ca700-119">Další informace najdete v tématu [načítání informací uložených v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="ca700-119">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>
- <span data-ttu-id="ca700-120">Pro zkoumání a vytváření instancí typů v sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca700-120">For examining and instantiating types in an assembly.</span></span>
- <span data-ttu-id="ca700-121">Pro vytváření nových typů za běhu.</span><span class="sxs-lookup"><span data-stu-id="ca700-121">For building new types at runtime.</span></span> <span data-ttu-id="ca700-122">Použijte třídy v <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="ca700-122">Use classes in <xref:System.Reflection.Emit>.</span></span>
- <span data-ttu-id="ca700-123">Pro provádění pozdní vazby získáte přístup k metodám typů vytvořeným v době běhu.</span><span class="sxs-lookup"><span data-stu-id="ca700-123">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="ca700-124">Viz téma [Dynamické načítání a používání typů](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="ca700-124">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>

## <a name="related-sections"></a><span data-ttu-id="ca700-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ca700-125">Related sections</span></span>

<span data-ttu-id="ca700-126">Další informace:</span><span class="sxs-lookup"><span data-stu-id="ca700-126">For more information:</span></span>

- [<span data-ttu-id="ca700-127">Reflexe</span><span class="sxs-lookup"><span data-stu-id="ca700-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="ca700-128">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="ca700-128">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="ca700-129">Reflexe a obecné typy</span><span class="sxs-lookup"><span data-stu-id="ca700-129">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [<span data-ttu-id="ca700-130">Načítání informací uložených v atributech</span><span class="sxs-lookup"><span data-stu-id="ca700-130">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a><span data-ttu-id="ca700-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca700-131">See also</span></span>

- [<span data-ttu-id="ca700-132">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ca700-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ca700-133">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="ca700-133">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
