---
title: základní klíčové slovo C# – referenční informace
ms.custom: seodec18
description: Přečtěte si základní klíčové slovo, které se používá pro přístup ke členům základní třídy v rámci odvozené třídy v C#.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: b882a8d1e5979ac184d184be379dd76f7bf3600f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602255"
---
# <a name="base-c-reference"></a><span data-ttu-id="4abf3-103">base (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4abf3-103">base (C# Reference)</span></span>

<span data-ttu-id="4abf3-104">`base` Klíčové slovo se používá pro přístup ke členům základní třídy v rámci odvozené třídy:</span><span class="sxs-lookup"><span data-stu-id="4abf3-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="4abf3-105">Volejte metodu pro základní třídu, která byla přepsána jinou metodou.</span><span class="sxs-lookup"><span data-stu-id="4abf3-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="4abf3-106">Určuje, který konstruktor základní třídy by měl být volán při vytváření instancí odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="4abf3-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="4abf3-107">Přístup ke základní třídě je povolený jenom v konstruktoru, metodě instance nebo přistupujícím objektu vlastnosti instance.</span><span class="sxs-lookup"><span data-stu-id="4abf3-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="4abf3-108">Použití `base` klíčového slova v rámci statické metody je chybné.</span><span class="sxs-lookup"><span data-stu-id="4abf3-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="4abf3-109">Základní třída, která je k dispozici, je základní třída zadaná v deklaraci třídy.</span><span class="sxs-lookup"><span data-stu-id="4abf3-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="4abf3-110">Například pokud zadáte `class ClassB : ClassA`, budou k členům třídy Class přicházet z ClassB bez ohledu na základní třídu třídy.</span><span class="sxs-lookup"><span data-stu-id="4abf3-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="4abf3-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="4abf3-111">Example</span></span>

<span data-ttu-id="4abf3-112">V tomto příkladu mají základní třídu, `Person`i odvozenou `Employee`třídu metodu s názvem `Getinfo`.</span><span class="sxs-lookup"><span data-stu-id="4abf3-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="4abf3-113">Pomocí `base` klíčového slova je možné `Getinfo` volat metodu pro základní třídu z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="4abf3-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

<span data-ttu-id="4abf3-114">Další příklady naleznete v tématu [New](new-modifier.md), [Virtual](virtual.md)a [override](override.md).</span><span class="sxs-lookup"><span data-stu-id="4abf3-114">For additional examples, see [new](new-modifier.md), [virtual](virtual.md), and [override](override.md).</span></span>

## <a name="example"></a><span data-ttu-id="4abf3-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="4abf3-115">Example</span></span>

<span data-ttu-id="4abf3-116">Tento příklad ukazuje, jak určit konstruktor základní třídy nazvaný při vytváření instancí odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="4abf3-116">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="4abf3-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4abf3-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4abf3-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4abf3-118">See also</span></span>

- [<span data-ttu-id="4abf3-119">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="4abf3-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4abf3-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4abf3-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4abf3-121">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4abf3-121">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="4abf3-122">this</span><span class="sxs-lookup"><span data-stu-id="4abf3-122">this</span></span>](./this.md)
