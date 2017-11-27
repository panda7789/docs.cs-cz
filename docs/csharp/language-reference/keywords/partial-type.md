---
title: "partial (typ) (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords: partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5212984cc577ce05fc4697e0d648fb5545528562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="3f131-102">partial (typ) (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3f131-102">partial (Type) (C# Reference)</span></span>
<span data-ttu-id="3f131-103">Aby se daly rozdělit do několika souborů umožňují definice třídy, struktury nebo rozhraní definice částečné typu.</span><span class="sxs-lookup"><span data-stu-id="3f131-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>  
  
 <span data-ttu-id="3f131-104">V File1.cs:</span><span class="sxs-lookup"><span data-stu-id="3f131-104">In File1.cs:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]  
  
 <span data-ttu-id="3f131-105">V deklaraci File2.cs:</span><span class="sxs-lookup"><span data-stu-id="3f131-105">In File2.cs the declaration:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="3f131-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f131-106">Remarks</span></span>  
 <span data-ttu-id="3f131-107">Rozdělení třídu, struktura nebo rozhraní typ přes několik souborů může být užitečná při práci velkých projektech nebo s automaticky generovaného kódu, například poskytnutá [Návrhář formulářů Windows](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="3f131-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="3f131-108">Částečné typ může obsahovat [částečné metoda](../../../csharp/language-reference/keywords/partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="3f131-108">A partial type may contain a [partial method](../../../csharp/language-reference/keywords/partial-method.md).</span></span> <span data-ttu-id="3f131-109">Další informace najdete v tématu [částečné třídy a metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="3f131-109">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="3f131-110">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3f131-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3f131-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f131-111">See Also</span></span>  
 [<span data-ttu-id="3f131-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3f131-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3f131-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="3f131-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3f131-114">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="3f131-114">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="3f131-115">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="3f131-115">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)
