---
title: Obecní delegáti C# – Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: 3c6f29ead76f2e835d78a15d782e1aaca28942c8
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423268"
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="0316b-102">Obecní delegáti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="0316b-102">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="0316b-103">[Delegát](../../language-reference/builtin-types/reference-types.md) může definovat své vlastní parametry typu.</span><span class="sxs-lookup"><span data-stu-id="0316b-103">A [delegate](../../language-reference/builtin-types/reference-types.md) can define its own type parameters.</span></span> <span data-ttu-id="0316b-104">Kód, který odkazuje na obecného delegáta, může zadat argument typu pro vytvoření uzavřeného konstruovaného typu, stejně jako při vytváření instancí obecné třídy nebo volání obecné metody, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0316b-104">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 <span data-ttu-id="0316b-105">C#verze 2,0 obsahuje novou funkci nazvanou převod skupiny metod, která se vztahuje na konkrétní a také na obecné typy delegátů, a umožňuje napsat předchozí řádek pomocí této zjednodušené syntaxe:</span><span class="sxs-lookup"><span data-stu-id="0316b-105">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 <span data-ttu-id="0316b-106">Delegáti, kteří jsou definováni v rámci obecné třídy, mohou použít parametry typu obecné třídy stejným způsobem jako metody třídy.</span><span class="sxs-lookup"><span data-stu-id="0316b-106">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 <span data-ttu-id="0316b-107">Kód, který odkazuje na delegáta musí specifikovat typ argumentu obsahující třídy, jak je znázorněno níže:</span><span class="sxs-lookup"><span data-stu-id="0316b-107">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 <span data-ttu-id="0316b-108">Obecné Delegáti jsou zvláště užitečné při definování událostí na základě typického vzoru návrhu, protože argument odesílatele může být silného typu a již nesmí být přetypování na <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="0316b-108">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a><span data-ttu-id="0316b-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0316b-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="0316b-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0316b-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0316b-111">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="0316b-111">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="0316b-112">Obecné metody</span><span class="sxs-lookup"><span data-stu-id="0316b-112">Generic Methods</span></span>](./generic-methods.md)
- [<span data-ttu-id="0316b-113">Obecné třídy</span><span class="sxs-lookup"><span data-stu-id="0316b-113">Generic Classes</span></span>](./generic-classes.md)
- [<span data-ttu-id="0316b-114">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="0316b-114">Generic Interfaces</span></span>](./generic-interfaces.md)
- [<span data-ttu-id="0316b-115">Delegáty</span><span class="sxs-lookup"><span data-stu-id="0316b-115">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="0316b-116">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="0316b-116">Generics</span></span>](../../../standard/generics/index.md)
