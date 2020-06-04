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
ms.openlocfilehash: 539ad639320615c1e53176fe47e5468864aa21d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414386"
---
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="45d3b-102">Vnořené řídicí struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45d3b-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="45d3b-103">Řídicí příkazy lze umístit do jiných řídicích příkazů, například `If...Then...Else` bloku v rámci `For...Next` smyčky.</span><span class="sxs-lookup"><span data-stu-id="45d3b-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="45d3b-104">Řídicí příkaz umístěný uvnitř jiného kontrolního příkazu je označován jako *vnořený*.</span><span class="sxs-lookup"><span data-stu-id="45d3b-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="45d3b-105">Vnořování úrovní</span><span class="sxs-lookup"><span data-stu-id="45d3b-105">Nesting Levels</span></span>  
 <span data-ttu-id="45d3b-106">Řídicí struktury v Visual Basic můžou být vnořené do tolika úrovní, kolik chcete.</span><span class="sxs-lookup"><span data-stu-id="45d3b-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="45d3b-107">Je běžné, že vnořené struktury budou čitelnější, když odsadíte tělo každé z nich.</span><span class="sxs-lookup"><span data-stu-id="45d3b-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="45d3b-108">To dělá Editor integrovaného vývojového prostředí (IDE) automaticky.</span><span class="sxs-lookup"><span data-stu-id="45d3b-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="45d3b-109">V následujícím příkladu postup `sumRows` přidá do sebe kladné prvky každého řádku matice.</span><span class="sxs-lookup"><span data-stu-id="45d3b-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="45d3b-110">V předchozím příkladu první `Next` příkaz zavře vnitřní `For` smyčku a poslední `Next` příkaz zavře vnější `For` smyčku.</span><span class="sxs-lookup"><span data-stu-id="45d3b-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="45d3b-111">Stejně tak ve vnořených `If` příkazech se `End If` příkazy automaticky použijí na nejbližší předchozí `If` příkaz.</span><span class="sxs-lookup"><span data-stu-id="45d3b-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="45d3b-112">Vnořené `Do` smyčky fungují podobným způsobem, přičemž vnitřní `Loop` příkaz odpovídá nejvnitřnějšímu `Do` příkazu.</span><span class="sxs-lookup"><span data-stu-id="45d3b-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45d3b-113">U mnoha řídicích struktur se při kliknutí na klíčové slovo zvýrazní všechna klíčová slova ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="45d3b-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="45d3b-114">Například při kliknutí na `If` `If...Then...Else` konstrukci `If` `Then` jsou zvýrazněny všechny instance,,, `ElseIf` `Else` a `End If` v konstrukci.</span><span class="sxs-lookup"><span data-stu-id="45d3b-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="45d3b-115">Chcete-li přejít na další nebo předchozí zvýrazněné klíčové slovo, stiskněte klávesy CTRL + SHIFT + šipka dolů nebo CTRL + SHIFT + šipka nahoru.</span><span class="sxs-lookup"><span data-stu-id="45d3b-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="45d3b-116">Vnořování různých druhů řídicích struktur</span><span class="sxs-lookup"><span data-stu-id="45d3b-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="45d3b-117">Jeden druh struktury ovládacího prvku můžete vnořit do jiného typu.</span><span class="sxs-lookup"><span data-stu-id="45d3b-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="45d3b-118">Následující příklad používá `With` blok uvnitř `For Each` smyčky a vnořené `If` bloky uvnitř `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="45d3b-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="45d3b-119">Překrývající se řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="45d3b-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="45d3b-120">Nemůžete překrývat řídicí struktury.</span><span class="sxs-lookup"><span data-stu-id="45d3b-120">You cannot overlap control structures.</span></span> <span data-ttu-id="45d3b-121">To znamená, že všechny vnořené struktury musí být zcela obsaženy v další nejvnitřnější struktuře.</span><span class="sxs-lookup"><span data-stu-id="45d3b-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="45d3b-122">Například následující uspořádání je neplatné, protože `For` smyčka končí před `With` ukončením vnitřního bloku.</span><span class="sxs-lookup"><span data-stu-id="45d3b-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 ![Diagram, který zobrazuje příklad neplatného vnoření.](./media/nested-control-structures/example-invalid-nesting.gif)
  
 <span data-ttu-id="45d3b-124">Kompilátor Visual Basic detekuje takové překrývající se řídicí struktury a signalizuje chybu při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="45d3b-124">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45d3b-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="45d3b-125">See also</span></span>

- [<span data-ttu-id="45d3b-126">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="45d3b-126">Control Flow</span></span>](index.md)
- [<span data-ttu-id="45d3b-127">Struktury rozhodování</span><span class="sxs-lookup"><span data-stu-id="45d3b-127">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="45d3b-128">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="45d3b-128">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="45d3b-129">Ostatní řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="45d3b-129">Other Control Structures</span></span>](other-control-structures.md)
