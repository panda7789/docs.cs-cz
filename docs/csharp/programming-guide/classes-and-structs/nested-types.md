---
title: "Vnořené typy (Průvodce programováním v C#)"
ms.date: 07/10/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab13c68b638062ab89c90dbfc51b51b8d72d3bde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="b1495-102">Vnořené typy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="b1495-102">Nested Types (C# Programming Guide)</span></span>
<span data-ttu-id="b1495-103">Typem definovaným v rámci [třída](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md) nazývá vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="b1495-103">A type defined within a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is called a nested type.</span></span> <span data-ttu-id="b1495-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b1495-104">For example:</span></span>  
  
[!code-csharp[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_1.cs)]  
  
<span data-ttu-id="b1495-105">Bez ohledu na to, jestli je vnější typ třídy nebo struktury, jako výchozí vnořené typy [privátní](../../../csharp/language-reference/keywords/private.md); jsou přístupné pouze z jejich nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="b1495-105">Regardless of whether the outer type is a class or a struct, nested types default to [private](../../../csharp/language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="b1495-106">V předchozím příkladu `Nested` třída je dostupná pro externí typy.</span><span class="sxs-lookup"><span data-stu-id="b1495-106">In the previous example, the `Nested` class is inaccessible to external types.</span></span> 

<span data-ttu-id="b1495-107">Můžete také určit, [– modifikátor přístupu](../../language-reference/keywords/access-modifiers.md) k usnadnění vnořeného typu, definujte takto:</span><span class="sxs-lookup"><span data-stu-id="b1495-107">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="b1495-108">Vnořené typy **třída** může být [veřejné](../../../csharp/language-reference/keywords/public.md), [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), [chráněné interní](../../../csharp/language-reference/keywords/protected-internal.md), [privátní](../../../csharp/language-reference/keywords/private.md) nebo [privátní chráněné](../../../csharp/language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="b1495-108">Nested types of a **class** can be [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md), [private](../../../csharp/language-reference/keywords/private.md) or [private protected](../../../csharp/language-reference/keywords/private-protected.md).</span></span> 

   <span data-ttu-id="b1495-109">Definování však `protected`, `protected internal` nebo `private protected` vnořené třídy uvnitř [zapečetěné třídy](../../language-reference/keywords/sealed.md) vygeneruje upozornění kompilátoru [CS0628](../../misc/cs0628.md), "nové chráněného člena deklarovaná ve třídě zapečetěné."</span><span class="sxs-lookup"><span data-stu-id="b1495-109">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="b1495-110">Vnořené typy **struktura** může být [veřejné](../../../csharp/language-reference/keywords/public.md), [interní](../../../csharp/language-reference/keywords/internal.md), nebo [privátní](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="b1495-110">Nested types of a **struct** can be [public](../../../csharp/language-reference/keywords/public.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md).</span></span>
  
<span data-ttu-id="b1495-111">Následující příklad vytvoří `Nested` veřejné třídy:</span><span class="sxs-lookup"><span data-stu-id="b1495-111">The following example makes the `Nested` class public:</span></span>
  
[!code-csharp[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_2.cs)]  
  
 <span data-ttu-id="b1495-112">Typ vnořené nebo vnitřní, můžete přistupovat obsahující nebo vnější typu.</span><span class="sxs-lookup"><span data-stu-id="b1495-112">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="b1495-113">Pro přístup k obsahující typ, předejte jako argument konstruktoru typu vnořené.</span><span class="sxs-lookup"><span data-stu-id="b1495-113">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="b1495-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b1495-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_3.cs)]  
  
 <span data-ttu-id="b1495-115">Vnořené typy má přístup do všech členů, které jsou přístupné pro jeho nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="b1495-115">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="b1495-116">Má přístup k privátním a chráněné členy obsahující typu, včetně všech zděděné chráněné členy.</span><span class="sxs-lookup"><span data-stu-id="b1495-116">It can access private and protected members of the containing type, including any inherited protected members.</span></span>  
  
 <span data-ttu-id="b1495-117">V předchozích deklaraci, úplný název třídy `Nested` je `Container.Nested`.</span><span class="sxs-lookup"><span data-stu-id="b1495-117">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="b1495-118">Toto je název sloužící k vytvoření nové instance vnořené třídy následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b1495-118">This is the name used to create a new instance of the nested class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b1495-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1495-119">See Also</span></span>  
 [<span data-ttu-id="b1495-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b1495-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b1495-121">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="b1495-121">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="b1495-122">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="b1495-122">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="b1495-123">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="b1495-123">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
