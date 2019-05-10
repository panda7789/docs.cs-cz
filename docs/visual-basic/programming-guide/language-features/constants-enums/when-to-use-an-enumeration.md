---
title: Kdy použít výčet (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: a43c55d4ad6a895957b53ae18c3641c5383a24ce
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64585077"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="87010-102">Kdy použít výčet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87010-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="87010-103">Výčty nabízí snadný způsob, jak pracovat se sadami související s konstantami.</span><span class="sxs-lookup"><span data-stu-id="87010-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="87010-104">Což je výčet nebo `Enum`, je symbolický název pro sadu hodnot.</span><span class="sxs-lookup"><span data-stu-id="87010-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="87010-105">Výčty jsou považovány za datových typů a můžete využít k vytvoření sady konstanty pro použití s proměnných a vlastností.</span><span class="sxs-lookup"><span data-stu-id="87010-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="87010-106">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="87010-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="87010-107">Pokaždé, když procedury přijímá omezenou sadu proměnných, zvažte možnost použít výčet.</span><span class="sxs-lookup"><span data-stu-id="87010-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="87010-108">Výčty usnadňují srozumitelnější a čitelnější kód, zejména v případě, že používají smysluplné názvy.</span><span class="sxs-lookup"><span data-stu-id="87010-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="87010-109">Výhody používání výčtů patří:</span><span class="sxs-lookup"><span data-stu-id="87010-109">The benefits of using enumerations include:</span></span>  
  
- <span data-ttu-id="87010-110">Snižuje chyby způsobené transpozice nebo chybným zadáním čísla.</span><span class="sxs-lookup"><span data-stu-id="87010-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
- <span data-ttu-id="87010-111">Umožňuje snadno ke změně hodnot v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="87010-111">Makes it easy to change values in the future.</span></span>  
  
- <span data-ttu-id="87010-112">Díky kód lépe čitelný, což znamená, že je méně pravděpodobné, že se do něj ovládat chyby.</span><span class="sxs-lookup"><span data-stu-id="87010-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
- <span data-ttu-id="87010-113">Zajišťuje kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="87010-113">Ensures forward compatibility.</span></span> <span data-ttu-id="87010-114">S výčty váš kód je méně pravděpodobné, že selhat, pokud v budoucnu někdo změní hodnoty odpovídající názvy členů.</span><span class="sxs-lookup"><span data-stu-id="87010-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="87010-115">Názvy výčtů</span><span class="sxs-lookup"><span data-stu-id="87010-115">Naming Enumerations</span></span>  
 <span data-ttu-id="87010-116">Použijte zásady vytváření názvů pro členy výčtu.</span><span class="sxs-lookup"><span data-stu-id="87010-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="87010-117">Pokud jazyka Visual Basic narazí název člena výčtu, může vyvolána výjimka, pokud obsahují další odkazované knihovny typů se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="87010-117">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="87010-118">Použijte jedinečnou předponu, která identifikuje hodnoty z vaší aplikace nebo komponenty.</span><span class="sxs-lookup"><span data-stu-id="87010-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="87010-119">Při odkazování na člena výčtu, které musí kvalifikovat název člena s názvem výčtu jinak použít `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="87010-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="87010-120">Další informace najdete v tématu [výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="87010-120">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="87010-121">Předdefinované výčty</span><span class="sxs-lookup"><span data-stu-id="87010-121">Predefined Enumerations</span></span>  
 <span data-ttu-id="87010-122">Visual Basic nabízí celou řadu předdefinovaných výčty, jako například `FirstDayOfWeek` a `MsgBoxResult`, které usnadní váš kód.</span><span class="sxs-lookup"><span data-stu-id="87010-122">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="87010-123">Jejich seznam naleznete v tématu [konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="87010-123">For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87010-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87010-124">See also</span></span>

- [<span data-ttu-id="87010-125">Postupy: Deklarace výčtů</span><span class="sxs-lookup"><span data-stu-id="87010-125">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="87010-126">Postupy: Odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="87010-126">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="87010-127">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="87010-127">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="87010-128">Postupy: Iterace ve výčtu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="87010-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="87010-129">Postupy: Určení řetězce spojeného s hodnotou výčtu</span><span class="sxs-lookup"><span data-stu-id="87010-129">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="87010-130">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="87010-130">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="87010-131">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="87010-131">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
