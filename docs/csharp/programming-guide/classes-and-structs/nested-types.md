---
title: Vnořené typy – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/10/2017
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: b08a7e95e3ddf7e2392be30f2e69c4ec8f425107
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244003"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="94e4f-102">Vnořené typy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="94e4f-102">Nested Types (C# Programming Guide)</span></span>
<span data-ttu-id="94e4f-103">Typ definovaný v rámci [třídy](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md) se nazývá vnořený typ.</span><span class="sxs-lookup"><span data-stu-id="94e4f-103">A type defined within a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is called a nested type.</span></span> <span data-ttu-id="94e4f-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="94e4f-104">For example:</span></span>  
  
[!code-csharp[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_1.cs)]  
  
<span data-ttu-id="94e4f-105">Bez ohledu na to, zda je vnější typ třída nebo struktura, vnořené typy jsou přednastaveny na [privátní](../../../csharp/language-reference/keywords/private.md); jsou přístupné jenom z jeho nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="94e4f-105">Regardless of whether the outer type is a class or a struct, nested types default to [private](../../../csharp/language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="94e4f-106">V předchozím příkladu `Nested` třídy je nedostupný pro externí typy.</span><span class="sxs-lookup"><span data-stu-id="94e4f-106">In the previous example, the `Nested` class is inaccessible to external types.</span></span> 

<span data-ttu-id="94e4f-107">Můžete také určit, [modifikátor přístupu](../../language-reference/keywords/access-modifiers.md) k definování přístupnost vnořeného typu, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="94e4f-107">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="94e4f-108">Vnořené typy **třídy** může být [veřejné](../../../csharp/language-reference/keywords/public.md), [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), [interní chráněné](../../../csharp/language-reference/keywords/protected-internal.md), [privátní](../../../csharp/language-reference/keywords/private.md) nebo [private, protected](../../../csharp/language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="94e4f-108">Nested types of a **class** can be [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md), [private](../../../csharp/language-reference/keywords/private.md) or [private protected](../../../csharp/language-reference/keywords/private-protected.md).</span></span> 

   <span data-ttu-id="94e4f-109">Ale definování `protected`, `protected internal` nebo `private protected` vnořenou třídu uvnitř [zapečetěná třída](../../language-reference/keywords/sealed.md) generuje upozornění kompilátoru [CS0628](../../misc/cs0628.md), "deklarovaný nový chráněný člen v zapečetěné třídě."</span><span class="sxs-lookup"><span data-stu-id="94e4f-109">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="94e4f-110">Vnořené typy **struktura** může být [veřejné](../../../csharp/language-reference/keywords/public.md), [interní](../../../csharp/language-reference/keywords/internal.md), nebo [privátní](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="94e4f-110">Nested types of a **struct** can be [public](../../../csharp/language-reference/keywords/public.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md).</span></span>
  
<span data-ttu-id="94e4f-111">Následující příklad provede `Nested` veřejné třídy:</span><span class="sxs-lookup"><span data-stu-id="94e4f-111">The following example makes the `Nested` class public:</span></span>
  
[!code-csharp[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_2.cs)]  
  
 <span data-ttu-id="94e4f-112">Typ vnořený nebo vnitřní, můžete získat přístup k obsahujícímu nebo vnějšímu, typu.</span><span class="sxs-lookup"><span data-stu-id="94e4f-112">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="94e4f-113">Pro přístup k nadřazeného typu, předejte ji jako argument konstruktoru vnořeného typu.</span><span class="sxs-lookup"><span data-stu-id="94e4f-113">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="94e4f-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="94e4f-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_3.cs)]  
  
 <span data-ttu-id="94e4f-115">Vnořený typ má přístup ke všem členům, kteří jsou k dispozici k jeho nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="94e4f-115">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="94e4f-116">Má přístup k soukromým a chráněným členům nadřazeného typu, včetně všech zděděných chráněných členů.</span><span class="sxs-lookup"><span data-stu-id="94e4f-116">It can access private and protected members of the containing type, including any inherited protected members.</span></span>  
  
 <span data-ttu-id="94e4f-117">V předchozí prohlášení, úplný název třídy `Nested` je `Container.Nested`.</span><span class="sxs-lookup"><span data-stu-id="94e4f-117">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="94e4f-118">Toto je název používaný k vytvoření nové instance vnořené třídy takto:</span><span class="sxs-lookup"><span data-stu-id="94e4f-118">This is the name used to create a new instance of the nested class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="94e4f-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="94e4f-119">See Also</span></span>

- [<span data-ttu-id="94e4f-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="94e4f-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="94e4f-121">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="94e4f-121">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="94e4f-122">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="94e4f-122">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [<span data-ttu-id="94e4f-123">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="94e4f-123">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
