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
# <a name="nested-control-structures-visual-basic"></a>Vnořené řídicí struktury (Visual Basic)
Příkazy ovládacího prvku můžete umístit do `If...Then...Else` jiných `For...Next` příkazů ovládacího prvku, například bloku ve smyčce. Příkaz ovládacího prvku umístěný uvnitř jiného příkazu ovládacího prvku se nazývá *vnořené*.  
  
## <a name="nesting-levels"></a>Úrovně vnoření  
 Struktury ovládacího prvku v jazyce Visual Basic lze vnořit do tolika úrovní, kolik chcete. Je běžnou praxí, aby byly vnořené struktury čitelnější odsazením těla každého z nich. Editor integrovaného vývojového prostředí (IDE) to automaticky provádí.  
  
 V následujícím příkladu `sumRows` postup sečte kladné prvky každého řádku matice.  
  
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
  
 V předchozím příkladu první `Next` příkaz zavře `For` vnitřní smyčky `Next` a poslední příkaz `For` zavře vnější smyčky.  
  
 Podobně v vnořených `If` `End If` příkazech příkazy automaticky platí `If` pro nejbližší předchozí příkaz. Vnořené `Do` smyčky pracovat podobným způsobem, `Loop` s nejvnitřnější `Do` příkaz odpovídající nejvnitřnější příkaz.  
  
> [!NOTE]
> U mnoha řídicích struktur jsou po klepnutí na klíčové slovo zvýrazněna všechna klíčová slova ve struktuře. `If` Pokud například klepnete `If...Then...Else` na stavbou, `If` `Then`zvýrazní se všechny instance aplikace , `ElseIf`, `Else`, a `End If` v konstrukci. Pokud chcete přejít na další nebo předchozí zvýrazněné klíčové slovo, stiskněte kombinaci kláves CTRL+SHIFT+ŠIPKA DOLŮ nebo CTRL+SHIFT+ŠIPKA NAHORU.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Vnoření různých druhů řídicích struktur  
 Můžete vnořit jeden druh řídicí struktury do jiného druhu. Následující příklad používá `With` blok `For Each` uvnitř smyčky `If` a vnořené bloky uvnitř `With` bloku.  
  
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
  
## <a name="overlapping-control-structures"></a>Překrývající se řídicí struktury  
 Nelze překrývat řídicí struktury. To znamená, že všechny vnořené struktury musí být zcela obsaženy v rámci další nejvnitřnější struktury. Například následující uspořádání je neplatné, protože `For` smyčka `With` končí před ukončením vnitřního bloku.  
  
 ![Diagram, který ukazuje příklad neplatného vnoření.](./media/nested-control-structures/example-invalid-nesting.gif)
  
 Kompilátor jazyka rozpozná tyto překrývající se řídicí struktury a signalizuje chybu v době kompilace.  
  
## <a name="see-also"></a>Viz také

- [Tok řízení](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Struktury rozhodování](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Struktury smyčky](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Ostatní řídicí struktury](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
