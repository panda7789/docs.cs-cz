---
title: Reflexe (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: fc5c3f6af1a089d824289a55f6781e887b7cfc56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340434"
---
# <a name="reflection-c"></a><span data-ttu-id="e6d2a-102">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="e6d2a-102">Reflection (C#)</span></span>
<span data-ttu-id="e6d2a-103">Reflexe poskytuje objekty (typu <xref:System.Type>) popisují sestavení, moduly a typy.</span><span class="sxs-lookup"><span data-stu-id="e6d2a-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="e6d2a-104">Reflexe můžete dynamicky vytvořit instanci typu, typ vazby s existujícím objektem, nebo z existujícího objektu získat typ a volat její metody nebo přístup k jeho polí a vlastností.</span><span class="sxs-lookup"><span data-stu-id="e6d2a-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="e6d2a-105">Pokud používáte atributy ve vašem kódu, reflexe umožňuje přistupovat k nim.</span><span class="sxs-lookup"><span data-stu-id="e6d2a-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="e6d2a-106">Další informace najdete v tématu [atributy](../../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="e6d2a-106">For more information, see [Attributes](../../../../docs/standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="e6d2a-107">Zde je jednoduchý příklad použití statické metody reflexe `GetType` – zděděné z pro všechny typy `Object` základní třída - získat požadovaný typ proměnné:</span><span class="sxs-lookup"><span data-stu-id="e6d2a-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 <span data-ttu-id="e6d2a-108">Výstup je:</span><span class="sxs-lookup"><span data-stu-id="e6d2a-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="e6d2a-109">Následující příklad používá reflexe získat úplný název načíst sestavení.</span><span class="sxs-lookup"><span data-stu-id="e6d2a-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```csharp  
// Using Reflection to get information from an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 <span data-ttu-id="e6d2a-110">Výstup je:</span><span class="sxs-lookup"><span data-stu-id="e6d2a-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  <span data-ttu-id="e6d2a-111">Klíčová slova jazyka C# `protected` a `internal` mít žádný význam v IL a nepoužívají se v rozhraní API reflexe.</span><span class="sxs-lookup"><span data-stu-id="e6d2a-111">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="e6d2a-112">Odpovídající podmínky v IL *rodiny* a *sestavení*.</span><span class="sxs-lookup"><span data-stu-id="e6d2a-112">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="e6d2a-113">K identifikaci `internal` metoda pomocí reflexe, použijte <xref:System.Reflection.MethodBase.IsAssembly%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e6d2a-113">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="e6d2a-114">K identifikaci `protected internal` metoda, použijte <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6d2a-114">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>  
  
## <a name="reflection-overview"></a><span data-ttu-id="e6d2a-115">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="e6d2a-115">Reflection Overview</span></span>  
 <span data-ttu-id="e6d2a-116">Reflexe je užitečné v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="e6d2a-116">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="e6d2a-117">Pokud máte přístup k atributům v metadatech vašeho programu.</span><span class="sxs-lookup"><span data-stu-id="e6d2a-117">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="e6d2a-118">Další informace najdete v tématu [načítání informace uložené v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="e6d2a-118">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="e6d2a-119">Pro zkoumání a vytváření instancí typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="e6d2a-119">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="e6d2a-120">Pro vytváření nových typů za běhu.</span><span class="sxs-lookup"><span data-stu-id="e6d2a-120">For building new types at runtime.</span></span> <span data-ttu-id="e6d2a-121">Použití třídy v <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="e6d2a-121">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="e6d2a-122">K provedení pozdní vazba, přístup k metody pro typy vytvořené v době běhu.</span><span class="sxs-lookup"><span data-stu-id="e6d2a-122">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="e6d2a-123">Podívejte se na téma [dynamické načtení a použití typů](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="e6d2a-123">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e6d2a-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="e6d2a-124">Related Sections</span></span>  
 <span data-ttu-id="e6d2a-125">Další informace:</span><span class="sxs-lookup"><span data-stu-id="e6d2a-125">For more information:</span></span>  
  
-   [<span data-ttu-id="e6d2a-126">Reflexe</span><span class="sxs-lookup"><span data-stu-id="e6d2a-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="e6d2a-127">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="e6d2a-127">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="e6d2a-128">Reflexe a obecné typy</span><span class="sxs-lookup"><span data-stu-id="e6d2a-128">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="e6d2a-129">Načítání informací uložených v atributech</span><span class="sxs-lookup"><span data-stu-id="e6d2a-129">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="e6d2a-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6d2a-130">See Also</span></span>  
 [<span data-ttu-id="e6d2a-131">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e6d2a-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e6d2a-132">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="e6d2a-132">Assemblies in the Common Language Runtime</span></span>](../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
