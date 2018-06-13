---
title: Implicitně typovaná lambda – výrazy
description: Zjistěte, proč nelze používat deklarace proměnné implicitně typované deklarovat výrazu lambda.
ms.date: 06/20/2016
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: f06c55f51c30c941d6d507ac8e2edd95c5152742
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33211820"
---
# <a name="implicitly-typed-lambda-expressions"></a><span data-ttu-id="62a1f-103">Implicitně typovaná lambda – výrazy</span><span class="sxs-lookup"><span data-stu-id="62a1f-103">Implicitly typed lambda expressions</span></span>

<span data-ttu-id="62a1f-104">Nepoužívám `var` deklarovat tento strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="62a1f-104">I'm not using `var` to declare this expression tree.</span></span> <span data-ttu-id="62a1f-105">Nelze použít implicitně typovaná deklarace proměnné deklarovat výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="62a1f-105">You can't use an implicitly typed variable declaration to declare a lambda expression.</span></span>
<span data-ttu-id="62a1f-106">Vytvoří problém cyklické logiku pro kompilátor.</span><span class="sxs-lookup"><span data-stu-id="62a1f-106">It creates a circular logic problem for the compiler.</span></span> <span data-ttu-id="62a1f-107">`var` Deklarace říká kompilátoru a pokuste se zjistit typ proměnné z typ výrazu na pravé straně operátoru přiřazení.</span><span class="sxs-lookup"><span data-stu-id="62a1f-107">The `var` declaration tells the compiler to figure out the type of the variable from the type of expression on the right hand side of the assignment operator.</span></span> <span data-ttu-id="62a1f-108">Výraz lambda nemá typu time kompilace, ale je převést na odpovídající typ delegáta nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="62a1f-108">A lambda expression does not have a compile time type, but is convertible to any matching delegate or expression type.</span></span> <span data-ttu-id="62a1f-109">Když přiřazujete výrazu lambda proměnné typu delegáta nebo výraz, se zjistit kompilátoru a zkuste to převést výrazu lambda delegáta, který odpovídá podpis přiřazené k proměnné nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="62a1f-109">When you assign a lambda expression to a variable of a delegate or expression type, you tell the compiler to try and convert the lambda expression into an expression or delegate that matches the signature of the 'assigned to' variable.</span></span> <span data-ttu-id="62a1f-110">Kompilátor musí pokusit zkontrolujte je věcí na pravé straně přiřazení shody typ na levé straně přiřazení.</span><span class="sxs-lookup"><span data-stu-id="62a1f-110">The compiler must try to make the thing on the right hand side of the assignment match the type on the left hand side of the assignment.</span></span> 

<span data-ttu-id="62a1f-111">Oba konce přiřazení nelze informuje kompilátor podívejte se na objekt na druhé straně operátoru přiřazení a jestli odpovídá vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="62a1f-111">Both sides of the assignment can't be telling the compiler to look at the object on the other side of the assignment operator and see if my type matches.</span></span>

<span data-ttu-id="62a1f-112">Můžete získat i další podrobnost, proč jazyka C# určuje tohoto chování načtením [v tomto článku](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (Stáhnout PDF)</span><span class="sxs-lookup"><span data-stu-id="62a1f-112">You can get even more details on why the C# language specifies that behavior by reading [this article](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF Download)</span></span>


