---
title: Obecní delegáti - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: ff19b3d71858552158a8ae5d0ab362a86dc98e65
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423506"
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="12922-102">Obecní delegáti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="12922-102">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="12922-103">A [delegovat](../../../csharp/language-reference/keywords/delegate.md) můžete definovat vlastní parametry typu.</span><span class="sxs-lookup"><span data-stu-id="12922-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can define its own type parameters.</span></span> <span data-ttu-id="12922-104">Kód, že odkazy obecného delegátu možné zadat argument typu k vytvoření uzavřený konstruovaný typ., stejně jako při vytvoření instance generické třídy nebo volání obecné metody, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="12922-104">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 <span data-ttu-id="12922-105">C# verze 2.0 obsahuje novou funkci s názvem metody skupiny převod, který se vztahuje na typy konkrétní, jakož i obecných delegátů a umožňuje zapisovat na předchozí řádek s této zjednodušenou syntaxi:</span><span class="sxs-lookup"><span data-stu-id="12922-105">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 <span data-ttu-id="12922-106">Delegáti definované v rámci obecné třídy můžete použít parametry typu obecné třídy v stejným způsobem jako metody třídy.</span><span class="sxs-lookup"><span data-stu-id="12922-106">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 <span data-ttu-id="12922-107">Argument typu obsahující třídy, musíte zadat kód, který odkazuje na delegáta následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="12922-107">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 <span data-ttu-id="12922-108">Obecní delegáti jsou zvláště užitečné při definování události založen na typické návrhový vzor, protože argument odesílatele, mohou být silného typu a už musí být převeden do a z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="12922-108">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a><span data-ttu-id="12922-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12922-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="12922-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="12922-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="12922-111">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="12922-111">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="12922-112">Obecné metody</span><span class="sxs-lookup"><span data-stu-id="12922-112">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)
- [<span data-ttu-id="12922-113">Obecné třídy</span><span class="sxs-lookup"><span data-stu-id="12922-113">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)
- [<span data-ttu-id="12922-114">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="12922-114">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)
- [<span data-ttu-id="12922-115">Delegáti</span><span class="sxs-lookup"><span data-stu-id="12922-115">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="12922-116">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="12922-116">Generics</span></span>](~/docs/standard/generics/index.md)
