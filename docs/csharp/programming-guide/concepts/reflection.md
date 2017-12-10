---
title: Reflexe (C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 68a586fd8a8a8fbe6e351efa3e51c5ba1d2ff4d7
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="reflection-c"></a><span data-ttu-id="aa03e-102">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="aa03e-102">Reflection (C#)</span></span>
<span data-ttu-id="aa03e-103">Reflexe poskytuje objekty (typu <xref:System.Type>) popisují sestavení, moduly a typy.</span><span class="sxs-lookup"><span data-stu-id="aa03e-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="aa03e-104">Reflexe můžete dynamicky vytvořit instanci typu, typ vazby s existujícím objektem, nebo z existujícího objektu získat typ a volat její metody nebo přístup k jeho polí a vlastností.</span><span class="sxs-lookup"><span data-stu-id="aa03e-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="aa03e-105">Pokud používáte atributy ve vašem kódu, reflexe umožňuje přistupovat k nim.</span><span class="sxs-lookup"><span data-stu-id="aa03e-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="aa03e-106">Další informace najdete v tématu [atributy](../../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="aa03e-106">For more information, see [Attributes](../../../../docs/standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="aa03e-107">Zde je jednoduchý příklad použití statické metody reflexe `GetType` – zděděné z pro všechny typy `Object` základní třída - získat požadovaný typ proměnné:</span><span class="sxs-lookup"><span data-stu-id="aa03e-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 <span data-ttu-id="aa03e-108">Výstup je:</span><span class="sxs-lookup"><span data-stu-id="aa03e-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="aa03e-109">Následující příklad používá reflexe získat úplný název načíst sestavení.</span><span class="sxs-lookup"><span data-stu-id="aa03e-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```csharp  
// Using Reflection to get information from an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 <span data-ttu-id="aa03e-110">Výstup je:</span><span class="sxs-lookup"><span data-stu-id="aa03e-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  <span data-ttu-id="aa03e-111">Klíčová slova jazyka C# `protected` a `internal` mít žádný význam v IL a nepoužívají se v rozhraní API reflexe.</span><span class="sxs-lookup"><span data-stu-id="aa03e-111">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="aa03e-112">Odpovídající podmínky v IL *rodiny* a *sestavení*.</span><span class="sxs-lookup"><span data-stu-id="aa03e-112">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="aa03e-113">K identifikaci `internal` metoda pomocí reflexe, použijte <xref:System.Reflection.MethodBase.IsAssembly%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="aa03e-113">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="aa03e-114">K identifikaci `protected internal` metoda, použijte <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="aa03e-114">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>  
  
## <a name="reflection-overview"></a><span data-ttu-id="aa03e-115">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="aa03e-115">Reflection Overview</span></span>  
 <span data-ttu-id="aa03e-116">Reflexe je užitečné v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="aa03e-116">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="aa03e-117">Pokud máte přístup k atributům v metadatech vašeho programu.</span><span class="sxs-lookup"><span data-stu-id="aa03e-117">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="aa03e-118">Další informace najdete v tématu [načítání informace uložené v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="aa03e-118">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="aa03e-119">Pro zkoumání a vytváření instancí typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="aa03e-119">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="aa03e-120">Pro vytváření nových typů za běhu.</span><span class="sxs-lookup"><span data-stu-id="aa03e-120">For building new types at runtime.</span></span> <span data-ttu-id="aa03e-121">Použití třídy v <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="aa03e-121">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="aa03e-122">K provedení pozdní vazba, přístup k metody pro typy vytvořené v době běhu.</span><span class="sxs-lookup"><span data-stu-id="aa03e-122">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="aa03e-123">Podívejte se na téma [dynamické načtení a použití typů](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="aa03e-123">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aa03e-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="aa03e-124">Related Sections</span></span>  
 <span data-ttu-id="aa03e-125">Další informace:</span><span class="sxs-lookup"><span data-stu-id="aa03e-125">For more information:</span></span>  
  
-   [<span data-ttu-id="aa03e-126">Reflexe</span><span class="sxs-lookup"><span data-stu-id="aa03e-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="aa03e-127">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="aa03e-127">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="aa03e-128">Reflexe a obecné typy</span><span class="sxs-lookup"><span data-stu-id="aa03e-128">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="aa03e-129">Načítání informací uložených v atributech</span><span class="sxs-lookup"><span data-stu-id="aa03e-129">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="aa03e-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa03e-130">See Also</span></span>  
 [<span data-ttu-id="aa03e-131">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="aa03e-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="aa03e-132">Sestavení v modulu Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="aa03e-132">Assemblies in the Common Language Runtime</span></span>](../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
