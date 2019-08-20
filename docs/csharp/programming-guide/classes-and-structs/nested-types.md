---
title: Vnořené typy – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/10/2017
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: de2e369702c48047835bc49b98df8f48fbd13480
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596533"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="5292f-102">Vnořené typy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5292f-102">Nested Types (C# Programming Guide)</span></span>
<span data-ttu-id="5292f-103">Typ definovaný v rámci [třídy](../../language-reference/keywords/class.md) nebo [struktury](../../language-reference/keywords/struct.md) se nazývá vnořený typ.</span><span class="sxs-lookup"><span data-stu-id="5292f-103">A type defined within a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/keywords/struct.md) is called a nested type.</span></span> <span data-ttu-id="5292f-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5292f-104">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#68](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#68)]  
  
<span data-ttu-id="5292f-105">Bez ohledu na to, zda je vnější typ třída nebo struktura, vnořené typy jsou standardně [soukromé](../../language-reference/keywords/private.md); jsou přístupné pouze z jejich nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="5292f-105">Regardless of whether the outer type is a class or a struct, nested types default to [private](../../language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="5292f-106">V předchozím příkladu `Nested` je třída nepřístupná externím typům.</span><span class="sxs-lookup"><span data-stu-id="5292f-106">In the previous example, the `Nested` class is inaccessible to external types.</span></span> 

<span data-ttu-id="5292f-107">Můžete také zadat [modifikátor přístupu](../../language-reference/keywords/access-modifiers.md) pro definování přístupnosti vnořeného typu, a to následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5292f-107">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="5292f-108">Vnořené typy **třídy** můžou být [veřejné](../../language-reference/keywords/public.md), [chráněné](../../language-reference/keywords/protected.md), [interní](../../language-reference/keywords/internal.md), [chráněné interní](../../language-reference/keywords/protected-internal.md), [privátní](../../language-reference/keywords/private.md) nebo [privátní](../../language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="5292f-108">Nested types of a **class** can be [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> 

   <span data-ttu-id="5292f-109">Nicméně definování `protected` `protected internal` nebo [](../../misc/cs0628.md) [](../../language-reference/keywords/sealed.md) vnořená třída v zapečetěné třídě vygeneruje upozornění kompilátoru CS0628, v zapečetěné třídě je deklarovaný nový chráněný člen. `private protected`</span><span class="sxs-lookup"><span data-stu-id="5292f-109">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="5292f-110">Vnořené typy **struktury** můžou být [veřejné](../../language-reference/keywords/public.md), [interní](../../language-reference/keywords/internal.md)nebo [soukromé](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="5292f-110">Nested types of a **struct** can be [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md), or [private](../../language-reference/keywords/private.md).</span></span>
  
<span data-ttu-id="5292f-111">Následující příklad nastaví třídu jako `Nested` veřejnou:</span><span class="sxs-lookup"><span data-stu-id="5292f-111">The following example makes the `Nested` class public:</span></span>
  
 [!code-csharp[csProgGuideObjects#69](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#69)]  
  
 <span data-ttu-id="5292f-112">Vnořený nebo vnitřní typ může přistupovat k typu, který obsahuje, nebo vnějšímu typu.</span><span class="sxs-lookup"><span data-stu-id="5292f-112">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="5292f-113">Chcete-li získat přístup k nadřazenému typu, předejte jej jako argument konstruktoru vnořeného typu.</span><span class="sxs-lookup"><span data-stu-id="5292f-113">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="5292f-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5292f-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#70](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#70)]  
  
 <span data-ttu-id="5292f-115">Vnořený typ má přístup ke všem členům, kteří mají přístup k jeho nadřazenému typu.</span><span class="sxs-lookup"><span data-stu-id="5292f-115">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="5292f-116">Má přístup k soukromým a chráněným členům nadřazeného typu, včetně všech zděděných chráněných členů.</span><span class="sxs-lookup"><span data-stu-id="5292f-116">It can access private and protected members of the containing type, including any inherited protected members.</span></span>  
  
 <span data-ttu-id="5292f-117">V předchozí deklaraci je `Nested` `Container.Nested`úplný název třídy.</span><span class="sxs-lookup"><span data-stu-id="5292f-117">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="5292f-118">Toto je název, který se používá k vytvoření nové instance vnořené třídy následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5292f-118">This is the name used to create a new instance of the nested class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#71](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#71)]  
  
## <a name="see-also"></a><span data-ttu-id="5292f-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5292f-119">See also</span></span>

- [<span data-ttu-id="5292f-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5292f-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5292f-121">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="5292f-121">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="5292f-122">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="5292f-122">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="5292f-123">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="5292f-123">Constructors</span></span>](./constructors.md)
