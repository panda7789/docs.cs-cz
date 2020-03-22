---
title: Vnořené řídicí struktury
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, control flow
- control structures [Visual Basic], nested
- conditional statements [Visual Basic], nested
- statements [Visual Basic], control flow
- control flow [Visual Basic], nested control statements
- structures [Visual Basic], nested control
- nested control statements [Visual Basic]
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
ms.openlocfilehash: b696c79cd3cada4416b3f4b6cdf96f00b89a5a0a
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266921"
---
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="56973-102">Vnořené řídicí struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56973-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="56973-103">Příkazy ovládacího prvku můžete umístit do `If...Then...Else` jiných `For...Next` příkazů ovládacího prvku, například bloku ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="56973-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="56973-104">Příkaz ovládacího prvku umístěný uvnitř jiného příkazu ovládacího prvku se nazývá *vnořené*.</span><span class="sxs-lookup"><span data-stu-id="56973-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="56973-105">Úrovně vnoření</span><span class="sxs-lookup"><span data-stu-id="56973-105">Nesting Levels</span></span>  
 <span data-ttu-id="56973-106">Struktury ovládacího prvku v jazyce Visual Basic lze vnořit do tolika úrovní, kolik chcete.</span><span class="sxs-lookup"><span data-stu-id="56973-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="56973-107">Je běžnou praxí, aby byly vnořené struktury čitelnější odsazením těla každého z nich.</span><span class="sxs-lookup"><span data-stu-id="56973-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="56973-108">Editor integrovaného vývojového prostředí (IDE) to automaticky provádí.</span><span class="sxs-lookup"><span data-stu-id="56973-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="56973-109">V následujícím příkladu `sumRows` postup sečte kladné prvky každého řádku matice.</span><span class="sxs-lookup"><span data-stu-id="56973-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
```vb
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
  
 <span data-ttu-id="56973-110">V předchozím příkladu první `Next` příkaz zavře `For` vnitřní smyčky `Next` a poslední příkaz `For` zavře vnější smyčky.</span><span class="sxs-lookup"><span data-stu-id="56973-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="56973-111">Podobně v vnořených `If` `End If` příkazech příkazy automaticky platí `If` pro nejbližší předchozí příkaz.</span><span class="sxs-lookup"><span data-stu-id="56973-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="56973-112">Vnořené `Do` smyčky pracovat podobným způsobem, `Loop` s nejvnitřnější `Do` příkaz odpovídající nejvnitřnější příkaz.</span><span class="sxs-lookup"><span data-stu-id="56973-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56973-113">U mnoha řídicích struktur jsou po klepnutí na klíčové slovo zvýrazněna všechna klíčová slova ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="56973-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="56973-114">`If` Pokud například klepnete `If...Then...Else` na stavbou, `If` `Then`zvýrazní se všechny instance aplikace , `ElseIf`, `Else`, a `End If` v konstrukci.</span><span class="sxs-lookup"><span data-stu-id="56973-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="56973-115">Pokud chcete přejít na další nebo předchozí zvýrazněné klíčové slovo, stiskněte kombinaci kláves CTRL+SHIFT+ŠIPKA DOLŮ nebo CTRL+SHIFT+ŠIPKA NAHORU.</span><span class="sxs-lookup"><span data-stu-id="56973-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="56973-116">Vnoření různých druhů řídicích struktur</span><span class="sxs-lookup"><span data-stu-id="56973-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="56973-117">Můžete vnořit jeden druh řídicí struktury do jiného druhu.</span><span class="sxs-lookup"><span data-stu-id="56973-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="56973-118">Následující příklad používá `With` blok `For Each` uvnitř smyčky `If` a vnořené bloky uvnitř `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="56973-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
```vb
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="56973-119">Překrývající se řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="56973-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="56973-120">Nelze překrývat řídicí struktury.</span><span class="sxs-lookup"><span data-stu-id="56973-120">You cannot overlap control structures.</span></span> <span data-ttu-id="56973-121">To znamená, že všechny vnořené struktury musí být zcela obsaženy v rámci další nejvnitřnější struktury.</span><span class="sxs-lookup"><span data-stu-id="56973-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="56973-122">Například následující uspořádání je neplatné, protože `For` smyčka `With` končí před ukončením vnitřního bloku.</span><span class="sxs-lookup"><span data-stu-id="56973-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 ![Diagram, který ukazuje příklad neplatného vnoření.](./media/nested-control-structures/example-invalid-nesting.gif)
  
 <span data-ttu-id="56973-124">Kompilátor jazyka rozpozná tyto překrývající se řídicí struktury a signalizuje chybu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="56973-124">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56973-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="56973-125">See also</span></span>

- [<span data-ttu-id="56973-126">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="56973-126">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="56973-127">Struktury rozhodování</span><span class="sxs-lookup"><span data-stu-id="56973-127">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="56973-128">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="56973-128">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="56973-129">Ostatní řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="56973-129">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
