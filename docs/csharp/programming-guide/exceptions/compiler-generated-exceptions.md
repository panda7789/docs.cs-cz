---
title: "Výjimky generované kompilátorem (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d1417e42f588978d5fc1beca4ad55463502ee219
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="460d5-102">Výjimky generované kompilátorem (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="460d5-102">Compiler-Generated Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="460d5-103">Některé výjimky jsou vyvolány automaticky pomocí rozhraní .NET Framework common language runtime (CLR), pokud základní operace s chybou.</span><span class="sxs-lookup"><span data-stu-id="460d5-103">Some exceptions are thrown automatically by the .NET Framework's common language runtime (CLR) when basic operations fail.</span></span> <span data-ttu-id="460d5-104">Tyto výjimky a jejich chybové stavy jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="460d5-104">These exceptions and their error conditions are listed in the following table.</span></span>  
  
|<span data-ttu-id="460d5-105">Výjimka</span><span class="sxs-lookup"><span data-stu-id="460d5-105">Exception</span></span>|<span data-ttu-id="460d5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="460d5-106">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|<span data-ttu-id="460d5-107">Základní třída pro výjimky, které se vyskytnou při aritmetické operace, jako například <xref:System.DivideByZeroException> a <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="460d5-107">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|  
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="460d5-108">Vyvolá, když pole nelze uložit daného elementu, protože skutečný typ elementu není kompatibilní s skutečný typ pole.</span><span class="sxs-lookup"><span data-stu-id="460d5-108">Thrown when an array cannot store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|  
|<xref:System.DivideByZeroException>|<span data-ttu-id="460d5-109">Vyvolá, když je učiněn pokus o hodnotu celočíselné dělení nulou.</span><span class="sxs-lookup"><span data-stu-id="460d5-109">Thrown when an attempt is made to divide an integral value by zero.</span></span>|  
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="460d5-110">Vyvolá, když je proveden pokus o indexu pole při index je menší než nula nebo mimo rozsah pole.</span><span class="sxs-lookup"><span data-stu-id="460d5-110">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|  
|<xref:System.InvalidCastException>|<span data-ttu-id="460d5-111">Vyvolá, když explicitní převod z typu základní rozhraní nebo odvozený typ selže za běhu.</span><span class="sxs-lookup"><span data-stu-id="460d5-111">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|  
|<xref:System.NullReferenceException>|<span data-ttu-id="460d5-112">Při pokusu o odkazují na objekt, jehož hodnota je [null](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="460d5-112">Thrown when you attempt to reference an object whose value is [null](../../../csharp/language-reference/keywords/null.md).</span></span>|  
|<xref:System.OutOfMemoryException>|<span data-ttu-id="460d5-113">Při pokusu o přidělení paměti pomocí [nové](../../../csharp/language-reference/keywords/new-operator.md) operátor selže.</span><span class="sxs-lookup"><span data-stu-id="460d5-113">Thrown when an attempt to allocate memory using the [new](../../../csharp/language-reference/keywords/new-operator.md) operator fails.</span></span> <span data-ttu-id="460d5-114">To znamená, že byl vyčerpán paměti k dispozici pro modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="460d5-114">This indicates that the memory available to the common language runtime has been exhausted.</span></span>|  
|<xref:System.OverflowException>|<span data-ttu-id="460d5-115">Vyvolá, když aritmetické operace v `checked` přeteče mimo kontext.</span><span class="sxs-lookup"><span data-stu-id="460d5-115">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|  
|<xref:System.StackOverflowException>|<span data-ttu-id="460d5-116">Při provádění zásobníku vyčerpá tak, že jsou příliš mnoha volání čekající metoda; obvykle to znamená velmi hloubkové nebo nekonečné rekurzi.</span><span class="sxs-lookup"><span data-stu-id="460d5-116">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|  
|<xref:System.TypeInitializationException>|<span data-ttu-id="460d5-117">Vyvolá, když statického konstruktoru výjimku a kompatibilní `catch` existuje klauzule k zachycení ho.</span><span class="sxs-lookup"><span data-stu-id="460d5-117">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="460d5-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="460d5-118">See Also</span></span>  
 [<span data-ttu-id="460d5-119">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="460d5-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="460d5-120">Výjimky a jejich zpracování</span><span class="sxs-lookup"><span data-stu-id="460d5-120">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)  
 [<span data-ttu-id="460d5-121">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="460d5-121">Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/exception-handling.md)  
 [<span data-ttu-id="460d5-122">try-catch –</span><span class="sxs-lookup"><span data-stu-id="460d5-122">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="460d5-123">try-finally –</span><span class="sxs-lookup"><span data-stu-id="460d5-123">try-finally</span></span>](../../../csharp/language-reference/keywords/try-finally.md)  
 [<span data-ttu-id="460d5-124">try-catch-finally –</span><span class="sxs-lookup"><span data-stu-id="460d5-124">try-catch-finally</span></span>](../../../csharp/language-reference/keywords/try-catch-finally.md)
