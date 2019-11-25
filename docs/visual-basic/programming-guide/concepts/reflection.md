---
title: Reflexe
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: 28f33c88f7aaaf51938a7d27fd2218a97b628acd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349271"
---
# <a name="reflection-visual-basic"></a><span data-ttu-id="65ea6-102">Reflection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65ea6-102">Reflection (Visual Basic)</span></span>
<span data-ttu-id="65ea6-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span><span class="sxs-lookup"><span data-stu-id="65ea6-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="65ea6-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span><span class="sxs-lookup"><span data-stu-id="65ea6-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="65ea6-105">If you are using attributes in your code, reflection enables you to access them.</span><span class="sxs-lookup"><span data-stu-id="65ea6-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="65ea6-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="65ea6-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="65ea6-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span><span class="sxs-lookup"><span data-stu-id="65ea6-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="65ea6-108">The output is:</span><span class="sxs-lookup"><span data-stu-id="65ea6-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="65ea6-109">The following example uses reflection to obtain the full name of the loaded assembly.</span><span class="sxs-lookup"><span data-stu-id="65ea6-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="65ea6-110">The output is:</span><span class="sxs-lookup"><span data-stu-id="65ea6-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="65ea6-111">Reflection Overview</span><span class="sxs-lookup"><span data-stu-id="65ea6-111">Reflection Overview</span></span>  
 <span data-ttu-id="65ea6-112">Reflection is useful in the following situations:</span><span class="sxs-lookup"><span data-stu-id="65ea6-112">Reflection is useful in the following situations:</span></span>  
  
- <span data-ttu-id="65ea6-113">When you have to access attributes in your program's metadata.</span><span class="sxs-lookup"><span data-stu-id="65ea6-113">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="65ea6-114">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="65ea6-114">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
- <span data-ttu-id="65ea6-115">For examining and instantiating types in an assembly.</span><span class="sxs-lookup"><span data-stu-id="65ea6-115">For examining and instantiating types in an assembly.</span></span>  
  
- <span data-ttu-id="65ea6-116">For building new types at runtime.</span><span class="sxs-lookup"><span data-stu-id="65ea6-116">For building new types at runtime.</span></span> <span data-ttu-id="65ea6-117">Use classes in <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="65ea6-117">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
- <span data-ttu-id="65ea6-118">For performing late binding, accessing methods on types created at run time.</span><span class="sxs-lookup"><span data-stu-id="65ea6-118">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="65ea6-119">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="65ea6-119">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="65ea6-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="65ea6-120">Related Sections</span></span>  
 <span data-ttu-id="65ea6-121">Další informace:</span><span class="sxs-lookup"><span data-stu-id="65ea6-121">For more information:</span></span>  
  
- [<span data-ttu-id="65ea6-122">Reflexe</span><span class="sxs-lookup"><span data-stu-id="65ea6-122">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
- [<span data-ttu-id="65ea6-123">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="65ea6-123">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [<span data-ttu-id="65ea6-124">Reflexe a obecné typy</span><span class="sxs-lookup"><span data-stu-id="65ea6-124">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [<span data-ttu-id="65ea6-125">Načítání informací uložených v atributech</span><span class="sxs-lookup"><span data-stu-id="65ea6-125">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="65ea6-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65ea6-126">See also</span></span>

- [<span data-ttu-id="65ea6-127">Visual Basic Programming Guide</span><span class="sxs-lookup"><span data-stu-id="65ea6-127">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="65ea6-128">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="65ea6-128">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
