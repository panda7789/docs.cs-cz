---
title: volatile (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: 64bd5ce7d7dfe3265c3c645467493ab7d8792172
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37936875"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="e78ff-102">volatile (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e78ff-102">volatile (C# Reference)</span></span>
<span data-ttu-id="e78ff-103">`volatile` – Klíčové slovo určuje, že pole může být upraveno ve víc vláknech, které jsou spuštěny ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="e78ff-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="e78ff-104">Pole, které jsou deklarovány `volatile` se nevyprázdňuje optimalizace kompilátoru, které se předpokládá přístup podle jednoho vlákna.</span><span class="sxs-lookup"><span data-stu-id="e78ff-104">Fields that are declared `volatile` are not subject to compiler optimizations that assume access by a single thread.</span></span> <span data-ttu-id="e78ff-105">Tato omezení Ujistěte se, že všechna vlákna budou sledovat volatile zápisy provádí ostatní vlákna v pořadí, ve kterém byly provedeny.</span><span class="sxs-lookup"><span data-stu-id="e78ff-105">These restrictions ensure that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="e78ff-106">Není zaručeno jeden celkový řazení volatile zápisů pohledu ze všech vláken, která.</span><span class="sxs-lookup"><span data-stu-id="e78ff-106">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>  
  
 <span data-ttu-id="e78ff-107">`volatile` Modifikátor se obvykle používá pro pole, které je přístup prostřednictvím více vláken bez použití [Zámek](../../../csharp/language-reference/keywords/lock-statement.md) příkaz k serializaci přístup.</span><span class="sxs-lookup"><span data-stu-id="e78ff-107">The `volatile` modifier is usually used for a field that is accessed by multiple threads without using the [lock](../../../csharp/language-reference/keywords/lock-statement.md) statement to serialize access.</span></span>  
  
 <span data-ttu-id="e78ff-108">`volatile` – Klíčové slovo lze použít u polí těchto typů:</span><span class="sxs-lookup"><span data-stu-id="e78ff-108">The `volatile` keyword can be applied to fields of these types:</span></span>  
  
-   <span data-ttu-id="e78ff-109">Typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="e78ff-109">Reference types.</span></span>  
  
-   <span data-ttu-id="e78ff-110">Typy ukazatelů (v nezabezpečeném kontextu.).</span><span class="sxs-lookup"><span data-stu-id="e78ff-110">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="e78ff-111">Všimněte si, že i když se ukazatel sám, může být typu volatile, objekt, který odkazuje na nelze.</span><span class="sxs-lookup"><span data-stu-id="e78ff-111">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="e78ff-112">Jinými slovy nelze deklarovat "ukazatel na volatile."</span><span class="sxs-lookup"><span data-stu-id="e78ff-112">In other words, you cannot declare a "pointer to volatile."</span></span>  
  
-   <span data-ttu-id="e78ff-113">Typy, jako je například sbyte, byte, short, ushort, int, uint, char, float a bool.</span><span class="sxs-lookup"><span data-stu-id="e78ff-113">Types such as sbyte, byte, short, ushort, int, uint, char, float, and bool.</span></span>  
  
-   <span data-ttu-id="e78ff-114">Typ výčtu s jedním z následujících základních typů: byte, sbyte, short, ushort, int nebo uint.</span><span class="sxs-lookup"><span data-stu-id="e78ff-114">An enum type with one of the following base types: byte, sbyte, short, ushort, int, or uint.</span></span>  
  
-   <span data-ttu-id="e78ff-115">Parametry obecného typu známé jako referenční typy.</span><span class="sxs-lookup"><span data-stu-id="e78ff-115">Generic type parameters known to be reference types.</span></span>  
  
-   <span data-ttu-id="e78ff-116"><xref:System.IntPtr> a <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="e78ff-116"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>  
  
 <span data-ttu-id="e78ff-117">Volatile – klíčové slovo lze použít pouze pro pole třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="e78ff-117">The volatile keyword can only be applied to fields of a class or struct.</span></span> <span data-ttu-id="e78ff-118">Místní proměnné nelze použít deklaraci `volatile`.</span><span class="sxs-lookup"><span data-stu-id="e78ff-118">Local variables cannot be declared `volatile`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e78ff-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="e78ff-119">Example</span></span>  
 <span data-ttu-id="e78ff-120">Následující příklad ukazuje, jak deklarovat proměnnou veřejné pole jako `volatile`.</span><span class="sxs-lookup"><span data-stu-id="e78ff-120">The following example shows how to declare a public field variable as `volatile`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="e78ff-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="e78ff-121">Example</span></span>  
 <span data-ttu-id="e78ff-122">Následující příklad ukazuje, jak můžete vytvořit a používá ke zpracování paralelní s ním primární vlákno pomocné nebo pracovní vlákno.</span><span class="sxs-lookup"><span data-stu-id="e78ff-122">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="e78ff-123">Základní informace o multithreading, viz [dělení na spravovaná vlákna](../../../standard/threading/index.md) a [zřetězení (C#)](../../programming-guide/concepts/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="e78ff-123">For background information about multithreading, see [Managed Threading](../../../standard/threading/index.md) and [Threading (C#)](../../programming-guide/concepts/threading/index.md).</span></span>  
  
 [!code-csharp[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="e78ff-124">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e78ff-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e78ff-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="e78ff-125">See Also</span></span>  
 [<span data-ttu-id="e78ff-126">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e78ff-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e78ff-127">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e78ff-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e78ff-128">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e78ff-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e78ff-129">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="e78ff-129">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
