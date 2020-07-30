---
title: Obecní delegáti – Průvodce programováním v C#
description: Seznamte se s používáním generických delegátů v jazyce C#. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: d99271ca9f12e95743d633caac16aaa4151e9c41
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301902"
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="845f8-104">Obecní delegáti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="845f8-104">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="845f8-105">[Delegát](../../language-reference/builtin-types/reference-types.md) může definovat své vlastní parametry typu.</span><span class="sxs-lookup"><span data-stu-id="845f8-105">A [delegate](../../language-reference/builtin-types/reference-types.md) can define its own type parameters.</span></span> <span data-ttu-id="845f8-106">Kód, který odkazuje na obecného delegáta, může zadat argument typu pro vytvoření uzavřeného konstruovaného typu, stejně jako při vytváření instancí obecné třídy nebo volání obecné metody, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="845f8-106">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 <span data-ttu-id="845f8-107">Jazyk C# verze 2,0 obsahuje novou funkci nazvanou převod skupiny metod, která se vztahuje na konkrétní a také na obecné typy delegátů, a umožňuje napsat předchozí řádek pomocí této zjednodušené syntaxe:</span><span class="sxs-lookup"><span data-stu-id="845f8-107">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 <span data-ttu-id="845f8-108">Delegáti, kteří jsou definováni v rámci obecné třídy, mohou použít parametry typu obecné třídy stejným způsobem jako metody třídy.</span><span class="sxs-lookup"><span data-stu-id="845f8-108">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 <span data-ttu-id="845f8-109">Kód, který odkazuje na delegáta musí specifikovat typ argumentu obsahující třídy, jak je znázorněno níže:</span><span class="sxs-lookup"><span data-stu-id="845f8-109">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 <span data-ttu-id="845f8-110">Obecné Delegáti jsou zvláště užitečné při definování událostí na základě typického vzoru návrhu, protože argument odesílatele může být silného typu a již není nutné jej přetypování na a z <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="845f8-110">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a><span data-ttu-id="845f8-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="845f8-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="845f8-112">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="845f8-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="845f8-113">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="845f8-113">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="845f8-114">Obecné metody</span><span class="sxs-lookup"><span data-stu-id="845f8-114">Generic Methods</span></span>](./generic-methods.md)
- [<span data-ttu-id="845f8-115">Obecné třídy</span><span class="sxs-lookup"><span data-stu-id="845f8-115">Generic Classes</span></span>](./generic-classes.md)
- [<span data-ttu-id="845f8-116">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="845f8-116">Generic Interfaces</span></span>](./generic-interfaces.md)
- [<span data-ttu-id="845f8-117">Delegáti</span><span class="sxs-lookup"><span data-stu-id="845f8-117">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="845f8-118">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="845f8-118">Generics</span></span>](../../../standard/generics/index.md)
