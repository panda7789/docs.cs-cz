---
title: Reflexe (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: 6d1206d84dec4202a7dad8f03c3d88c8a97ff5ba
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972122"
---
# <a name="reflection-visual-basic"></a><span data-ttu-id="40950-102">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40950-102">Reflection (Visual Basic)</span></span>
<span data-ttu-id="40950-103">Reflexe poskytuje objekty ( <xref:System.Type>typu), které popisují sestavení, moduly a typy.</span><span class="sxs-lookup"><span data-stu-id="40950-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="40950-104">Můžete použít reflexi k dynamickému vytvoření instance typu, svázání typu s existujícím objektem nebo získat typ z existujícího objektu a vyvolat jeho metody nebo získat přístup k jeho polím a vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="40950-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="40950-105">Pokud používáte atributy v kódu, reflexe vám umožní přístup k nim.</span><span class="sxs-lookup"><span data-stu-id="40950-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="40950-106">Další informace najdete v tématu [atributy](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="40950-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="40950-107">Tady je jednoduchý příklad reflexe pomocí statické metody `GetType` – zděděné všemi typy `Object` ze základní třídy – pro získání typu proměnné:</span><span class="sxs-lookup"><span data-stu-id="40950-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="40950-108">Výstup je:</span><span class="sxs-lookup"><span data-stu-id="40950-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="40950-109">Následující příklad používá reflexi k získání úplného názvu načteného sestavení.</span><span class="sxs-lookup"><span data-stu-id="40950-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="40950-110">Výstup je:</span><span class="sxs-lookup"><span data-stu-id="40950-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="40950-111">Přehled reflexe</span><span class="sxs-lookup"><span data-stu-id="40950-111">Reflection Overview</span></span>  
 <span data-ttu-id="40950-112">Reflexe je užitečná v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="40950-112">Reflection is useful in the following situations:</span></span>  
  
- <span data-ttu-id="40950-113">Pokud budete mít přístup k atributům v metadatech vašeho programu.</span><span class="sxs-lookup"><span data-stu-id="40950-113">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="40950-114">Další informace najdete v tématu [načítání informací uložených v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="40950-114">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
- <span data-ttu-id="40950-115">Pro zkoumání a vytváření instancí typů v sestavení.</span><span class="sxs-lookup"><span data-stu-id="40950-115">For examining and instantiating types in an assembly.</span></span>  
  
- <span data-ttu-id="40950-116">Pro vytváření nových typů za běhu.</span><span class="sxs-lookup"><span data-stu-id="40950-116">For building new types at runtime.</span></span> <span data-ttu-id="40950-117">Použijte třídy v <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="40950-117">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
- <span data-ttu-id="40950-118">Pro provádění pozdní vazby získáte přístup k metodám typů vytvořeným v době běhu.</span><span class="sxs-lookup"><span data-stu-id="40950-118">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="40950-119">Viz téma [Dynamické načítání a používání typů](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="40950-119">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="40950-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="40950-120">Related Sections</span></span>  
 <span data-ttu-id="40950-121">Další informace:</span><span class="sxs-lookup"><span data-stu-id="40950-121">For more information:</span></span>  
  
- [<span data-ttu-id="40950-122">Reflexe</span><span class="sxs-lookup"><span data-stu-id="40950-122">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
- [<span data-ttu-id="40950-123">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="40950-123">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [<span data-ttu-id="40950-124">Reflexe a obecné typy</span><span class="sxs-lookup"><span data-stu-id="40950-124">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [<span data-ttu-id="40950-125">Načítání informací uložených v atributech</span><span class="sxs-lookup"><span data-stu-id="40950-125">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="40950-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40950-126">See also</span></span>

- [<span data-ttu-id="40950-127">Průvodce programováním Visual Basic</span><span class="sxs-lookup"><span data-stu-id="40950-127">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="40950-128">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="40950-128">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
