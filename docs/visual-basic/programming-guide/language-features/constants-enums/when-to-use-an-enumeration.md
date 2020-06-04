---
title: Kdy použít výčet
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: ba69249e16b8c0ee06d57d06d192874a283b295e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403534"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="f185d-102">Kdy použít výčet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f185d-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="f185d-103">Výčty představují snadný způsob, jak pracovat se sadami souvisejících konstant.</span><span class="sxs-lookup"><span data-stu-id="f185d-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="f185d-104">Výčet nebo `Enum` je symbolický název pro sadu hodnot.</span><span class="sxs-lookup"><span data-stu-id="f185d-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="f185d-105">Výčty jsou považovány za datové typy a lze je použít k vytvoření sady konstant pro použití s proměnnými a vlastnostmi.</span><span class="sxs-lookup"><span data-stu-id="f185d-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="f185d-106">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="f185d-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="f185d-107">Pokaždé, když procedura přijme omezené sady proměnných, zvažte použití výčtu.</span><span class="sxs-lookup"><span data-stu-id="f185d-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="f185d-108">Výčty vycházejí z jasných a čitelnějších kódů, zejména v případě, že se používají smysluplné názvy.</span><span class="sxs-lookup"><span data-stu-id="f185d-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="f185d-109">Mezi výhody používání výčtů patří:</span><span class="sxs-lookup"><span data-stu-id="f185d-109">The benefits of using enumerations include:</span></span>  
  
- <span data-ttu-id="f185d-110">Snižuje chyby způsobené přetypováním nebo nesprávným zadáním čísel.</span><span class="sxs-lookup"><span data-stu-id="f185d-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
- <span data-ttu-id="f185d-111">V budoucnu usnadňuje změnu hodnot.</span><span class="sxs-lookup"><span data-stu-id="f185d-111">Makes it easy to change values in the future.</span></span>  
  
- <span data-ttu-id="f185d-112">Usnadňuje čtení kódu, což znamená, že je méně pravděpodobný, že se na něj chyby ponárůstí.</span><span class="sxs-lookup"><span data-stu-id="f185d-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
- <span data-ttu-id="f185d-113">Zajišťuje dopředné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="f185d-113">Ensures forward compatibility.</span></span> <span data-ttu-id="f185d-114">V případě výčtů je váš kód méně pravděpodobný, pokud v budoucnu někdo změní hodnoty odpovídající názvům členů.</span><span class="sxs-lookup"><span data-stu-id="f185d-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="f185d-115">Vytváření názvů výčtů</span><span class="sxs-lookup"><span data-stu-id="f185d-115">Naming Enumerations</span></span>  
 <span data-ttu-id="f185d-116">Použijte zásady vytváření názvů pro členy výčtu.</span><span class="sxs-lookup"><span data-stu-id="f185d-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="f185d-117">Když Visual Basic narazí na název člena výčtu, může být vyvolána výjimka, pokud jiné odkazované knihovny typů obsahují stejný název.</span><span class="sxs-lookup"><span data-stu-id="f185d-117">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="f185d-118">Použijte jedinečnou předponu, která identifikuje hodnoty z vaší aplikace nebo komponenty.</span><span class="sxs-lookup"><span data-stu-id="f185d-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="f185d-119">Při odkazování na člena výčtu je nutné kvalifikovat název člena s názvem výčtu nebo jinak použít `Imports` příkaz.</span><span class="sxs-lookup"><span data-stu-id="f185d-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="f185d-120">Další informace naleznete v tématu [výčty a kvalifikace názvu](enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="f185d-120">For more information, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="f185d-121">Předdefinované výčty</span><span class="sxs-lookup"><span data-stu-id="f185d-121">Predefined Enumerations</span></span>  
 <span data-ttu-id="f185d-122">Visual Basic poskytuje řadu předdefinovaných výčtů, jako jsou `FirstDayOfWeek` a `MsgBoxResult` , pro usnadnění kódu.</span><span class="sxs-lookup"><span data-stu-id="f185d-122">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="f185d-123">Seznam těchto naleznete v tématu [konstanty a výčty](../../../language-reference/constants-and-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="f185d-123">For a list of these see [Constants and Enumerations](../../../language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f185d-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="f185d-124">See also</span></span>

- [<span data-ttu-id="f185d-125">Postupy: deklarace výčtu</span><span class="sxs-lookup"><span data-stu-id="f185d-125">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="f185d-126">Postupy: Odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="f185d-126">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="f185d-127">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="f185d-127">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="f185d-128">Postupy: Iterace ve výčtu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f185d-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="f185d-129">Postupy: Určení řetězce spojeného s hodnotou výčtu</span><span class="sxs-lookup"><span data-stu-id="f185d-129">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="f185d-130">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="f185d-130">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="f185d-131">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="f185d-131">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
