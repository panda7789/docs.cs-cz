---
title: Obecné delegáty – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: 4e57256328fc81a485670b47fcf8fd1c38e26fac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712218"
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="b7323-102">Obecní delegáti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="b7323-102">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="b7323-103">[Delegát](../../language-reference/builtin-types/reference-types.md) může definovat vlastní parametry typu.</span><span class="sxs-lookup"><span data-stu-id="b7323-103">A [delegate](../../language-reference/builtin-types/reference-types.md) can define its own type parameters.</span></span> <span data-ttu-id="b7323-104">Kód, který odkazuje na obecný delegát můžete zadat argument typu k vytvoření uzavřeného konstruovaného typu, stejně jako při vytváření instancí obecné třídy nebo volání obecné metody, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b7323-104">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 <span data-ttu-id="b7323-105">C# verze 2.0 má novou funkci nazvanou převod skupiny metod, která se vztahuje na konkrétní i obecné typy delegátů a umožňuje napsat předchozí řádek s touto zjednodušenou syntaxí:</span><span class="sxs-lookup"><span data-stu-id="b7323-105">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 <span data-ttu-id="b7323-106">Delegáti definovaní v rámci obecné třídy můžete použít parametry typu obecné třídy stejným způsobem jako metody třídy.</span><span class="sxs-lookup"><span data-stu-id="b7323-106">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 <span data-ttu-id="b7323-107">Kód, který odkazuje delegát musí určit typ argument obsahující třídy, takto:</span><span class="sxs-lookup"><span data-stu-id="b7323-107">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 <span data-ttu-id="b7323-108">Obecné delegáty jsou užitečné zejména při definování událostí na základě typického návrhového vzoru, protože argument odesílatele <xref:System.Object>může být silně zadán a již nemusí být přetypován do a z .</span><span class="sxs-lookup"><span data-stu-id="b7323-108">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a><span data-ttu-id="b7323-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7323-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="b7323-110">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b7323-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b7323-111">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="b7323-111">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="b7323-112">Obecné metody</span><span class="sxs-lookup"><span data-stu-id="b7323-112">Generic Methods</span></span>](./generic-methods.md)
- [<span data-ttu-id="b7323-113">Obecné třídy</span><span class="sxs-lookup"><span data-stu-id="b7323-113">Generic Classes</span></span>](./generic-classes.md)
- [<span data-ttu-id="b7323-114">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7323-114">Generic Interfaces</span></span>](./generic-interfaces.md)
- [<span data-ttu-id="b7323-115">Delegáty</span><span class="sxs-lookup"><span data-stu-id="b7323-115">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="b7323-116">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="b7323-116">Generics</span></span>](../../../standard/generics/index.md)
