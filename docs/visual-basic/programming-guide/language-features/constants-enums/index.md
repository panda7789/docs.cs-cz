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
ms.openlocfilehash: 7d15c46c0f6bb00c23dd98e464f61a5f94b0773a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414399"
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="0ec1e-102">Konstanty a výčty v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0ec1e-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="0ec1e-103">Konstanty představují způsob, jak použít smysluplné názvy místo hodnoty, která se nemění.</span><span class="sxs-lookup"><span data-stu-id="0ec1e-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="0ec1e-104">Konstanty ukládají hodnoty, které jako název implikují, zůstávají během provádění aplikace konstantní.</span><span class="sxs-lookup"><span data-stu-id="0ec1e-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="0ec1e-105">Můžete použít konstanty k poskytnutí smysluplných názvů namísto čísel, aby byl kód čitelnější.</span><span class="sxs-lookup"><span data-stu-id="0ec1e-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="0ec1e-106">Výčty poskytují pohodlný způsob práce se sadami souvisejících konstant a k přidružení konstantních hodnot k názvům.</span><span class="sxs-lookup"><span data-stu-id="0ec1e-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="0ec1e-107">Můžete například deklarovat výčet pro sadu celočíselných konstant přidružených ke dnům v týdnu a potom použít názvy dnů, nikoli jejich celočíselné hodnoty ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="0ec1e-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0ec1e-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0ec1e-108">In This Section</span></span>  
  
|<span data-ttu-id="0ec1e-109">Pojem</span><span class="sxs-lookup"><span data-stu-id="0ec1e-109">Term</span></span>|<span data-ttu-id="0ec1e-110">Definice</span><span class="sxs-lookup"><span data-stu-id="0ec1e-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="0ec1e-111">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="0ec1e-111">Constants Overview</span></span>](constants-overview.md)|<span data-ttu-id="0ec1e-112">Témata v této části popisují konstanty a jejich použití.</span><span class="sxs-lookup"><span data-stu-id="0ec1e-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="0ec1e-113">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="0ec1e-113">Enumerations Overview</span></span>](enumerations-overview.md)|<span data-ttu-id="0ec1e-114">Témata v této části popisují výčty a jejich použití.</span><span class="sxs-lookup"><span data-stu-id="0ec1e-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="0ec1e-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0ec1e-115">Related Sections</span></span>  
  
|<span data-ttu-id="0ec1e-116">Pojem</span><span class="sxs-lookup"><span data-stu-id="0ec1e-116">Term</span></span>|<span data-ttu-id="0ec1e-117">Definice</span><span class="sxs-lookup"><span data-stu-id="0ec1e-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="0ec1e-118">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="0ec1e-118">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)|<span data-ttu-id="0ec1e-119">Popisuje `Const` příkaz, který slouží k deklaraci konstant.</span><span class="sxs-lookup"><span data-stu-id="0ec1e-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="0ec1e-120">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="0ec1e-120">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)|<span data-ttu-id="0ec1e-121">Popisuje `Enum` příkaz, který se používá k vytváření výčtů.</span><span class="sxs-lookup"><span data-stu-id="0ec1e-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="0ec1e-122">Option Explicit – příkaz</span><span class="sxs-lookup"><span data-stu-id="0ec1e-122">Option Explicit Statement</span></span>](../../../language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="0ec1e-123">Popisuje `Option Explicit` příkaz, který se používá na úrovni modulu k vynucení explicitní deklarace všech proměnných v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="0ec1e-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="0ec1e-124">Option Infer – příkaz</span><span class="sxs-lookup"><span data-stu-id="0ec1e-124">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)|<span data-ttu-id="0ec1e-125">Popisuje `Option Infer` příkaz, který umožňuje použití odvození místního typu v deklaraci proměnných.</span><span class="sxs-lookup"><span data-stu-id="0ec1e-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="0ec1e-126">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="0ec1e-126">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)|<span data-ttu-id="0ec1e-127">Popisuje `Option Strict` příkaz, který omezuje implicitní převody datových typů pouze na rozšiřování převodů, nepovoluje pozdní vazbu a nepovoluje implicitní zápis, který je výsledkem `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="0ec1e-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
