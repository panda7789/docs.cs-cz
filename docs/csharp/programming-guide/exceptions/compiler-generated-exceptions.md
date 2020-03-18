---
title: Výjimky generované kompilátorem – programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 2a6b2c3fa053f1c555856df8098975340e78e2b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705311"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="d92ed-102">Výjimky generované kompilátorem (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="d92ed-102">Compiler-Generated Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="d92ed-103">Některé výjimky jsou vyvolány automaticky v rámci .NET Framework je společný jazyk runtime (CLR) při selhání základní operace.</span><span class="sxs-lookup"><span data-stu-id="d92ed-103">Some exceptions are thrown automatically by the .NET Framework's common language runtime (CLR) when basic operations fail.</span></span> <span data-ttu-id="d92ed-104">Tyto výjimky a jejich chybové stavy jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="d92ed-104">These exceptions and their error conditions are listed in the following table.</span></span>  
  
|<span data-ttu-id="d92ed-105">Výjimka</span><span class="sxs-lookup"><span data-stu-id="d92ed-105">Exception</span></span>|<span data-ttu-id="d92ed-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d92ed-106">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|<span data-ttu-id="d92ed-107">Základní třída pro výjimky, ke kterým dochází během <xref:System.DivideByZeroException> <xref:System.OverflowException>aritmetických operací, například a .</span><span class="sxs-lookup"><span data-stu-id="d92ed-107">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|  
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="d92ed-108">Vyvolána, když pole nelze uložit daný prvek, protože skutečný typ prvku je nekompatibilní s aktuální typ pole.</span><span class="sxs-lookup"><span data-stu-id="d92ed-108">Thrown when an array cannot store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|  
|<xref:System.DivideByZeroException>|<span data-ttu-id="d92ed-109">Vyvolána při pokusu o rozdělení integrální hodnoty nulou.</span><span class="sxs-lookup"><span data-stu-id="d92ed-109">Thrown when an attempt is made to divide an integral value by zero.</span></span>|  
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="d92ed-110">Vyvolána při pokusu o index pole, pokud je index menší než nula nebo mimo hranice pole.</span><span class="sxs-lookup"><span data-stu-id="d92ed-110">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|  
|<xref:System.InvalidCastException>|<span data-ttu-id="d92ed-111">Vyvolána při explicitní převod ze základního typu do rozhraní nebo odvozeného typu selže za běhu.</span><span class="sxs-lookup"><span data-stu-id="d92ed-111">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|  
|<xref:System.NullReferenceException>|<span data-ttu-id="d92ed-112">Vyvolána při pokusu o odkaz na objekt, jehož hodnota je [null](../../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="d92ed-112">Thrown when an attempt is made to reference an object whose value is [null](../../language-reference/keywords/null.md).</span></span>|  
|<xref:System.OutOfMemoryException>|<span data-ttu-id="d92ed-113">Vyvolána při pokusu o přidělení paměti pomocí [nového](../../language-reference/operators/new-operator.md) operátoru se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="d92ed-113">Thrown when an attempt to allocate memory using the [new](../../language-reference/operators/new-operator.md) operator fails.</span></span> <span data-ttu-id="d92ed-114">To znamená, že paměť dostupná pro běžný jazyk runtime byla vyčerpána.</span><span class="sxs-lookup"><span data-stu-id="d92ed-114">This indicates that the memory available to the common language runtime has been exhausted.</span></span>|  
|<xref:System.OverflowException>|<span data-ttu-id="d92ed-115">Vyvolána při aritmetické operace `checked` v kontextu přetečení.</span><span class="sxs-lookup"><span data-stu-id="d92ed-115">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|  
|<xref:System.StackOverflowException>|<span data-ttu-id="d92ed-116">Vyvolána při spuštění zásobníku je vyčerpán tím, že příliš mnoho čekající volání metody; obvykle označuje velmi hlubokou nebo nekonečnou rekurzi.</span><span class="sxs-lookup"><span data-stu-id="d92ed-116">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|  
|<xref:System.TypeInitializationException>|<span data-ttu-id="d92ed-117">Vyvolána, když statický konstruktor vyvolá výjimku a neexistuje žádná kompatibilní `catch` klauzule, která by ji zachytila.</span><span class="sxs-lookup"><span data-stu-id="d92ed-117">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d92ed-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="d92ed-118">See also</span></span>

- [<span data-ttu-id="d92ed-119">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d92ed-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d92ed-120">Výjimky a zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="d92ed-120">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="d92ed-121">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="d92ed-121">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="d92ed-122">try-catch</span><span class="sxs-lookup"><span data-stu-id="d92ed-122">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="d92ed-123">try-finally</span><span class="sxs-lookup"><span data-stu-id="d92ed-123">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="d92ed-124">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="d92ed-124">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
