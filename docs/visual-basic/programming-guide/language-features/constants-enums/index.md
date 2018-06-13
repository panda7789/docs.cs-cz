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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646380"
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="016f4-102">Konstanty a výčty v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="016f4-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="016f4-103">Konstanty představují způsob, jak používat smysluplný názvy místo hodnotu, která se nemění.</span><span class="sxs-lookup"><span data-stu-id="016f4-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="016f4-104">Konstanty ukládat hodnoty, které jak již název napovídá, zůstat konstantní po spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="016f4-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="016f4-105">Konstanty můžete zadat smysluplný názvy, namísto čísla, provádění kódu lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="016f4-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="016f4-106">Výčty poskytují pohodlný způsob pro práci se sadami související konstanty a přidružení konstantních hodnot k názvy.</span><span class="sxs-lookup"><span data-stu-id="016f4-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="016f4-107">Můžete například deklarovat výčet sady konstanty typu integer, které jsou přidružené k dny v týdnu a pak použít názvy dnů, nikoli jejich celočíselné hodnoty v kódu.</span><span class="sxs-lookup"><span data-stu-id="016f4-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="016f4-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="016f4-108">In This Section</span></span>  
  
|<span data-ttu-id="016f4-109">Termín</span><span class="sxs-lookup"><span data-stu-id="016f4-109">Term</span></span>|<span data-ttu-id="016f4-110">Definice</span><span class="sxs-lookup"><span data-stu-id="016f4-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="016f4-111">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="016f4-111">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)|<span data-ttu-id="016f4-112">Témata v této části popisují konstanty a jejich použití.</span><span class="sxs-lookup"><span data-stu-id="016f4-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="016f4-113">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="016f4-113">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)|<span data-ttu-id="016f4-114">Témata v této části popisují, výčty a jejich použití.</span><span class="sxs-lookup"><span data-stu-id="016f4-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="016f4-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="016f4-115">Related Sections</span></span>  
  
|<span data-ttu-id="016f4-116">Termín</span><span class="sxs-lookup"><span data-stu-id="016f4-116">Term</span></span>|<span data-ttu-id="016f4-117">Definice</span><span class="sxs-lookup"><span data-stu-id="016f4-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="016f4-118">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="016f4-118">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="016f4-119">Popisuje `Const` příkaz, který se používá k deklaraci konstanty.</span><span class="sxs-lookup"><span data-stu-id="016f4-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="016f4-120">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="016f4-120">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)|<span data-ttu-id="016f4-121">Popisuje `Enum` příkaz, který se používá k vytvoření výčty.</span><span class="sxs-lookup"><span data-stu-id="016f4-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="016f4-122">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="016f4-122">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="016f4-123">Popisuje `Option Explicit` příkaz, který se používá na úrovni modulu vynutíte explicitní deklaraci všech proměnných v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="016f4-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="016f4-124">Příkaz Option Infer</span><span class="sxs-lookup"><span data-stu-id="016f4-124">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)|<span data-ttu-id="016f4-125">Popisuje `Option Infer` příkaz, který umožňuje použít odvození místního typu v deklarování proměnných.</span><span class="sxs-lookup"><span data-stu-id="016f4-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="016f4-126">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="016f4-126">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="016f4-127">Popisuje `Option Strict` příkaz, který omezuje převody typu implicitní data do pouze rozšiřující převody, zakáže pozdní vazba a zakáže implicitní zadáte, která způsobí, že `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="016f4-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
