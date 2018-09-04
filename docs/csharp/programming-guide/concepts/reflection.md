---
title: Reflexe (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: d04fb15add465d0a04ac6b38b1c47aa408c81eaa
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521669"
---
# <a name="reflection-c"></a><span data-ttu-id="a2559-102">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="a2559-102">Reflection (C#)</span></span>
<span data-ttu-id="a2559-103">Reflexe poskytuje objekty (typu <xref:System.Type>), které popisují sestavení, modulů a typů.</span><span class="sxs-lookup"><span data-stu-id="a2559-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="a2559-104">Vám pomůže odrazu dynamicky vytvořit instanci typu, navázat na existující objekt, nebo získat typ z existujícího objektu a volat jeho metody nebo přístup k vlastnostem a polím.</span><span class="sxs-lookup"><span data-stu-id="a2559-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="a2559-105">Pokud používáte atributy ve vašem kódu, reflexe umožňuje přistupovat k nim.</span><span class="sxs-lookup"><span data-stu-id="a2559-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="a2559-106">Další informace najdete v tématu [atributy](../../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="a2559-106">For more information, see [Attributes](../../../../docs/standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="a2559-107">Tady je jednoduchý příklad použití statické metody reflexe `GetType` – zděděný všechny typy z `Object` základní třídy – získat typ proměnné:</span><span class="sxs-lookup"><span data-stu-id="a2559-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 <span data-ttu-id="a2559-108">Výstup bude:</span><span class="sxs-lookup"><span data-stu-id="a2559-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="a2559-109">Následující příklad používá reflexi získat úplný název načteného sestavení.</span><span class="sxs-lookup"><span data-stu-id="a2559-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```csharp  
// Using Reflection to get information from an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 <span data-ttu-id="a2559-110">Výstup bude:</span><span class="sxs-lookup"><span data-stu-id="a2559-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  <span data-ttu-id="a2559-111">Klíčová slova jazyka C# `protected` a `internal` nemají význam IL a nepoužívají se v rozhraní API reflexe.</span><span class="sxs-lookup"><span data-stu-id="a2559-111">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="a2559-112">Odpovídající výrazy v IL jsou *řady* a *sestavení*.</span><span class="sxs-lookup"><span data-stu-id="a2559-112">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="a2559-113">K identifikaci `internal` pomocí reflexe, použijte metodu <xref:System.Reflection.MethodBase.IsAssembly%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a2559-113">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="a2559-114">K identifikaci `protected internal` metody, použijte <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2559-114">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>  
  
## <a name="reflection-overview"></a><span data-ttu-id="a2559-115">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="a2559-115">Reflection Overview</span></span>  
 <span data-ttu-id="a2559-116">Reflexe je užitečná v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="a2559-116">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="a2559-117">Pokud máte přístup k atributům v metadatech váš program.</span><span class="sxs-lookup"><span data-stu-id="a2559-117">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="a2559-118">Další informace najdete v tématu [načítání informací uložených v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a2559-118">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="a2559-119">Pro prozkoumání a vytvoření instance typů v sestavení.</span><span class="sxs-lookup"><span data-stu-id="a2559-119">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="a2559-120">Pro vytváření nových typů v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a2559-120">For building new types at runtime.</span></span> <span data-ttu-id="a2559-121">Použití tříd v <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="a2559-121">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="a2559-122">Pro provádění pozdní vazby, přístup k metodám na typy vytvořené v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a2559-122">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="a2559-123">Naleznete v tématu [dynamické načtení a použití typů](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="a2559-123">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a2559-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a2559-124">Related Sections</span></span>  
 <span data-ttu-id="a2559-125">Další informace:</span><span class="sxs-lookup"><span data-stu-id="a2559-125">For more information:</span></span>  
  
-   [<span data-ttu-id="a2559-126">Reflexe</span><span class="sxs-lookup"><span data-stu-id="a2559-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="a2559-127">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="a2559-127">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="a2559-128">Reflexe a obecné typy</span><span class="sxs-lookup"><span data-stu-id="a2559-128">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="a2559-129">Načítání informací uložených v atributech</span><span class="sxs-lookup"><span data-stu-id="a2559-129">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="a2559-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2559-130">See Also</span></span>

- [<span data-ttu-id="a2559-131">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a2559-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a2559-132">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="a2559-132">Assemblies in the Common Language Runtime</span></span>](../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
