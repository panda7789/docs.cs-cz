---
title: Implicitně typované výrazy lambda
description: Zjistěte, proč nemůžete použít deklaraci proměnné s implicitním typem k deklaraci výrazu lambda.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: cf16bb4d9ed27f536ae163284f36a0f305877139
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713891"
---
# <a name="implicitly-typed-lambda-expressions"></a><span data-ttu-id="2900e-103">Implicitně typované výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="2900e-103">Implicitly typed lambda expressions</span></span>

<span data-ttu-id="2900e-104">Deklaraci proměnné s implicitním typem nelze použít k deklaraci výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="2900e-104">You can't use an implicitly typed variable declaration to declare a lambda expression.</span></span>
<span data-ttu-id="2900e-105">Vytvoří kruhovou logickou potíž pro kompilátor.</span><span class="sxs-lookup"><span data-stu-id="2900e-105">It creates a circular logic problem for the compiler.</span></span> <span data-ttu-id="2900e-106">Deklarace `var` instruuje kompilátor, aby typ proměnné z typu výrazu na pravé straně operátoru přiřazení.</span><span class="sxs-lookup"><span data-stu-id="2900e-106">The `var` declaration tells the compiler to figure out the type of the variable from the type of expression on the right hand side of the assignment operator.</span></span> <span data-ttu-id="2900e-107">Výraz lambda nemá typ doby kompilace, ale je převoditelný na libovolný typ odpovídajícího delegáta nebo výrazu.</span><span class="sxs-lookup"><span data-stu-id="2900e-107">A lambda expression does not have a compile time type, but is convertible to any matching delegate or expression type.</span></span> <span data-ttu-id="2900e-108">Když přiřadíte výraz lambda proměnné delegáta nebo typu výrazu, říkáte kompilátoru, aby vyzkoušel a převedl výraz lambda na výraz nebo delegáta, který odpovídá podpisu proměnné "přiřazeno".</span><span class="sxs-lookup"><span data-stu-id="2900e-108">When you assign a lambda expression to a variable of a delegate or expression type, you tell the compiler to try and convert the lambda expression into an expression or delegate that matches the signature of the 'assigned to' variable.</span></span> <span data-ttu-id="2900e-109">Kompilátor se musí pokusit na pravé straně přiřazení, aby odpovídal typu na levé straně přiřazení.</span><span class="sxs-lookup"><span data-stu-id="2900e-109">The compiler must try to make the thing on the right hand side of the assignment match the type on the left hand side of the assignment.</span></span> 

<span data-ttu-id="2900e-110">Na obou stranách přiřazení nelze kompilátor sdělit, aby procházel na objektu na druhé straně operátoru přiřazení a viděli, zda odpovídá typ.</span><span class="sxs-lookup"><span data-stu-id="2900e-110">Both sides of the assignment can't be telling the compiler to look at the object on the other side of the assignment operator and see if my type matches.</span></span>

<span data-ttu-id="2900e-111">Můžete získat ještě více podrobností o tom, proč C# jazyk určuje chování tak, že si přečte [Tento článek](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (stažení PDF).</span><span class="sxs-lookup"><span data-stu-id="2900e-111">You can get even more details on why the C# language specifies that behavior by reading [this article](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF download).</span></span>
