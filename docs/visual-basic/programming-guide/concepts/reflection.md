---
title: Reflexe (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: d2ad8957d308aa98935c862ec1864b6682be904b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834878"
---
# <a name="reflection-visual-basic"></a><span data-ttu-id="516a0-102">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="516a0-102">Reflection (Visual Basic)</span></span>
<span data-ttu-id="516a0-103">Reflexe poskytuje objekty (typu <xref:System.Type>), které popisují sestavení, modulů a typů.</span><span class="sxs-lookup"><span data-stu-id="516a0-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="516a0-104">Vám pomůže odrazu dynamicky vytvořit instanci typu, navázat na existující objekt, nebo získat typ z existujícího objektu a volat jeho metody nebo přístup k vlastnostem a polím.</span><span class="sxs-lookup"><span data-stu-id="516a0-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="516a0-105">Pokud používáte atributy ve vašem kódu, reflexe umožňuje přistupovat k nim.</span><span class="sxs-lookup"><span data-stu-id="516a0-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="516a0-106">Další informace najdete v tématu [atributy](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="516a0-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="516a0-107">Tady je jednoduchý příklad použití statické metody reflexe `GetType` – zděděný všechny typy z `Object` základní třídy – získat typ proměnné:</span><span class="sxs-lookup"><span data-stu-id="516a0-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="516a0-108">Výstup bude:</span><span class="sxs-lookup"><span data-stu-id="516a0-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="516a0-109">Následující příklad používá reflexi získat úplný název načteného sestavení.</span><span class="sxs-lookup"><span data-stu-id="516a0-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="516a0-110">Výstup bude:</span><span class="sxs-lookup"><span data-stu-id="516a0-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="516a0-111">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="516a0-111">Reflection Overview</span></span>  
 <span data-ttu-id="516a0-112">Reflexe je užitečná v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="516a0-112">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="516a0-113">Pokud máte přístup k atributům v metadatech váš program.</span><span class="sxs-lookup"><span data-stu-id="516a0-113">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="516a0-114">Další informace najdete v tématu [načítání informací uložených v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="516a0-114">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="516a0-115">Pro prozkoumání a vytvoření instance typů v sestavení.</span><span class="sxs-lookup"><span data-stu-id="516a0-115">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="516a0-116">Pro vytváření nových typů v době běhu.</span><span class="sxs-lookup"><span data-stu-id="516a0-116">For building new types at runtime.</span></span> <span data-ttu-id="516a0-117">Použití tříd v <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="516a0-117">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="516a0-118">Pro provádění pozdní vazby, přístup k metodám na typy vytvořené v době běhu.</span><span class="sxs-lookup"><span data-stu-id="516a0-118">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="516a0-119">Naleznete v tématu [dynamické načtení a použití typů](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="516a0-119">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="516a0-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="516a0-120">Related Sections</span></span>  
 <span data-ttu-id="516a0-121">Další informace:</span><span class="sxs-lookup"><span data-stu-id="516a0-121">For more information:</span></span>  
  
-   [<span data-ttu-id="516a0-122">Reflexe</span><span class="sxs-lookup"><span data-stu-id="516a0-122">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="516a0-123">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="516a0-123">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="516a0-124">Reflexe a obecné typy</span><span class="sxs-lookup"><span data-stu-id="516a0-124">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="516a0-125">Načítání informací uložených v atributech</span><span class="sxs-lookup"><span data-stu-id="516a0-125">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="516a0-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="516a0-126">See also</span></span>

- [<span data-ttu-id="516a0-127">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="516a0-127">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="516a0-128">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="516a0-128">Assemblies in the Common Language Runtime</span></span>](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
