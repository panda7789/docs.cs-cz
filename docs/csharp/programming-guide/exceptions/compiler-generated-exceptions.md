---
title: Výjimky generované kompilátorem – Průvodce programováním v C#
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 1d2d561df3e496893657b050fa93b44c56542d97
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240727"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="e7631-102">Výjimky generované kompilátorem (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="e7631-102">Compiler-Generated Exceptions (C# Programming Guide)</span></span>

<span data-ttu-id="e7631-103">Některé výjimky jsou vyvolány automaticky modulem runtime .NET, pokud základní operace selžou.</span><span class="sxs-lookup"><span data-stu-id="e7631-103">Some exceptions are thrown automatically by the .NET runtime when basic operations fail.</span></span> <span data-ttu-id="e7631-104">Tyto výjimky a jejich chybové podmínky jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="e7631-104">These exceptions and their error conditions are listed in the following table.</span></span>  
  
|<span data-ttu-id="e7631-105">Výjimka</span><span class="sxs-lookup"><span data-stu-id="e7631-105">Exception</span></span>|<span data-ttu-id="e7631-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e7631-106">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|<span data-ttu-id="e7631-107">Základní třída pro výjimky, ke kterým dochází během aritmetických operací, jako například <xref:System.DivideByZeroException> a <xref:System.OverflowException> .</span><span class="sxs-lookup"><span data-stu-id="e7631-107">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|  
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="e7631-108">Vyvolána, když pole nemůže uložit daný element, protože skutečný typ elementu je nekompatibilní se skutečným typem pole.</span><span class="sxs-lookup"><span data-stu-id="e7631-108">Thrown when an array cannot store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|  
|<xref:System.DivideByZeroException>|<span data-ttu-id="e7631-109">Vyvolána při pokusu o rozdělení celočíselné hodnoty nulou.</span><span class="sxs-lookup"><span data-stu-id="e7631-109">Thrown when an attempt is made to divide an integral value by zero.</span></span>|  
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="e7631-110">Vyvolána při pokusu o indexování pole, když je index menší než nula nebo mimo hranice pole.</span><span class="sxs-lookup"><span data-stu-id="e7631-110">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|  
|<xref:System.InvalidCastException>|<span data-ttu-id="e7631-111">Vyvolá se v případě, že při spuštění dojde k chybě explicitního převodu ze základního typu na rozhraní nebo na odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="e7631-111">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|  
|<xref:System.NullReferenceException>|<span data-ttu-id="e7631-112">Vyvolána, když se provede pokus o odkaz na objekt, jehož hodnota je [null](../../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="e7631-112">Thrown when an attempt is made to reference an object whose value is [null](../../language-reference/keywords/null.md).</span></span>|  
|<xref:System.OutOfMemoryException>|<span data-ttu-id="e7631-113">Vyvolá se v případě, že pokus o přidělení paměti pomocí operátoru [New](../../language-reference/operators/new-operator.md) se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="e7631-113">Thrown when an attempt to allocate memory using the [new](../../language-reference/operators/new-operator.md) operator fails.</span></span> <span data-ttu-id="e7631-114">To znamená, že byla vyčerpána paměť dostupná pro modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="e7631-114">This indicates that the memory available to the common language runtime has been exhausted.</span></span>|  
|<xref:System.OverflowException>|<span data-ttu-id="e7631-115">Vyvolána, pokud dojde k přetečení aritmetické operace v `checked` kontextu.</span><span class="sxs-lookup"><span data-stu-id="e7631-115">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|  
|<xref:System.StackOverflowException>|<span data-ttu-id="e7631-116">Vyvoláno při vyčerpání zásobníku spouštění pomocí příliš velkého počtu volání metod, které čekají na zpracování; obvykle označuje velmi hlubokou nebo nekonečnou rekurzi.</span><span class="sxs-lookup"><span data-stu-id="e7631-116">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|  
|<xref:System.TypeInitializationException>|<span data-ttu-id="e7631-117">Vyvolána, když statický konstruktor vyvolá výjimku a neexistuje žádná kompatibilní `catch` klauzule pro zachycení.</span><span class="sxs-lookup"><span data-stu-id="e7631-117">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7631-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7631-118">See also</span></span>

- [<span data-ttu-id="e7631-119">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="e7631-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e7631-120">Výjimky a jejich zpracování</span><span class="sxs-lookup"><span data-stu-id="e7631-120">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="e7631-121">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="e7631-121">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="e7631-122">try-catch</span><span class="sxs-lookup"><span data-stu-id="e7631-122">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="e7631-123">try-finally</span><span class="sxs-lookup"><span data-stu-id="e7631-123">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="e7631-124">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="e7631-124">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
