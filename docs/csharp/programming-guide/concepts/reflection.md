---
title: Reflexe (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 8cdfe00a09d340d8b77f1f5582a3a3ad82c496b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537644"
---
# <a name="reflection-c"></a><span data-ttu-id="674fd-102">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="674fd-102">Reflection (C#)</span></span>
<span data-ttu-id="674fd-103">Reflexe poskytuje objekty (typu <xref:System.Type>), které popisují sestavení, modulů a typů.</span><span class="sxs-lookup"><span data-stu-id="674fd-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="674fd-104">Vám pomůže odrazu dynamicky vytvořit instanci typu, navázat na existující objekt, nebo získat typ z existujícího objektu a volat jeho metody nebo přístup k vlastnostem a polím.</span><span class="sxs-lookup"><span data-stu-id="674fd-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="674fd-105">Pokud používáte atributy ve vašem kódu, reflexe umožňuje přistupovat k nim.</span><span class="sxs-lookup"><span data-stu-id="674fd-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="674fd-106">Další informace najdete v tématu [atributy](../../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="674fd-106">For more information, see [Attributes](../../../../docs/standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="674fd-107">Tady je jednoduchý příklad použití statické metody reflexe `GetType` – zděděný všechny typy z `Object` základní třídy – získat typ proměnné:</span><span class="sxs-lookup"><span data-stu-id="674fd-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 <span data-ttu-id="674fd-108">Výstup bude:</span><span class="sxs-lookup"><span data-stu-id="674fd-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="674fd-109">Následující příklad používá reflexi získat úplný název načteného sestavení.</span><span class="sxs-lookup"><span data-stu-id="674fd-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```csharp  
// Using Reflection to get information from an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 <span data-ttu-id="674fd-110">Výstup bude:</span><span class="sxs-lookup"><span data-stu-id="674fd-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  <span data-ttu-id="674fd-111">Klíčová slova jazyka C# `protected` a `internal` nemají význam IL a nepoužívají se v rozhraní API reflexe.</span><span class="sxs-lookup"><span data-stu-id="674fd-111">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="674fd-112">Odpovídající výrazy v IL jsou *řady* a *sestavení*.</span><span class="sxs-lookup"><span data-stu-id="674fd-112">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="674fd-113">K identifikaci `internal` pomocí reflexe, použijte metodu <xref:System.Reflection.MethodBase.IsAssembly%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="674fd-113">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="674fd-114">K identifikaci `protected internal` metody, použijte <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="674fd-114">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>  
  
## <a name="reflection-overview"></a><span data-ttu-id="674fd-115">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="674fd-115">Reflection Overview</span></span>  
 <span data-ttu-id="674fd-116">Reflexe je užitečná v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="674fd-116">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="674fd-117">Pokud máte přístup k atributům v metadatech váš program.</span><span class="sxs-lookup"><span data-stu-id="674fd-117">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="674fd-118">Další informace najdete v tématu [načítání informací uložených v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="674fd-118">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="674fd-119">Pro prozkoumání a vytvoření instance typů v sestavení.</span><span class="sxs-lookup"><span data-stu-id="674fd-119">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="674fd-120">Pro vytváření nových typů v době běhu.</span><span class="sxs-lookup"><span data-stu-id="674fd-120">For building new types at runtime.</span></span> <span data-ttu-id="674fd-121">Použití tříd v <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="674fd-121">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="674fd-122">Pro provádění pozdní vazby, přístup k metodám na typy vytvořené v době běhu.</span><span class="sxs-lookup"><span data-stu-id="674fd-122">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="674fd-123">Naleznete v tématu [dynamické načtení a použití typů](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="674fd-123">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="674fd-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="674fd-124">Related Sections</span></span>  
 <span data-ttu-id="674fd-125">Další informace:</span><span class="sxs-lookup"><span data-stu-id="674fd-125">For more information:</span></span>  
  
-   [<span data-ttu-id="674fd-126">Reflexe</span><span class="sxs-lookup"><span data-stu-id="674fd-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="674fd-127">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="674fd-127">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="674fd-128">Reflexe a obecné typy</span><span class="sxs-lookup"><span data-stu-id="674fd-128">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="674fd-129">Načítání informací uložených v atributech</span><span class="sxs-lookup"><span data-stu-id="674fd-129">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="674fd-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="674fd-130">See also</span></span>

- [<span data-ttu-id="674fd-131">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="674fd-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="674fd-132">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="674fd-132">Assemblies in the Common Language Runtime</span></span>](../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
