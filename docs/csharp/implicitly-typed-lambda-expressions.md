---
title: Implicitně zadané lambda výrazy
description: Zjistěte, proč nelze použít implicitně zadávanou deklaraci proměnné k deklarování výrazu lambda.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: ef437ef961210290db4150a8a5cfb70e01aee958
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145719"
---
# <a name="implicitly-typed-lambda-expressions"></a><span data-ttu-id="65779-103">Implicitně zadané lambda výrazy</span><span class="sxs-lookup"><span data-stu-id="65779-103">Implicitly typed lambda expressions</span></span>

<span data-ttu-id="65779-104">Implicitně zadávanou deklaraci proměnné nelze použít k deklarování výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="65779-104">You can't use an implicitly typed variable declaration to declare a lambda expression.</span></span>
<span data-ttu-id="65779-105">Vytvoří cyklický logický problém pro kompilátor.</span><span class="sxs-lookup"><span data-stu-id="65779-105">It creates a circular logic problem for the compiler.</span></span> <span data-ttu-id="65779-106">Deklarace `var` říká kompilátoru zjistit typ proměnné z typu výrazu na pravé straně operátoru přiřazení.</span><span class="sxs-lookup"><span data-stu-id="65779-106">The `var` declaration tells the compiler to figure out the type of the variable from the type of expression on the right hand side of the assignment operator.</span></span> <span data-ttu-id="65779-107">Výraz lambda nemá typ času kompilace, ale je konvertibilní s libovolným odpovídajícím delegátem nebo typem výrazu.</span><span class="sxs-lookup"><span data-stu-id="65779-107">A lambda expression does not have a compile time type, but is convertible to any matching delegate or expression type.</span></span> <span data-ttu-id="65779-108">Když přiřadíte výraz lambda proměnné delegáta nebo typu výrazu, sdělíte kompilátoru, aby se pokusil převést výraz lambda na výraz nebo delegáta, který odpovídá podpisu proměnné přiřazeno.</span><span class="sxs-lookup"><span data-stu-id="65779-108">When you assign a lambda expression to a variable of a delegate or expression type, you tell the compiler to try and convert the lambda expression into an expression or delegate that matches the signature of the 'assigned to' variable.</span></span> <span data-ttu-id="65779-109">Kompilátor se musí pokusit, aby věc na pravé straně přiřazení odpovídala typu na levé straně přiřazení.</span><span class="sxs-lookup"><span data-stu-id="65779-109">The compiler must try to make the thing on the right hand side of the assignment match the type on the left hand side of the assignment.</span></span>

<span data-ttu-id="65779-110">Obě strany přiřazení nemůže být říkat kompilátoru podívat se na objekt na druhé straně operátoru přiřazení a zjistěte, zda můj typ odpovídá.</span><span class="sxs-lookup"><span data-stu-id="65779-110">Both sides of the assignment can't be telling the compiler to look at the object on the other side of the assignment operator and see if my type matches.</span></span>

<span data-ttu-id="65779-111">Můžete získat ještě více podrobností o tom, proč jazyk C# určuje, že chování čtením [tohoto článku](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF ke stažení).</span><span class="sxs-lookup"><span data-stu-id="65779-111">You can get even more details on why the C# language specifies that behavior by reading [this article](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF download).</span></span>
