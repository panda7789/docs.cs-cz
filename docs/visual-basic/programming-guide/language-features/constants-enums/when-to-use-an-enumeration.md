---
title: Kdy použít výčet (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ab152687f4f9e4ba6bd032ae7c1352f65af715f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="d9927-102">Kdy použít výčet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9927-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="d9927-103">Výčty nabízí snadný způsob, jak pracovat s sady souvisejících konstanty.</span><span class="sxs-lookup"><span data-stu-id="d9927-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="d9927-104">Na výčtu nebo `Enum`, je symbolický název pro sadu hodnot.</span><span class="sxs-lookup"><span data-stu-id="d9927-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="d9927-105">Výčty jsou považovány za datové typy a můžete je použít k vytvoření sad konstanty pro použití s proměnnými a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d9927-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="d9927-106">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="d9927-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="d9927-107">Vždy, když procedury přijímá omezenou sadu proměnných, zvažte použití výčet.</span><span class="sxs-lookup"><span data-stu-id="d9927-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="d9927-108">Výčty zajistěte pro jasnější a srozumitelnější kód, zvláště pokud smysluplný názvy jsou použity.</span><span class="sxs-lookup"><span data-stu-id="d9927-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="d9927-109">Mezi výhody používání výčty patří:</span><span class="sxs-lookup"><span data-stu-id="d9927-109">The benefits of using enumerations include:</span></span>  
  
-   <span data-ttu-id="d9927-110">Snižuje chyby způsobené transpozice nebo chybným zadáním čísla.</span><span class="sxs-lookup"><span data-stu-id="d9927-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="d9927-111">Lze snadno ke změně hodnot v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="d9927-111">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="d9927-112">Díky kód snadněji číst, což znamená, že je méně pravděpodobné, že se do ní ovládat chyby.</span><span class="sxs-lookup"><span data-stu-id="d9927-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
-   <span data-ttu-id="d9927-113">Zajišťuje kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="d9927-113">Ensures forward compatibility.</span></span> <span data-ttu-id="d9927-114">Váš kód s výčty, je méně pravděpodobné, že nezdaří, pokud v budoucnu někdo změní hodnoty odpovídající názvy členů.</span><span class="sxs-lookup"><span data-stu-id="d9927-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="d9927-115">Pojmenování výčty</span><span class="sxs-lookup"><span data-stu-id="d9927-115">Naming Enumerations</span></span>  
 <span data-ttu-id="d9927-116">Použijte zásady vytváření názvů pro členy výčtu.</span><span class="sxs-lookup"><span data-stu-id="d9927-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="d9927-117">Když Visual Basic dojde název člena výčtu, může být vyvolána výjimka, pokud obsahovat další odkazovaného typu knihovny se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="d9927-117">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="d9927-118">Použijte jedinečnou předponu, která identifikuje hodnoty z vaší aplikace nebo součásti.</span><span class="sxs-lookup"><span data-stu-id="d9927-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="d9927-119">K odkazování na člena výčtu, je nutné kvalifikaci název člena s názvem výčtu jinak použít `Imports` příkaz.</span><span class="sxs-lookup"><span data-stu-id="d9927-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="d9927-120">Další informace najdete v tématu [výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="d9927-120">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="d9927-121">Předdefinované výčty</span><span class="sxs-lookup"><span data-stu-id="d9927-121">Predefined Enumerations</span></span>  
 <span data-ttu-id="d9927-122">Visual Basic poskytuje řadu předdefinovaných výčty, jako například `FirstDayOfWeek` a `MsgBoxResult`, aby se usnadnilo kódu.</span><span class="sxs-lookup"><span data-stu-id="d9927-122">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="d9927-123">Seznam naleznete v části [konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="d9927-123">For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9927-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9927-124">See Also</span></span>  
 [<span data-ttu-id="d9927-125">Postupy: deklarace výčtů</span><span class="sxs-lookup"><span data-stu-id="d9927-125">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="d9927-126">Postupy: Odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="d9927-126">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="d9927-127">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="d9927-127">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="d9927-128">Postupy: iterace výčet v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d9927-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="d9927-129">Postupy: Určení řetězce spojeného s hodnotou výčtu</span><span class="sxs-lookup"><span data-stu-id="d9927-129">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="d9927-130">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="d9927-130">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="d9927-131">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="d9927-131">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
