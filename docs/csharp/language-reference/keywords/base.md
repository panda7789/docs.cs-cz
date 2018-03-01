---
title: "base (Referenční dokumentace jazyka C#)"
description: "Další informace o základní klíčové slovo, který se používá pro přístup k členy základní třídy z v odvozené třídě v jazyce C#."
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1bbaa0cc05b35f822113bc3a8c3cde966b1484ef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="base-c-reference"></a><span data-ttu-id="6af43-103">base (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6af43-103">base (C# Reference)</span></span>

<span data-ttu-id="6af43-104">`base` – Klíčové slovo se používá pro přístup členy základní třídy z v odvozené třídě:</span><span class="sxs-lookup"><span data-stu-id="6af43-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="6af43-105">Volání metody na základní třídy, který se přepsal jinou metodou.</span><span class="sxs-lookup"><span data-stu-id="6af43-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="6af43-106">Zadejte, které konstruktor základní třídy by měla být volána při vytváření instance odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="6af43-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="6af43-107">Pro přístup k základní třída je povoleno pouze v konstruktor, metody instance nebo přistupující objekt vlastnosti instance.</span><span class="sxs-lookup"><span data-stu-id="6af43-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="6af43-108">Jedná se o chybu používat `base` – klíčové slovo z v rámci statickou metodu.</span><span class="sxs-lookup"><span data-stu-id="6af43-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="6af43-109">Základní třídy, které je přístupné je základní třídy zadaný v deklaraci třídy.</span><span class="sxs-lookup"><span data-stu-id="6af43-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="6af43-110">Pokud zadáte například `class ClassB : ClassA`, členové ClassA jsou k němu přistupovat z ClassB, bez ohledu na základní třídu ClassA.</span><span class="sxs-lookup"><span data-stu-id="6af43-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="6af43-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="6af43-111">Example</span></span>
<span data-ttu-id="6af43-112">V tomto příkladu i základní třídy, `Person`a odvozené třídy, `Employee`, obsahovat metodu s názvem `Getinfo`.</span><span class="sxs-lookup"><span data-stu-id="6af43-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="6af43-113">Pomocí `base` – klíčové slovo, je možné volat `Getinfo` metodu základní třídy, v rámci odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="6af43-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]

<span data-ttu-id="6af43-114">Další příklady najdete v tématu [nové](../../../csharp/language-reference/keywords/new.md), [virtuální](../../../csharp/language-reference/keywords/virtual.md), a [přepsat](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="6af43-114">For additional examples, see [new](../../../csharp/language-reference/keywords/new.md), [virtual](../../../csharp/language-reference/keywords/virtual.md), and [override](../../../csharp/language-reference/keywords/override.md).</span></span>

## <a name="example"></a><span data-ttu-id="6af43-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="6af43-115">Example</span></span>
<span data-ttu-id="6af43-116">Tento příklad ukazuje, jak určit volána při vytváření instance odvozené třídy základní třídy konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="6af43-116">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="6af43-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6af43-117">C# language specification</span></span>
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6af43-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="6af43-118">See also</span></span>
 [<span data-ttu-id="6af43-119">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6af43-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6af43-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="6af43-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6af43-121">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6af43-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="6af43-122">Tento</span><span class="sxs-lookup"><span data-stu-id="6af43-122">this</span></span>](../../../csharp/language-reference/keywords/this.md)