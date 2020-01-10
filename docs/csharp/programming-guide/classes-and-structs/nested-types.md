---
title: Vnořené typy – C# Průvodce programováním
ms.date: 07/10/2017
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 982eeceb2088dd6e1e57fe796b38e46c0f2d4de8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705493"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="1d90c-102">Vnořené typy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="1d90c-102">Nested Types (C# Programming Guide)</span></span>
<span data-ttu-id="1d90c-103">Typ definovaný v rámci [třídy](../../language-reference/keywords/class.md) nebo [struktury](../../language-reference/keywords/struct.md) se nazývá vnořený typ.</span><span class="sxs-lookup"><span data-stu-id="1d90c-103">A type defined within a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/keywords/struct.md) is called a nested type.</span></span> <span data-ttu-id="1d90c-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1d90c-104">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#68](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#68)]  
  
<span data-ttu-id="1d90c-105">Bez ohledu na to, zda je vnější typ třída nebo struktura, vnořené typy jsou standardně [soukromé](../../language-reference/keywords/private.md); jsou přístupné pouze z jejich nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="1d90c-105">Regardless of whether the outer type is a class or a struct, nested types default to [private](../../language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="1d90c-106">V předchozím příkladu je třída `Nested` nepřístupná externím typům.</span><span class="sxs-lookup"><span data-stu-id="1d90c-106">In the previous example, the `Nested` class is inaccessible to external types.</span></span> 

<span data-ttu-id="1d90c-107">Můžete také zadat [modifikátor přístupu](../../language-reference/keywords/access-modifiers.md) pro definování přístupnosti vnořeného typu, a to následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="1d90c-107">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="1d90c-108">Vnořené typy **třídy** můžou být [veřejné](../../language-reference/keywords/public.md), [chráněné](../../language-reference/keywords/protected.md), [interní](../../language-reference/keywords/internal.md), [chráněné interní](../../language-reference/keywords/protected-internal.md), [privátní](../../language-reference/keywords/private.md) nebo [privátní](../../language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="1d90c-108">Nested types of a **class** can be [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> 

   <span data-ttu-id="1d90c-109">Nicméně definování `protected`, `protected internal` nebo `private protected` vnořené třídy v [zapečetěné třídě](../../language-reference/keywords/sealed.md) vygeneruje upozornění kompilátoru [CS0628](../../misc/cs0628.md), v zapečetěné třídě je deklarovaný nový chráněný člen.</span><span class="sxs-lookup"><span data-stu-id="1d90c-109">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="1d90c-110">Vnořené typy **struktury** můžou být [veřejné](../../language-reference/keywords/public.md), [interní](../../language-reference/keywords/internal.md)nebo [soukromé](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="1d90c-110">Nested types of a **struct** can be [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md), or [private](../../language-reference/keywords/private.md).</span></span>
  
<span data-ttu-id="1d90c-111">Následující příklad nastaví `Nested` třídy jako veřejné:</span><span class="sxs-lookup"><span data-stu-id="1d90c-111">The following example makes the `Nested` class public:</span></span>
  
 [!code-csharp[csProgGuideObjects#69](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#69)]  
  
 <span data-ttu-id="1d90c-112">Vnořený nebo vnitřní typ může přistupovat k typu, který obsahuje, nebo vnějšímu typu.</span><span class="sxs-lookup"><span data-stu-id="1d90c-112">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="1d90c-113">Chcete-li získat přístup k nadřazenému typu, předejte jej jako argument konstruktoru vnořeného typu.</span><span class="sxs-lookup"><span data-stu-id="1d90c-113">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="1d90c-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1d90c-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#70](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#70)]  
  
 <span data-ttu-id="1d90c-115">Vnořený typ má přístup ke všem členům, kteří mají přístup k jeho nadřazenému typu.</span><span class="sxs-lookup"><span data-stu-id="1d90c-115">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="1d90c-116">Má přístup k soukromým a chráněným členům nadřazeného typu, včetně všech zděděných chráněných členů.</span><span class="sxs-lookup"><span data-stu-id="1d90c-116">It can access private and protected members of the containing type, including any inherited protected members.</span></span>  
  
 <span data-ttu-id="1d90c-117">V předchozí deklaraci je úplný název třídy `Nested` `Container.Nested`.</span><span class="sxs-lookup"><span data-stu-id="1d90c-117">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="1d90c-118">Toto je název, který se používá k vytvoření nové instance vnořené třídy následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="1d90c-118">This is the name used to create a new instance of the nested class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#71](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#71)]  
  
## <a name="see-also"></a><span data-ttu-id="1d90c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d90c-119">See also</span></span>

- [<span data-ttu-id="1d90c-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1d90c-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1d90c-121">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="1d90c-121">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="1d90c-122">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="1d90c-122">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="1d90c-123">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="1d90c-123">Constructors</span></span>](./constructors.md)
