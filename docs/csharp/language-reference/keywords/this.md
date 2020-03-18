---
title: toto klíčové slovo – odkaz jazyka C#
description: toto klíčové slovo (Odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 2a2c487ad93e6fc75ecf95c541e859b8b60bb5b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715109"
---
# <a name="this-c-reference"></a><span data-ttu-id="a999c-103">this (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a999c-103">this (C# Reference)</span></span>

<span data-ttu-id="a999c-104">Klíčové `this` slovo odkazuje na aktuální instanci třídy a je také použit jako modifikátor prvníparametr metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="a999c-104">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>

> [!NOTE]
> <span data-ttu-id="a999c-105">Tento článek popisuje použití `this` s instancemi třídy.</span><span class="sxs-lookup"><span data-stu-id="a999c-105">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="a999c-106">Další informace o jeho použití v rozšiřujících metodách naleznete v [tématu Metody rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="a999c-106">For more information about its use in extension methods, see [Extension Methods](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="a999c-107">Toto jsou běžná použití `this`:</span><span class="sxs-lookup"><span data-stu-id="a999c-107">The following are common uses of `this`:</span></span>

- <span data-ttu-id="a999c-108">Chcete-li kvalifikovat členy skryté pod podobnými názvy, například:</span><span class="sxs-lookup"><span data-stu-id="a999c-108">To qualify members hidden by similar names, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- <span data-ttu-id="a999c-109">Chcete-li předat objekt jako parametr jiným metodám, například:</span><span class="sxs-lookup"><span data-stu-id="a999c-109">To pass an object as a parameter to other methods, for example:</span></span>

  ```csharp
  CalcTax(this);
  ```

- <span data-ttu-id="a999c-110">Deklarovat indexery, například:</span><span class="sxs-lookup"><span data-stu-id="a999c-110">To declare indexers, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

<span data-ttu-id="a999c-111">Statické členské funkce, protože existují na úrovni třídy a nikoli jako `this` součást objektu, nemají ukazatel.</span><span class="sxs-lookup"><span data-stu-id="a999c-111">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="a999c-112">Je chyba odkazovat `this` se na ve statické metodě.</span><span class="sxs-lookup"><span data-stu-id="a999c-112">It is an error to refer to `this` in a static method.</span></span>

## <a name="example"></a><span data-ttu-id="a999c-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="a999c-113">Example</span></span>

<span data-ttu-id="a999c-114">V tomto `this` příkladu se `Employee` používá ke `name` `alias`kvalifikaci členy třídy a , které jsou skryté pod podobnými názvy.</span><span class="sxs-lookup"><span data-stu-id="a999c-114">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="a999c-115">Používá se také k předání objektu metodě `CalcTax`, která patří do jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="a999c-115">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="a999c-116">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a999c-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a999c-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a999c-117">See also</span></span>

- [<span data-ttu-id="a999c-118">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a999c-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a999c-119">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a999c-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a999c-120">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a999c-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a999c-121">base</span><span class="sxs-lookup"><span data-stu-id="a999c-121">base</span></span>](base.md)
- [<span data-ttu-id="a999c-122">Metody</span><span class="sxs-lookup"><span data-stu-id="a999c-122">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
