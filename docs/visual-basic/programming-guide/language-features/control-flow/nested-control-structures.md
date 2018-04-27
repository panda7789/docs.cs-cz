---
title: Vnořené řídicí struktury (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, control flow
- control structures [Visual Basic], nested
- conditional statements [Visual Basic], nested
- statements [Visual Basic], control flow
- control flow [Visual Basic], nested control statements
- structures [Visual Basic], nested control
- nested control statements [Visual Basic]
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f2c91bcdd741ef75417fe50b0c08bd0f9bd5ff80
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="39dd4-102">Vnořené řídicí struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39dd4-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="39dd4-103">Můžete umístit řídicí příkazy uvnitř jiné řídicí příkazy, například `If...Then...Else` blokovat v rámci `For...Next` smyčky.</span><span class="sxs-lookup"><span data-stu-id="39dd4-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="39dd4-104">Příkaz Ovládací prvek umístěn uvnitř jiného příkazu ovládací prvek se říká, že *vnořené*.</span><span class="sxs-lookup"><span data-stu-id="39dd4-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="39dd4-105">Úrovně vnoření</span><span class="sxs-lookup"><span data-stu-id="39dd4-105">Nesting Levels</span></span>  
 <span data-ttu-id="39dd4-106">Na libovolný počet úrovní můžete vnořené řídicí struktury v jazyku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="39dd4-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="39dd4-107">Je obvyklé, aby byl čitelnější vnořené struktury odsazením text každé z nich.</span><span class="sxs-lookup"><span data-stu-id="39dd4-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="39dd4-108">Integrované vývojové prostředí (IDE) editoru automaticky tomu.</span><span class="sxs-lookup"><span data-stu-id="39dd4-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="39dd4-109">V následujícím příkladu, postup `sumRows` přidá společně kladné elementy každý řádek matice.</span><span class="sxs-lookup"><span data-stu-id="39dd4-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
```  
Public Sub sumRows(ByVal a(,) As Double, ByRef r() As Double)  
    Dim i, j As Integer  
    For i = 0 To UBound(a, 1)  
        r(i) = 0  
        For j = 0 To UBound(a, 2)  
            If a(i, j) > 0 Then  
                r(i) = r(i) + a(i, j)  
            End If  
        Next j  
    Next i  
End Sub  
```  
  
 <span data-ttu-id="39dd4-110">V předchozím příkladu první `Next` příkaz zavře vnitřní `For` smyčky a poslední `Next` příkaz zavře vnější `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="39dd4-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="39dd4-111">Podobně ve vnořených `If` příkazy, `End If` příkazy automaticky použít pro nejbližší před `If` příkaz.</span><span class="sxs-lookup"><span data-stu-id="39dd4-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="39dd4-112">Vnořené `Do` smyčky fungovat podobným způsobem, s nejvnitřnější `Loop` příkaz odpovídající nejvnitřnější `Do` příkaz.</span><span class="sxs-lookup"><span data-stu-id="39dd4-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39dd4-113">Pro mnoho řídicí struktury po kliknutí na tlačítko klíčové slovo, všechny klíčová slova ve struktuře jsou vyznačené.</span><span class="sxs-lookup"><span data-stu-id="39dd4-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="39dd4-114">Například když kliknete na tlačítko `If` v `If...Then...Else` konstrukce, všechny instance `If`, `Then`, `ElseIf`, `Else`, a `End If` jsou vyznačené při sestavování.</span><span class="sxs-lookup"><span data-stu-id="39dd4-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="39dd4-115">Chcete-li přesunout další nebo předchozí zvýrazněný – klíčové slovo, stiskněte CTRL + SHIFT + šipka dolů nebo CTRL + SHIFT + šipka nahoru.</span><span class="sxs-lookup"><span data-stu-id="39dd4-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="39dd4-116">Vnoření různé druhy řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="39dd4-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="39dd4-117">Lze vnořit jednoho druhu řízení struktury v rámci jiného typu.</span><span class="sxs-lookup"><span data-stu-id="39dd4-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="39dd4-118">Následující příklad používá `With` blokovat uvnitř `For Each` smyčky a vnořené `If` blokuje uvnitř `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="39dd4-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
```  
For Each ctl As System.Windows.Forms.Control In Me.Controls  
    With ctl  
        .BackColor = System.Drawing.Color.Yellow  
        .ForeColor = System.Drawing.Color.Black  
        If .CanFocus Then  
            .Text = "Colors changed"  
            If Not .Focus() Then  
                ' Insert code to process failed focus.  
            End If  
        End If  
    End With  
Next ctl  
```  
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="39dd4-119">Překrývající se řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="39dd4-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="39dd4-120">Řídicí struktury nesmí překrývat.</span><span class="sxs-lookup"><span data-stu-id="39dd4-120">You cannot overlap control structures.</span></span> <span data-ttu-id="39dd4-121">To znamená, že všechny vnořené struktury musí být zcela obsažen v další nejvnitřnější strukturu.</span><span class="sxs-lookup"><span data-stu-id="39dd4-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="39dd4-122">Například následující uspořádání je neplatný protože `For` smyčky ukončí před vnitřní `With` ukončí bloku.</span><span class="sxs-lookup"><span data-stu-id="39dd4-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 <span data-ttu-id="39dd4-123">![Grafický diagram neplatný vnoření](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span><span class="sxs-lookup"><span data-stu-id="39dd4-123">![Graphic diagram of invalid nesting](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span></span>  
<span data-ttu-id="39dd4-124">Neplatný vnořené pro a struktury</span><span class="sxs-lookup"><span data-stu-id="39dd4-124">Invalid nesting of For and With structures</span></span>  
  
 <span data-ttu-id="39dd4-125">Visual Basic – kompilátor zjistí takové překrývající se řídicí struktury a signály chyby kompilace.</span><span class="sxs-lookup"><span data-stu-id="39dd4-125">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39dd4-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="39dd4-126">See Also</span></span>  
 [<span data-ttu-id="39dd4-127">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="39dd4-127">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="39dd4-128">Rozhodovací struktury</span><span class="sxs-lookup"><span data-stu-id="39dd4-128">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="39dd4-129">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="39dd4-129">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="39dd4-130">Ostatní řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="39dd4-130">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
