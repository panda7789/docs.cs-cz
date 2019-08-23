---
title: Vnořené řídicí struktury (Visual Basic)
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
ms.openlocfilehash: f559bf603605873f1b9155e9a96cb367e5420343
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941677"
---
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="fea9a-102">Vnořené řídicí struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fea9a-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="fea9a-103">Řídicí příkazy lze umístit do jiných řídicích příkazů, například `If...Then...Else` bloku `For...Next` v rámci smyčky.</span><span class="sxs-lookup"><span data-stu-id="fea9a-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="fea9a-104">Řídicí příkaz umístěný uvnitř jiného kontrolního příkazu je označován jako *vnořený*.</span><span class="sxs-lookup"><span data-stu-id="fea9a-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="fea9a-105">Vnořování úrovní</span><span class="sxs-lookup"><span data-stu-id="fea9a-105">Nesting Levels</span></span>  
 <span data-ttu-id="fea9a-106">Řídicí struktury v Visual Basic můžou být vnořené do tolika úrovní, kolik chcete.</span><span class="sxs-lookup"><span data-stu-id="fea9a-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="fea9a-107">Je běžné, že vnořené struktury budou čitelnější, když odsadíte tělo každé z nich.</span><span class="sxs-lookup"><span data-stu-id="fea9a-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="fea9a-108">To dělá Editor integrovaného vývojového prostředí (IDE) automaticky.</span><span class="sxs-lookup"><span data-stu-id="fea9a-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="fea9a-109">V následujícím příkladu postup `sumRows` přidá do sebe kladné prvky každého řádku matice.</span><span class="sxs-lookup"><span data-stu-id="fea9a-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="fea9a-110">`Next` V předchozím příkladu první příkaz zavře vnitřní `For` smyčku a poslední `Next` příkaz zavře vnější `For` smyčku.</span><span class="sxs-lookup"><span data-stu-id="fea9a-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="fea9a-111">Stejně tak ve vnořených `If` příkazech `End If` se příkazy automaticky použijí na nejbližší předchozí `If` příkaz.</span><span class="sxs-lookup"><span data-stu-id="fea9a-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="fea9a-112">Vnořené `Do` smyčky fungují podobným způsobem, přičemž vnitřní `Loop` příkaz odpovídá nejvnitřnějšímu `Do` příkazu.</span><span class="sxs-lookup"><span data-stu-id="fea9a-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fea9a-113">U mnoha řídicích struktur se při kliknutí na klíčové slovo zvýrazní všechna klíčová slova ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="fea9a-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="fea9a-114">`If` Například při kliknutí `If...Then...Else` na `Then` `ElseIf` `End If` konstrukci jsou zvýrazněny všechny`Else`instance,,, a v konstrukci. `If`</span><span class="sxs-lookup"><span data-stu-id="fea9a-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="fea9a-115">Chcete-li přejít na další nebo předchozí zvýrazněné klíčové slovo, stiskněte klávesy CTRL + SHIFT + šipka dolů nebo CTRL + SHIFT + šipka nahoru.</span><span class="sxs-lookup"><span data-stu-id="fea9a-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="fea9a-116">Vnořování různých druhů řídicích struktur</span><span class="sxs-lookup"><span data-stu-id="fea9a-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="fea9a-117">Jeden druh struktury ovládacího prvku můžete vnořit do jiného typu.</span><span class="sxs-lookup"><span data-stu-id="fea9a-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="fea9a-118">Následující příklad používá `With` blok `For Each` uvnitř `If` smyčky`With` a vnořené bloky uvnitř bloku.</span><span class="sxs-lookup"><span data-stu-id="fea9a-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="fea9a-119">Překrývající se řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="fea9a-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="fea9a-120">Nemůžete překrývat řídicí struktury.</span><span class="sxs-lookup"><span data-stu-id="fea9a-120">You cannot overlap control structures.</span></span> <span data-ttu-id="fea9a-121">To znamená, že všechny vnořené struktury musí být zcela obsaženy v další nejvnitřnější struktuře.</span><span class="sxs-lookup"><span data-stu-id="fea9a-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="fea9a-122">Například následující uspořádání je neplatné, `For` protože smyčka končí před ukončením vnitřního `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="fea9a-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 ![Diagram, který zobrazuje příklad neplatného vnoření.](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 <span data-ttu-id="fea9a-124">Kompilátor Visual Basic detekuje takové překrývající se řídicí struktury a signalizuje chybu při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="fea9a-124">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fea9a-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fea9a-125">See also</span></span>

- [<span data-ttu-id="fea9a-126">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="fea9a-126">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="fea9a-127">Rozhodovací struktury</span><span class="sxs-lookup"><span data-stu-id="fea9a-127">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="fea9a-128">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="fea9a-128">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="fea9a-129">Ostatní řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="fea9a-129">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
