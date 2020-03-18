---
title: základní klíčové slovo - C# Reference
description: Informace o základní klíčové slovo, které se používá pro přístup k členům základní třídy z v rámci odvozené třídy v C#.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: a4686fc5d4245a50de5d77dc0e71c231772f40ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713770"
---
# <a name="base-c-reference"></a><span data-ttu-id="4cac7-103">base (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4cac7-103">base (C# Reference)</span></span>

<span data-ttu-id="4cac7-104">Klíčové `base` slovo se používá pro přístup k členům základní třídy z odvozené třídy:</span><span class="sxs-lookup"><span data-stu-id="4cac7-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="4cac7-105">Volání metody na základní třídy, která byla přepsána jinou metodou.</span><span class="sxs-lookup"><span data-stu-id="4cac7-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="4cac7-106">Určete, který konstruktor základní třídy by měl být volán při vytváření instancí odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="4cac7-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="4cac7-107">Přístup základní třídy je povolen pouze v konstruktoru, metodě instance nebo přistupujícím objektu vlastnosti instance.</span><span class="sxs-lookup"><span data-stu-id="4cac7-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="4cac7-108">Je chyba použít `base` klíčové slovo z v rámci statické metody.</span><span class="sxs-lookup"><span data-stu-id="4cac7-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="4cac7-109">Základní třída, která je přístupná, je základní třída zadaná v deklaraci třídy.</span><span class="sxs-lookup"><span data-stu-id="4cac7-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="4cac7-110">Například pokud zadáte `class ClassB : ClassA`, členy ClassA jsou přístupné z ClassB, bez ohledu na základní třídy ClassA.</span><span class="sxs-lookup"><span data-stu-id="4cac7-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="4cac7-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="4cac7-111">Example</span></span>

<span data-ttu-id="4cac7-112">V tomto příkladu mají `Person`základní třída a odvozená třída `Employee`, `Getinfo`metodu s názvem .</span><span class="sxs-lookup"><span data-stu-id="4cac7-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="4cac7-113">Pomocí klíčového `base` slova je možné `Getinfo` volat metodu na základní třídy, z v rámci odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="4cac7-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

<span data-ttu-id="4cac7-114">Další příklady naleznete [v tématu new](new-modifier.md), [virtual](virtual.md)a [override](override.md).</span><span class="sxs-lookup"><span data-stu-id="4cac7-114">For additional examples, see [new](new-modifier.md), [virtual](virtual.md), and [override](override.md).</span></span>

## <a name="example"></a><span data-ttu-id="4cac7-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="4cac7-115">Example</span></span>

<span data-ttu-id="4cac7-116">Tento příklad ukazuje, jak určit konstruktor základní třídy volaný při vytváření instancí odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="4cac7-116">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="4cac7-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4cac7-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4cac7-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="4cac7-118">See also</span></span>

- [<span data-ttu-id="4cac7-119">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4cac7-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4cac7-120">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4cac7-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4cac7-121">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="4cac7-121">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="4cac7-122">tohoto provozu</span><span class="sxs-lookup"><span data-stu-id="4cac7-122">this</span></span>](./this.md)
