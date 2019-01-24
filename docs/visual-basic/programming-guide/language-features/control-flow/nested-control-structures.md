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
ms.openlocfilehash: fec1b4dbca0a4c6979e52fc74ceeb3e8c7ac6cad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520461"
---
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="3818d-102">Vnořené řídicí struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3818d-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="3818d-103">Můžete například umístit řídicí příkazy uvnitř jiné řídicí příkazy `If...Then...Else` blokovat v rámci `For...Next` smyčky.</span><span class="sxs-lookup"><span data-stu-id="3818d-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="3818d-104">Ovládací prvek příkaz umístit do jiného příkazu ovládacího prvku se říká, že *vnořené*.</span><span class="sxs-lookup"><span data-stu-id="3818d-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="3818d-105">Vnořování úrovní</span><span class="sxs-lookup"><span data-stu-id="3818d-105">Nesting Levels</span></span>  
 <span data-ttu-id="3818d-106">Pro libovolný počet úrovní, mohou být vnořené řídicí struktury v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3818d-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="3818d-107">Je obvyklé, aby byl čitelnější vnořené struktury odsazením tělo každé z nich.</span><span class="sxs-lookup"><span data-stu-id="3818d-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="3818d-108">Editor integrované vývojové prostředí (IDE) to provede automaticky.</span><span class="sxs-lookup"><span data-stu-id="3818d-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="3818d-109">V následujícím příkladu, postup `sumRows` sečte pozitivní prvky každý řádek v matici.</span><span class="sxs-lookup"><span data-stu-id="3818d-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="3818d-110">V předchozím příkladu první `Next` příkaz zavře vnitřní `For` smyčky a poslední `Next` příkaz zavře vnější `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="3818d-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="3818d-111">Podobně ve vnořené `If` příkazy, `End If` příkazy automaticky použít k nejbližší předchozí `If` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3818d-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="3818d-112">Vnořené `Do` smyčky fungovat podobným způsobem, s nejvnitřnější `Loop` příkaz odpovídající nejvnitřnější `Do` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3818d-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3818d-113">Pro mnoho řídících struktur po kliknutí na klíčové slovo, všechna klíčová slova ve struktuře jsou zvýrazněné.</span><span class="sxs-lookup"><span data-stu-id="3818d-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="3818d-114">Například po kliknutí na `If` v `If...Then...Else` konstrukce, všechny výskyty `If`, `Then`, `ElseIf`, `Else`, a `End If` jsou zvýrazněné v procesu vytváření.</span><span class="sxs-lookup"><span data-stu-id="3818d-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="3818d-115">Přesunout další nebo předchozí zvýrazněný – klíčové slovo, stiskněte kombinaci kláves CTRL + SHIFT + šipka dolů nebo CTRL + SHIFT + šipka nahoru.</span><span class="sxs-lookup"><span data-stu-id="3818d-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="3818d-116">Vnoření různé druhy řídicích struktur</span><span class="sxs-lookup"><span data-stu-id="3818d-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="3818d-117">Je možné vnořovat jednoho druhu struktury ovládací prvek v rámci jiného druhu.</span><span class="sxs-lookup"><span data-stu-id="3818d-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="3818d-118">Následující příklad používá `With` uvnitř bloku `For Each` smyčky a vnořené `If` blokuje uvnitř `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="3818d-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="3818d-119">Překrývající se řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="3818d-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="3818d-120">Řídicí struktury nemůžou překrývat.</span><span class="sxs-lookup"><span data-stu-id="3818d-120">You cannot overlap control structures.</span></span> <span data-ttu-id="3818d-121">To znamená, že všechny vnořené struktury musí být zcela obsažen v rámci další vnitřní struktury.</span><span class="sxs-lookup"><span data-stu-id="3818d-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="3818d-122">Například následující uspořádání je neplatný protože `For` smyčku ukončí před vnitřní `With` blok ukončí.</span><span class="sxs-lookup"><span data-stu-id="3818d-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 <span data-ttu-id="3818d-123">![Grafický diagram neplatné vnoření](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span><span class="sxs-lookup"><span data-stu-id="3818d-123">![Graphic diagram of invalid nesting](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span></span>  
<span data-ttu-id="3818d-124">Neplatné vnoření pro a struktury</span><span class="sxs-lookup"><span data-stu-id="3818d-124">Invalid nesting of For and With structures</span></span>  
  
 <span data-ttu-id="3818d-125">Kompilátor jazyka Visual Basic zjistí překrývající se ovládací prvek struktur a signály chybu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="3818d-125">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3818d-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3818d-126">See also</span></span>
- [<span data-ttu-id="3818d-127">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="3818d-127">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="3818d-128">Rozhodovací struktury</span><span class="sxs-lookup"><span data-stu-id="3818d-128">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="3818d-129">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="3818d-129">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="3818d-130">Ostatní řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="3818d-130">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
