---
title: Implicitně typovaná lambda výrazy
description: Zjistěte, proč nelze použít deklaraci proměnné implicitně typované k deklarování výrazů lambda.
ms.date: 06/20/2016
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: 9b798f40676afaad2075806d6dc512f279bc7065
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672078"
---
# <a name="implicitly-typed-lambda-expressions"></a><span data-ttu-id="a88e9-103">Implicitně typovaná lambda výrazy</span><span class="sxs-lookup"><span data-stu-id="a88e9-103">Implicitly typed lambda expressions</span></span>

<span data-ttu-id="a88e9-104">Implicitně typovaná deklarace proměnné nelze použít k deklarování výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="a88e9-104">You can't use an implicitly typed variable declaration to declare a lambda expression.</span></span>
<span data-ttu-id="a88e9-105">Vytvoří problém cyklické logiku pro kompilátor.</span><span class="sxs-lookup"><span data-stu-id="a88e9-105">It creates a circular logic problem for the compiler.</span></span> <span data-ttu-id="a88e9-106">`var` Deklarace instruuje kompilátor, aby zjistit typ proměnné z typu výrazu na pravé straně operátoru přiřazení.</span><span class="sxs-lookup"><span data-stu-id="a88e9-106">The `var` declaration tells the compiler to figure out the type of the variable from the type of expression on the right hand side of the assignment operator.</span></span> <span data-ttu-id="a88e9-107">Výraz lambda nemá typ času kompilace, ale lze převést na odpovídající typ delegáta nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="a88e9-107">A lambda expression does not have a compile time type, but is convertible to any matching delegate or expression type.</span></span> <span data-ttu-id="a88e9-108">Pokud je výraz lambda přiřadit proměnné typu delegát nebo výraz, dáte kompilátoru vyzkoušet a převést výraz lambda výraz nebo delegát, který se shoduje se signaturou přiřazená k proměnné.</span><span class="sxs-lookup"><span data-stu-id="a88e9-108">When you assign a lambda expression to a variable of a delegate or expression type, you tell the compiler to try and convert the lambda expression into an expression or delegate that matches the signature of the 'assigned to' variable.</span></span> <span data-ttu-id="a88e9-109">Kompilátor musí pokusí provést je na pravé straně přiřazení shoda typu přiřazení na levé straně.</span><span class="sxs-lookup"><span data-stu-id="a88e9-109">The compiler must try to make the thing on the right hand side of the assignment match the type on the left hand side of the assignment.</span></span> 

<span data-ttu-id="a88e9-110">Obě strany přiřazení nelze sděluje kompilátoru, aby podívat se na objekt na druhé straně operátoru přiřazení a jestli Moje typ odpovídá.</span><span class="sxs-lookup"><span data-stu-id="a88e9-110">Both sides of the assignment can't be telling the compiler to look at the object on the other side of the assignment operator and see if my type matches.</span></span>

<span data-ttu-id="a88e9-111">Získáte i další podrobnosti o tom, proč jazyka C# určuje chování načtením [v tomto článku](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (Stáhnout soubor PDF)</span><span class="sxs-lookup"><span data-stu-id="a88e9-111">You can get even more details on why the C# language specifies that behavior by reading [this article](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF Download)</span></span>
