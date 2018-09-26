---
title: Base – klíčové slovo (referenční dokumentace jazyka C#)
description: Další informace o základní klíčové slovo, které se používá pro přístup ke členům základní třídy z odvozené třídy v jazyce C#.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: 8719ab79273701173530760ad1bec837c4f4302d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077879"
---
# <a name="base-c-reference"></a><span data-ttu-id="91f7a-103">base (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="91f7a-103">base (C# Reference)</span></span>

<span data-ttu-id="91f7a-104">`base` – Klíčové slovo se používá pro přístup ke členům základní třídy z odvozené třídy:</span><span class="sxs-lookup"><span data-stu-id="91f7a-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="91f7a-105">Volejte metodu v základní třídě, který se přepsal jinou metodu.</span><span class="sxs-lookup"><span data-stu-id="91f7a-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="91f7a-106">Zadejte konstruktoru základní třídy, který by měla být volána při vytváření instance odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="91f7a-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="91f7a-107">Přístup základní třídy je povolený jenom v konstruktoru, metodu instance nebo přistupující objekt vlastnosti instance.</span><span class="sxs-lookup"><span data-stu-id="91f7a-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="91f7a-108">Jedná se o chybu používat `base` – klíčové slovo z v rámci statické metody.</span><span class="sxs-lookup"><span data-stu-id="91f7a-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="91f7a-109">Základní třída, která se využívají je základní třída zadaná v deklaraci třídy.</span><span class="sxs-lookup"><span data-stu-id="91f7a-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="91f7a-110">Pokud zadáte například `class ClassB : ClassA`, jsou přístupné členy ClassA od ClassB, bez ohledu na základní třídu ClassA.</span><span class="sxs-lookup"><span data-stu-id="91f7a-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="91f7a-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="91f7a-111">Example</span></span>

<span data-ttu-id="91f7a-112">V tomto příkladu i základní třídy, `Person`a odvozená třída `Employee`, měl odpovídající metodu s názvem `Getinfo`.</span><span class="sxs-lookup"><span data-stu-id="91f7a-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="91f7a-113">S použitím `base` – klíčové slovo, je možné volat `Getinfo` metodu v základní třídě, v rámci odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="91f7a-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

<span data-ttu-id="91f7a-114">Další příklady najdete v tématu [nové](../../../csharp/language-reference/keywords/new.md), [virtuální](../../../csharp/language-reference/keywords/virtual.md), a [přepsat](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="91f7a-114">For additional examples, see [new](../../../csharp/language-reference/keywords/new.md), [virtual](../../../csharp/language-reference/keywords/virtual.md), and [override](../../../csharp/language-reference/keywords/override.md).</span></span>

## <a name="example"></a><span data-ttu-id="91f7a-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="91f7a-115">Example</span></span>

<span data-ttu-id="91f7a-116">Tento příklad ukazuje, jak určit konstruktor základní třídy, volá se při vytváření instance odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="91f7a-116">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="91f7a-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="91f7a-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="91f7a-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91f7a-118">See also</span></span>

- [<span data-ttu-id="91f7a-119">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="91f7a-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="91f7a-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="91f7a-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="91f7a-121">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="91f7a-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="91f7a-122">this</span><span class="sxs-lookup"><span data-stu-id="91f7a-122">this</span></span>](../../../csharp/language-reference/keywords/this.md)