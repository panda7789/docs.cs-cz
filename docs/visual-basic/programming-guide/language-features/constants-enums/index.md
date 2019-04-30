---
title: Konstanty a výčty v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- Visual Basic code, constants
- constants [Visual Basic]
- object libraries, Object Browser
- Visual Basic code, enumerations
- declaring constants [Visual Basic], enumerations
- naming conventions [Visual Basic], constants
- Visual Basic code, improving readability with constants
ms.assetid: c8aba36e-fa47-4a33-8b68-cb2009218270
ms.openlocfilehash: dfd9330210dd748d739cd8da2985795099beacd8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907293"
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="e6495-102">Konstanty a výčty v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e6495-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="e6495-103">Konstanty jsou způsob, jak použijte smysluplné názvy místo hodnotu, která se nezmění.</span><span class="sxs-lookup"><span data-stu-id="e6495-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="e6495-104">Konstanty ukládání hodnot, které, jak již název napovídá, zůstanou neměnný po celou dobu spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="e6495-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="e6495-105">Konstanty slouží k poskytování smysluplné názvy, namísto čísla, aby váš kód lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="e6495-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="e6495-106">Výčty poskytují pohodlný způsob pro práci se sadami související s konstantami a přidružení konstantních hodnot s názvy.</span><span class="sxs-lookup"><span data-stu-id="e6495-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="e6495-107">Můžete třeba deklarovat výčet sady konstanty typu integer, které jsou spojené s dny v týdnu a potom použít názvy dní, namísto jejich celočíselných hodnot ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="e6495-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e6495-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e6495-108">In This Section</span></span>  
  
|<span data-ttu-id="e6495-109">Termín</span><span class="sxs-lookup"><span data-stu-id="e6495-109">Term</span></span>|<span data-ttu-id="e6495-110">Definice</span><span class="sxs-lookup"><span data-stu-id="e6495-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="e6495-111">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="e6495-111">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)|<span data-ttu-id="e6495-112">Témata v této části popisují, konstanty a jejich použití.</span><span class="sxs-lookup"><span data-stu-id="e6495-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="e6495-113">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="e6495-113">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)|<span data-ttu-id="e6495-114">Témata v této části popisují, výčty a jejich použití.</span><span class="sxs-lookup"><span data-stu-id="e6495-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="e6495-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="e6495-115">Related Sections</span></span>  
  
|<span data-ttu-id="e6495-116">Termín</span><span class="sxs-lookup"><span data-stu-id="e6495-116">Term</span></span>|<span data-ttu-id="e6495-117">Definice</span><span class="sxs-lookup"><span data-stu-id="e6495-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="e6495-118">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="e6495-118">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="e6495-119">Popisuje `Const` příkaz, který se používá k deklaraci konstanty.</span><span class="sxs-lookup"><span data-stu-id="e6495-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="e6495-120">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="e6495-120">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)|<span data-ttu-id="e6495-121">Popisuje `Enum` příkaz, který se používá k vytvoření výčtů.</span><span class="sxs-lookup"><span data-stu-id="e6495-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="e6495-122">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="e6495-122">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="e6495-123">Popisuje `Option Explicit` příkaz, který se používá na úrovni modulu vynutit explicitní deklaraci všech proměnných v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="e6495-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="e6495-124">Příkaz Option Infer</span><span class="sxs-lookup"><span data-stu-id="e6495-124">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)|<span data-ttu-id="e6495-125">Popisuje `Option Infer` příkaz, který umožňuje použití odvození místního typu v deklarujících proměnných.</span><span class="sxs-lookup"><span data-stu-id="e6495-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="e6495-126">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="e6495-126">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="e6495-127">Popisuje `Option Strict` příkazu, který omezí implicitní převody typů dat jenom na rozšiřující převody, nepovoluje pozdní vazbu a zakazuje implicitního zápisu, která vede `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="e6495-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
