---
title: "Obecní delegáti (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1377723f18d6dd0e984538b530acbc7aa8d52feb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="6e270-102">Obecní delegáti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="6e270-102">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="6e270-103">A [delegovat](../../../csharp/language-reference/keywords/delegate.md) můžete definovat vlastní parametry typu.</span><span class="sxs-lookup"><span data-stu-id="6e270-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can define its own type parameters.</span></span> <span data-ttu-id="6e270-104">Kód, aby odkazy – obecný delegát typ argumentu zadat vytvoření uzavřené sestavené typu, stejně jako při vytvoření instance obecné třídy nebo volání obecné metody, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6e270-104">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]  
  
 <span data-ttu-id="6e270-105">C# verze 2.0 má novou funkci s názvem skupiny převod metoda, která se vztahují na konkrétní, jakož i obecný delegát typy a umožňuje zapsat předchozí řádek zjednodušenou syntaxí:</span><span class="sxs-lookup"><span data-stu-id="6e270-105">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]  
  
 <span data-ttu-id="6e270-106">Delegáti definované v rámci obecné třídy můžete použít parametry typu obecné třídy v stejným způsobem jako metody třídy.</span><span class="sxs-lookup"><span data-stu-id="6e270-106">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]  
  
 <span data-ttu-id="6e270-107">Argument typu obsahující třídy, musíte zadat kód, který odkazuje na delegát následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="6e270-107">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]  
  
 <span data-ttu-id="6e270-108">Obecní delegáti jsou zvláště užitečné při definování události podle typické návrhový vzor, protože argument odesílatele může být silného typu a již má být přetypovat do a z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="6e270-108">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6e270-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e270-109">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="6e270-110">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="6e270-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6e270-111">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="6e270-111">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="6e270-112">Obecné metody</span><span class="sxs-lookup"><span data-stu-id="6e270-112">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
 [<span data-ttu-id="6e270-113">Obecné třídy</span><span class="sxs-lookup"><span data-stu-id="6e270-113">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
 [<span data-ttu-id="6e270-114">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e270-114">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
 [<span data-ttu-id="6e270-115">Delegáti</span><span class="sxs-lookup"><span data-stu-id="6e270-115">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="6e270-116">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="6e270-116">Generics</span></span>](~/docs/standard/generics/index.md)
