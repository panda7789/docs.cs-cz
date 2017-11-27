---
title: "Konstanty a výčty v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5bbba6434d8b0a5c02882d1ac858296fd8eeb346
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="9c590-102">Konstanty a výčty v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c590-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="9c590-103">Konstanty představují způsob, jak používat smysluplný názvy místo hodnotu, která se nemění.</span><span class="sxs-lookup"><span data-stu-id="9c590-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="9c590-104">Konstanty ukládat hodnoty, které jak již název napovídá, zůstat konstantní po spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c590-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="9c590-105">Konstanty můžete zadat smysluplný názvy, namísto čísla, provádění kódu lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="9c590-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="9c590-106">Výčty poskytují pohodlný způsob pro práci se sadami související konstanty a přidružení konstantních hodnot k názvy.</span><span class="sxs-lookup"><span data-stu-id="9c590-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="9c590-107">Můžete například deklarovat výčet sady konstanty typu integer, které jsou přidružené k dny v týdnu a pak použít názvy dnů, nikoli jejich celočíselné hodnoty v kódu.</span><span class="sxs-lookup"><span data-stu-id="9c590-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c590-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9c590-108">In This Section</span></span>  
  
|<span data-ttu-id="9c590-109">Termín</span><span class="sxs-lookup"><span data-stu-id="9c590-109">Term</span></span>|<span data-ttu-id="9c590-110">Definice</span><span class="sxs-lookup"><span data-stu-id="9c590-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="9c590-111">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="9c590-111">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)|<span data-ttu-id="9c590-112">Témata v této části popisují konstanty a jejich použití.</span><span class="sxs-lookup"><span data-stu-id="9c590-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="9c590-113">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="9c590-113">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)|<span data-ttu-id="9c590-114">Témata v této části popisují, výčty a jejich použití.</span><span class="sxs-lookup"><span data-stu-id="9c590-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="9c590-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="9c590-115">Related Sections</span></span>  
  
|<span data-ttu-id="9c590-116">Termín</span><span class="sxs-lookup"><span data-stu-id="9c590-116">Term</span></span>|<span data-ttu-id="9c590-117">Definice</span><span class="sxs-lookup"><span data-stu-id="9c590-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="9c590-118">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="9c590-118">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="9c590-119">Popisuje `Const` příkaz, který se používá k deklaraci konstanty.</span><span class="sxs-lookup"><span data-stu-id="9c590-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="9c590-120">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="9c590-120">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)|<span data-ttu-id="9c590-121">Popisuje `Enum` příkaz, který se používá k vytvoření výčty.</span><span class="sxs-lookup"><span data-stu-id="9c590-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="9c590-122">Option Explicit – příkaz</span><span class="sxs-lookup"><span data-stu-id="9c590-122">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="9c590-123">Popisuje `Option Explicit` příkaz, který se používá na úrovni modulu vynutíte explicitní deklaraci všech proměnných v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="9c590-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="9c590-124">Option Infer – příkaz</span><span class="sxs-lookup"><span data-stu-id="9c590-124">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)|<span data-ttu-id="9c590-125">Popisuje `Option Infer` příkaz, který umožňuje použít odvození místního typu v deklarování proměnných.</span><span class="sxs-lookup"><span data-stu-id="9c590-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="9c590-126">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="9c590-126">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="9c590-127">Popisuje `Option Strict` příkaz, který omezuje převody typu implicitní data do pouze rozšiřující převody, zakáže pozdní vazba a zakáže implicitní zadáte, která způsobí, že `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="9c590-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
