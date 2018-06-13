---
title: volatile (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: 7f3aafc1255667f2a3917c6e171ce4ddf0343b41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272581"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="861b9-102">volatile (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="861b9-102">volatile (C# Reference)</span></span>
<span data-ttu-id="861b9-103">`volatile` – Klíčové slovo označuje, že pole mohou být změněna více vláken, které jsou prováděny ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="861b9-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="861b9-104">Pole, které jsou deklarovány `volatile` nevztahují kompilátoru optimalizace, které předpokládá přístup podle jednoho vlákna.</span><span class="sxs-lookup"><span data-stu-id="861b9-104">Fields that are declared `volatile` are not subject to compiler optimizations that assume access by a single thread.</span></span> <span data-ttu-id="861b9-105">Tím se zajistí, že aktuální hodnota je přítomen v poli za všech okolností.</span><span class="sxs-lookup"><span data-stu-id="861b9-105">This ensures that the most up-to-date value is present in the field at all times.</span></span>  
  
 <span data-ttu-id="861b9-106">`volatile` Modifikátor se obvykle používá pro pole, kterému je získat přístup z více vláken bez použití [zámku](../../../csharp/language-reference/keywords/lock-statement.md) příkaz k serializaci přístup.</span><span class="sxs-lookup"><span data-stu-id="861b9-106">The `volatile` modifier is usually used for a field that is accessed by multiple threads without using the [lock](../../../csharp/language-reference/keywords/lock-statement.md) statement to serialize access.</span></span>  
  
 <span data-ttu-id="861b9-107">`volatile` – Klíčové slovo lze použít pro pole těchto typů:</span><span class="sxs-lookup"><span data-stu-id="861b9-107">The `volatile` keyword can be applied to fields of these types:</span></span>  
  
-   <span data-ttu-id="861b9-108">Odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="861b9-108">Reference types.</span></span>  
  
-   <span data-ttu-id="861b9-109">Typy ukazatelů (v kontextu unsafe).</span><span class="sxs-lookup"><span data-stu-id="861b9-109">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="861b9-110">Všimněte si, že i když má ukazatel sám sebe může být volatile, objekt, který odkazuje na nelze.</span><span class="sxs-lookup"><span data-stu-id="861b9-110">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="861b9-111">Jinými slovy nelze deklarovat "ukazatel na volatile."</span><span class="sxs-lookup"><span data-stu-id="861b9-111">In other words, you cannot declare a "pointer to volatile."</span></span>  
  
-   <span data-ttu-id="861b9-112">Typy například SByte –, bajtů, short, ushort –, int, uint, char, float a bool.</span><span class="sxs-lookup"><span data-stu-id="861b9-112">Types such as sbyte, byte, short, ushort, int, uint, char, float, and bool.</span></span>  
  
-   <span data-ttu-id="861b9-113">Typ výčtu s jedním z následujících typů základní: bajtů, sbyte –, short, ushort, int nebo uint.</span><span class="sxs-lookup"><span data-stu-id="861b9-113">An enum type with one of the following base types: byte, sbyte, short, ushort, int, or uint.</span></span>  
  
-   <span data-ttu-id="861b9-114">Parametry obecného typu známé jako odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="861b9-114">Generic type parameters known to be reference types.</span></span>  
  
-   <span data-ttu-id="861b9-115"><xref:System.IntPtr> a <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="861b9-115"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>  
  
 <span data-ttu-id="861b9-116">Volatile – klíčové slovo lze použít pouze na pole třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="861b9-116">The volatile keyword can only be applied to fields of a class or struct.</span></span> <span data-ttu-id="861b9-117">Místní proměnné nelze deklarovat `volatile`.</span><span class="sxs-lookup"><span data-stu-id="861b9-117">Local variables cannot be declared `volatile`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="861b9-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="861b9-118">Example</span></span>  
 <span data-ttu-id="861b9-119">Následující příklad ukazuje, jak deklarovat proměnnou veřejné pole jako `volatile`.</span><span class="sxs-lookup"><span data-stu-id="861b9-119">The following example shows how to declare a public field variable as `volatile`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="861b9-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="861b9-120">Example</span></span>  
 <span data-ttu-id="861b9-121">Následující příklad ukazuje, jak vytvořit a použít k provedení zpracování paralelně s u primární vlákno pomocné nebo pracovní vlákno.</span><span class="sxs-lookup"><span data-stu-id="861b9-121">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="861b9-122">Základní informace o více vláken, viz [zřetězení (C#)](../../../standard/threading/index.md) a [dělení na spravovaná vlákna](../../programming-guide/concepts/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="861b9-122">For background information about multithreading, see [Threading (C#)](../../../standard/threading/index.md) and [Managed Threading](../../programming-guide/concepts/threading/index.md).</span></span>  
  
 [!code-csharp[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="861b9-123">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="861b9-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="861b9-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="861b9-124">See Also</span></span>  
 [<span data-ttu-id="861b9-125">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="861b9-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="861b9-126">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="861b9-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="861b9-127">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="861b9-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="861b9-128">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="861b9-128">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
