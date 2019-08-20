---
title: Toto klíčové slovo C# – referenční informace
ms.custom: seodec18
description: Toto klíčové slovoC# (referenční)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 4a3342e73fef3effd54f72e68283eb6085eef5b5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608446"
---
# <a name="this-c-reference"></a><span data-ttu-id="de37e-103">this (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="de37e-103">this (C# Reference)</span></span>

<span data-ttu-id="de37e-104">`this` Klíčové slovo odkazuje na aktuální instanci třídy a používá se také jako modifikátor prvního parametru metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="de37e-104">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>

> [!NOTE]
> <span data-ttu-id="de37e-105">Tento článek popisuje použití `this` s instancemi třídy.</span><span class="sxs-lookup"><span data-stu-id="de37e-105">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="de37e-106">Další informace o jeho použití v rozšiřujících metodách naleznete v tématu [metody rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="de37e-106">For more information about its use in extension methods, see [Extension Methods](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="de37e-107">Zde jsou běžně používané `this`nástroje:</span><span class="sxs-lookup"><span data-stu-id="de37e-107">The following are common uses of `this`:</span></span>

- <span data-ttu-id="de37e-108">Chcete-li kvalifikovat členy skryté podobným názvem, například:</span><span class="sxs-lookup"><span data-stu-id="de37e-108">To qualify members hidden by similar names, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- <span data-ttu-id="de37e-109">Pro předání objektu jako parametru jiným metodám, například:</span><span class="sxs-lookup"><span data-stu-id="de37e-109">To pass an object as a parameter to other methods, for example:</span></span>

  ```csharp
  CalcTax(this);
  ```

- <span data-ttu-id="de37e-110">Chcete-li deklarovat indexery, například:</span><span class="sxs-lookup"><span data-stu-id="de37e-110">To declare indexers, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

<span data-ttu-id="de37e-111">Statické členské funkce, protože existují na úrovni třídy a ne jako součást objektu, `this` nemají ukazatel.</span><span class="sxs-lookup"><span data-stu-id="de37e-111">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="de37e-112">V případě, že se odkazuje na `this` statickou metodu, se jedná o chybu.</span><span class="sxs-lookup"><span data-stu-id="de37e-112">It is an error to refer to `this` in a static method.</span></span>

## <a name="example"></a><span data-ttu-id="de37e-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="de37e-113">Example</span></span>

<span data-ttu-id="de37e-114">V tomto příkladu `this` se používá k `Employee` kvalifikování členů třídy, `name` a `alias`, které jsou skryté podobnými názvy.</span><span class="sxs-lookup"><span data-stu-id="de37e-114">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="de37e-115">Slouží také k předání objektu do metody `CalcTax`, která patří do jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="de37e-115">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="de37e-116">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="de37e-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="de37e-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de37e-117">See also</span></span>

- [<span data-ttu-id="de37e-118">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="de37e-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="de37e-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="de37e-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="de37e-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="de37e-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="de37e-121">base</span><span class="sxs-lookup"><span data-stu-id="de37e-121">base</span></span>](base.md)
- [<span data-ttu-id="de37e-122">Metody</span><span class="sxs-lookup"><span data-stu-id="de37e-122">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
