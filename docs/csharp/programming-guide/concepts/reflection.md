---
title: Reflexe (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 9b4322d83ad43cd3e49647df49c15bb5c917e1be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924094"
---
# <a name="reflection-c"></a><span data-ttu-id="76434-102">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="76434-102">Reflection (C#)</span></span>
<span data-ttu-id="76434-103">Reflexe poskytuje objekty ( <xref:System.Type>typu), které popisují sestavení, moduly a typy.</span><span class="sxs-lookup"><span data-stu-id="76434-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="76434-104">Můžete použít reflexi k dynamickému vytvoření instance typu, svázání typu s existujícím objektem nebo získat typ z existujícího objektu a vyvolat jeho metody nebo získat přístup k jeho polím a vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="76434-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="76434-105">Pokud používáte atributy v kódu, reflexe vám umožní přístup k nim.</span><span class="sxs-lookup"><span data-stu-id="76434-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="76434-106">Další informace najdete v tématu [atributy](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="76434-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="76434-107">Tady je jednoduchý příklad reflexe pomocí statické metody `GetType` – zděděné všemi typy `Object` ze základní třídy – pro získání typu proměnné:</span><span class="sxs-lookup"><span data-stu-id="76434-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 <span data-ttu-id="76434-108">Výstup je:</span><span class="sxs-lookup"><span data-stu-id="76434-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="76434-109">Následující příklad používá reflexi k získání úplného názvu načteného sestavení.</span><span class="sxs-lookup"><span data-stu-id="76434-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```csharp  
// Using Reflection to get information of an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 <span data-ttu-id="76434-110">Výstup je:</span><span class="sxs-lookup"><span data-stu-id="76434-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
> <span data-ttu-id="76434-111">C# Klíčová `protected` slova `internal` a nemají žádný význam v Il a nejsou použity v rozhraních API reflexe.</span><span class="sxs-lookup"><span data-stu-id="76434-111">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="76434-112">Odpovídající výrazy v IL jsou *rodina* a *sestavení*.</span><span class="sxs-lookup"><span data-stu-id="76434-112">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="76434-113">K identifikaci `internal` metody pomocí reflexe <xref:System.Reflection.MethodBase.IsAssembly%2A> použijte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="76434-113">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="76434-114">K identifikaci `protected internal` metody <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>použijte.</span><span class="sxs-lookup"><span data-stu-id="76434-114">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>  
  
## <a name="reflection-overview"></a><span data-ttu-id="76434-115">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="76434-115">Reflection Overview</span></span>  
 <span data-ttu-id="76434-116">Reflexe je užitečná v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="76434-116">Reflection is useful in the following situations:</span></span>  
  
- <span data-ttu-id="76434-117">Pokud budete mít přístup k atributům v metadatech vašeho programu.</span><span class="sxs-lookup"><span data-stu-id="76434-117">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="76434-118">Další informace najdete v tématu [načítání informací uložených v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="76434-118">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
- <span data-ttu-id="76434-119">Pro zkoumání a vytváření instancí typů v sestavení.</span><span class="sxs-lookup"><span data-stu-id="76434-119">For examining and instantiating types in an assembly.</span></span>  
  
- <span data-ttu-id="76434-120">Pro vytváření nových typů za běhu.</span><span class="sxs-lookup"><span data-stu-id="76434-120">For building new types at runtime.</span></span> <span data-ttu-id="76434-121">Použijte třídy v <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="76434-121">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
- <span data-ttu-id="76434-122">Pro provádění pozdní vazby získáte přístup k metodám typů vytvořeným v době běhu.</span><span class="sxs-lookup"><span data-stu-id="76434-122">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="76434-123">Viz téma [Dynamické načítání a používání typů](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="76434-123">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="76434-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="76434-124">Related Sections</span></span>  
 <span data-ttu-id="76434-125">Další informace:</span><span class="sxs-lookup"><span data-stu-id="76434-125">For more information:</span></span>  
  
- [<span data-ttu-id="76434-126">Reflexe</span><span class="sxs-lookup"><span data-stu-id="76434-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
- [<span data-ttu-id="76434-127">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="76434-127">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [<span data-ttu-id="76434-128">Reflexe a obecné typy</span><span class="sxs-lookup"><span data-stu-id="76434-128">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [<span data-ttu-id="76434-129">Načítání informací uložených v atributech</span><span class="sxs-lookup"><span data-stu-id="76434-129">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="76434-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76434-130">See also</span></span>

- [<span data-ttu-id="76434-131">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="76434-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="76434-132">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="76434-132">Assemblies in the Common Language Runtime</span></span>](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
