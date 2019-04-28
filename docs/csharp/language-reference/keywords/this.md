---
title: Toto klíčové slovo - C# odkaz
ms.custom: seodec18
description: Toto klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: af39ba6e20fb1a7c9e1a356ef5015afd885dbbca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660577"
---
# <a name="this-c-reference"></a><span data-ttu-id="88d89-103">this (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="88d89-103">this (C# Reference)</span></span>

<span data-ttu-id="88d89-104">`this` – Klíčové slovo odkazuje na aktuální instanci třídy a slouží také jako modifikátor první parametr metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="88d89-104">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>

> [!NOTE]
> <span data-ttu-id="88d89-105">Tento článek popisuje způsob používání `this` instancemi třídy.</span><span class="sxs-lookup"><span data-stu-id="88d89-105">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="88d89-106">Další informace o jeho použití v metodách rozšíření naleznete v tématu [rozšiřující metody](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="88d89-106">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="88d89-107">Tady jsou běžné způsoby použití `this`:</span><span class="sxs-lookup"><span data-stu-id="88d89-107">The following are common uses of `this`:</span></span>

- <span data-ttu-id="88d89-108">K získání způsobilosti členy skryta podobnými názvy, například:</span><span class="sxs-lookup"><span data-stu-id="88d89-108">To qualify members hidden by similar names, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- <span data-ttu-id="88d89-109">K předání objektu jako parametr do jiné metody, například:</span><span class="sxs-lookup"><span data-stu-id="88d89-109">To pass an object as a parameter to other methods, for example:</span></span>

  ```csharp
  CalcTax(this);
  ```

- <span data-ttu-id="88d89-110">Chcete-li deklarovat indexery, například:</span><span class="sxs-lookup"><span data-stu-id="88d89-110">To declare indexers, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

<span data-ttu-id="88d89-111">Statické členské funkce, protože existují na úrovni třídy, nikoli jako součást objektu, není nutné `this` ukazatele.</span><span class="sxs-lookup"><span data-stu-id="88d89-111">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="88d89-112">Jedná se o chybu k odkazování na `this` uvnitř statické metody.</span><span class="sxs-lookup"><span data-stu-id="88d89-112">It is an error to refer to `this` in a static method.</span></span>

## <a name="example"></a><span data-ttu-id="88d89-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="88d89-113">Example</span></span>

<span data-ttu-id="88d89-114">V tomto příkladu `this` se použijí pro kvalifikaci `Employee` členy, třídy `name` a `alias`, které jsou skryté, podobně jako názvy.</span><span class="sxs-lookup"><span data-stu-id="88d89-114">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="88d89-115">Používá se také k objektu předat metodě `CalcTax`, který patří do jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="88d89-115">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="88d89-116">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="88d89-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="88d89-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88d89-117">See also</span></span>

- [<span data-ttu-id="88d89-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="88d89-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="88d89-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="88d89-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="88d89-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="88d89-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="88d89-121">base</span><span class="sxs-lookup"><span data-stu-id="88d89-121">base</span></span>](base.md)
- [<span data-ttu-id="88d89-122">Metody</span><span class="sxs-lookup"><span data-stu-id="88d89-122">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
