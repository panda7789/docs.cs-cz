---
title: Vnořené typy – Průvodce programováním v C#
description: Typ definovaný v rámci třídy, struktury nebo rozhraní se nazývá vnořený typ v jazyce C#.
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 9e1c6c1e8b22b5447d43915ab02984aa13146301
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864940"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="9aeba-103">Vnořené typy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="9aeba-103">Nested Types (C# Programming Guide)</span></span>

<span data-ttu-id="9aeba-104">Typ definovaný v rámci [třídy](../../language-reference/keywords/class.md), [struktury](../../language-reference/builtin-types/struct.md)nebo [rozhraní](../../language-reference/keywords/interface.md) se nazývá vnořený typ.</span><span class="sxs-lookup"><span data-stu-id="9aeba-104">A type defined within a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) is called a nested type.</span></span> <span data-ttu-id="9aeba-105">Například</span><span class="sxs-lookup"><span data-stu-id="9aeba-105">For example</span></span>

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

<span data-ttu-id="9aeba-106">Bez ohledu na to, zda je vnější typ třída, rozhraní nebo struktura, jsou vnořené typy standardně [soukromé](../../language-reference/keywords/private.md); jsou přístupné pouze z jejich nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="9aeba-106">Regardless of whether the outer type is a class, interface, or struct, nested types default to [private](../../language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="9aeba-107">V předchozím příkladu `Nested` je třída nepřístupná externím typům.</span><span class="sxs-lookup"><span data-stu-id="9aeba-107">In the previous example, the `Nested` class is inaccessible to external types.</span></span>

<span data-ttu-id="9aeba-108">Můžete také zadat [modifikátor přístupu](../../language-reference/keywords/access-modifiers.md) pro definování přístupnosti vnořeného typu, a to následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9aeba-108">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="9aeba-109">Vnořené typy **třídy** můžou být [veřejné](../../language-reference/keywords/public.md), [chráněné](../../language-reference/keywords/protected.md), [interní](../../language-reference/keywords/internal.md), [chráněné interní](../../language-reference/keywords/protected-internal.md), [privátní](../../language-reference/keywords/private.md) nebo [privátní](../../language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="9aeba-109">Nested types of a **class** can be [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span>

   <span data-ttu-id="9aeba-110">Nicméně definování `protected` `protected internal` nebo `private protected` vnořená třída v [zapečetěné třídě](../../language-reference/keywords/sealed.md) vygeneruje upozornění kompilátoru [CS0628](../../misc/cs0628.md), v zapečetěné třídě je deklarovaný nový chráněný člen.</span><span class="sxs-lookup"><span data-stu-id="9aeba-110">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="9aeba-111">Vnořené typy **struktury** můžou být [veřejné](../../language-reference/keywords/public.md), [interní](../../language-reference/keywords/internal.md)nebo [soukromé](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="9aeba-111">Nested types of a **struct** can be [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md), or [private](../../language-reference/keywords/private.md).</span></span>

<span data-ttu-id="9aeba-112">Následující příklad nastaví třídu jako `Nested` veřejnou:</span><span class="sxs-lookup"><span data-stu-id="9aeba-112">The following example makes the `Nested` class public:</span></span>

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

<span data-ttu-id="9aeba-113">Vnořený nebo vnitřní typ může přistupovat k typu, který obsahuje, nebo vnějšímu typu.</span><span class="sxs-lookup"><span data-stu-id="9aeba-113">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="9aeba-114">Chcete-li získat přístup k nadřazenému typu, předejte jej jako argument konstruktoru vnořeného typu.</span><span class="sxs-lookup"><span data-stu-id="9aeba-114">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="9aeba-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9aeba-115">For example:</span></span>

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

<span data-ttu-id="9aeba-116">Vnořený typ má přístup ke všem členům, kteří mají přístup k jeho nadřazenému typu.</span><span class="sxs-lookup"><span data-stu-id="9aeba-116">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="9aeba-117">Má přístup k soukromým a chráněným členům nadřazeného typu, včetně všech zděděných chráněných členů.</span><span class="sxs-lookup"><span data-stu-id="9aeba-117">It can access private and protected members of the containing type, including any inherited protected members.</span></span>

<span data-ttu-id="9aeba-118">V předchozí deklaraci je úplný název třídy `Nested` `Container.Nested` .</span><span class="sxs-lookup"><span data-stu-id="9aeba-118">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="9aeba-119">Toto je název, který se používá k vytvoření nové instance vnořené třídy následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9aeba-119">This is the name used to create a new instance of the nested class, as follows:</span></span>

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a><span data-ttu-id="9aeba-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="9aeba-120">See also</span></span>

- [<span data-ttu-id="9aeba-121">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="9aeba-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9aeba-122">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="9aeba-122">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="9aeba-123">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="9aeba-123">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="9aeba-124">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="9aeba-124">Constructors</span></span>](./constructors.md)
