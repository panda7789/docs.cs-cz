---
title: Konstanty a výčty
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
ms.openlocfilehash: 858f22df26d44f47848921ee862c1d4c1ca1fc60
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353987"
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="a6a04-102">Konstanty a výčty v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a6a04-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="a6a04-103">Konstanty představují způsob, jak použít smysluplné názvy místo hodnoty, která se nemění.</span><span class="sxs-lookup"><span data-stu-id="a6a04-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="a6a04-104">Konstanty ukládají hodnoty, které jako název implikují, zůstávají během provádění aplikace konstantní.</span><span class="sxs-lookup"><span data-stu-id="a6a04-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="a6a04-105">Můžete použít konstanty k poskytnutí smysluplných názvů namísto čísel, aby byl kód čitelnější.</span><span class="sxs-lookup"><span data-stu-id="a6a04-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="a6a04-106">Výčty poskytují pohodlný způsob práce se sadami souvisejících konstant a k přidružení konstantních hodnot k názvům.</span><span class="sxs-lookup"><span data-stu-id="a6a04-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="a6a04-107">Můžete například deklarovat výčet pro sadu celočíselných konstant přidružených ke dnům v týdnu a potom použít názvy dnů, nikoli jejich celočíselné hodnoty ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="a6a04-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6a04-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a6a04-108">In This Section</span></span>  
  
|<span data-ttu-id="a6a04-109">Termín</span><span class="sxs-lookup"><span data-stu-id="a6a04-109">Term</span></span>|<span data-ttu-id="a6a04-110">Definice</span><span class="sxs-lookup"><span data-stu-id="a6a04-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="a6a04-111">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="a6a04-111">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)|<span data-ttu-id="a6a04-112">Témata v této části popisují konstanty a jejich použití.</span><span class="sxs-lookup"><span data-stu-id="a6a04-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="a6a04-113">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="a6a04-113">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)|<span data-ttu-id="a6a04-114">Témata v této části popisují výčty a jejich použití.</span><span class="sxs-lookup"><span data-stu-id="a6a04-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="a6a04-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a6a04-115">Related Sections</span></span>  
  
|<span data-ttu-id="a6a04-116">Termín</span><span class="sxs-lookup"><span data-stu-id="a6a04-116">Term</span></span>|<span data-ttu-id="a6a04-117">Definice</span><span class="sxs-lookup"><span data-stu-id="a6a04-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="a6a04-118">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="a6a04-118">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="a6a04-119">Popisuje příkaz `Const`, který slouží k deklaraci konstant.</span><span class="sxs-lookup"><span data-stu-id="a6a04-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="a6a04-120">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="a6a04-120">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)|<span data-ttu-id="a6a04-121">Popisuje příkaz `Enum`, který se používá k vytváření výčtů.</span><span class="sxs-lookup"><span data-stu-id="a6a04-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="a6a04-122">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="a6a04-122">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="a6a04-123">Popisuje příkaz `Option Explicit`, který se používá na úrovni modulu k vynucení explicitní deklarace všech proměnných v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="a6a04-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="a6a04-124">Příkaz Option Infer</span><span class="sxs-lookup"><span data-stu-id="a6a04-124">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)|<span data-ttu-id="a6a04-125">Popisuje příkaz `Option Infer`, který umožňuje použití odvození místního typu v deklaraci proměnných.</span><span class="sxs-lookup"><span data-stu-id="a6a04-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="a6a04-126">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="a6a04-126">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="a6a04-127">Popisuje příkaz `Option Strict`, který omezuje implicitní převody datových typů pouze na rozšiřování převodů, nepovoluje pozdní vazbu a nepovoluje implicitní psaní, které má za následek `Object` typ.</span><span class="sxs-lookup"><span data-stu-id="a6a04-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
