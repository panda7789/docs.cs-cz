---
title: Vnořené typy – programovací příručka jazyka C#
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 12e44ccc1254424c152a238c8390f133550fa54c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626487"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="d3233-102">Vnořené typy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="d3233-102">Nested Types (C# Programming Guide)</span></span>

<span data-ttu-id="d3233-103">Typ definovaný v rámci [třídy](../../language-reference/keywords/class.md), [struktury](../../language-reference/builtin-types/struct.md)nebo [rozhraní](../../language-reference/keywords/interface.md) se nazývá vnořený typ.</span><span class="sxs-lookup"><span data-stu-id="d3233-103">A type defined within a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) is called a nested type.</span></span> <span data-ttu-id="d3233-104">Například</span><span class="sxs-lookup"><span data-stu-id="d3233-104">For example</span></span>

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

<span data-ttu-id="d3233-105">Bez ohledu na to, zda vnější typ je třída, rozhraní nebo struktura, vnořené typy výchozí [private](../../language-reference/keywords/private.md); jsou přístupné pouze z jejich obsahujícího typu.</span><span class="sxs-lookup"><span data-stu-id="d3233-105">Regardless of whether the outer type is a class, interface, or struct, nested types default to [private](../../language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="d3233-106">V předchozím příkladu `Nested` je třída nepřístupná pro externí typy.</span><span class="sxs-lookup"><span data-stu-id="d3233-106">In the previous example, the `Nested` class is inaccessible to external types.</span></span>

<span data-ttu-id="d3233-107">Můžete také určit [modifikátor přístupu](../../language-reference/keywords/access-modifiers.md) k definování přístupnosti vnořeného typu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="d3233-107">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="d3233-108">Vnořené typy **třídy** mohou být [veřejné](../../language-reference/keywords/public.md), [chráněné](../../language-reference/keywords/protected.md), [interní](../../language-reference/keywords/internal.md), [chráněné interní](../../language-reference/keywords/protected-internal.md), [soukromé](../../language-reference/keywords/private.md) nebo [soukromé chráněné](../../language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="d3233-108">Nested types of a **class** can be [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span>

   <span data-ttu-id="d3233-109">`protected`Definování třídy nebo `protected internal` `private protected` vnořené třídy uvnitř [zapečetěné třídy](../../language-reference/keywords/sealed.md) však generuje upozornění kompilátoru [CS0628](../../misc/cs0628.md), "nový chráněný člen deklarovaný v zapečetěné třídě".</span><span class="sxs-lookup"><span data-stu-id="d3233-109">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="d3233-110">Vnořené typy **struktury** mohou být [veřejné](../../language-reference/keywords/public.md), [interní](../../language-reference/keywords/internal.md)nebo [soukromé](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="d3233-110">Nested types of a **struct** can be [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md), or [private](../../language-reference/keywords/private.md).</span></span>

<span data-ttu-id="d3233-111">Následující příklad zpřístupňuje třídu: `Nested`</span><span class="sxs-lookup"><span data-stu-id="d3233-111">The following example makes the `Nested` class public:</span></span>

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

<span data-ttu-id="d3233-112">Vnořený nebo vnitřní, typ může přistupovat k obsahující nebo vnější, typ.</span><span class="sxs-lookup"><span data-stu-id="d3233-112">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="d3233-113">Chcete-li získat přístup k obsahujícímu typu, předajte jej jako argument konstruktoru vnořeného typu.</span><span class="sxs-lookup"><span data-stu-id="d3233-113">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="d3233-114">Například:</span><span class="sxs-lookup"><span data-stu-id="d3233-114">For example:</span></span>

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

<span data-ttu-id="d3233-115">Vnořený typ má přístup ke všem členům, které jsou přístupné pro jeho obsahující typ.</span><span class="sxs-lookup"><span data-stu-id="d3233-115">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="d3233-116">Může přistupovat k soukromým a chráněným členům obsahujícího typu, včetně všech zděděných chráněných členů.</span><span class="sxs-lookup"><span data-stu-id="d3233-116">It can access private and protected members of the containing type, including any inherited protected members.</span></span>

<span data-ttu-id="d3233-117">V předchozím prohlášení je `Nested` `Container.Nested`úplný název třídy .</span><span class="sxs-lookup"><span data-stu-id="d3233-117">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="d3233-118">Toto je název použitý k vytvoření nové instance vnořené třídy takto:</span><span class="sxs-lookup"><span data-stu-id="d3233-118">This is the name used to create a new instance of the nested class, as follows:</span></span>

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a><span data-ttu-id="d3233-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3233-119">See also</span></span>

- [<span data-ttu-id="d3233-120">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d3233-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d3233-121">Třídy a struky</span><span class="sxs-lookup"><span data-stu-id="d3233-121">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="d3233-122">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="d3233-122">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="d3233-123">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="d3233-123">Constructors</span></span>](./constructors.md)
