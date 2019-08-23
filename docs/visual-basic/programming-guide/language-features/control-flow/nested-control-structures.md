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
# <a name="nested-control-structures-visual-basic"></a>Vnořené řídicí struktury (Visual Basic)
Řídicí příkazy lze umístit do jiných řídicích příkazů, například `If...Then...Else` bloku `For...Next` v rámci smyčky. Řídicí příkaz umístěný uvnitř jiného kontrolního příkazu je označován jako *vnořený*.  
  
## <a name="nesting-levels"></a>Vnořování úrovní  
 Řídicí struktury v Visual Basic můžou být vnořené do tolika úrovní, kolik chcete. Je běžné, že vnořené struktury budou čitelnější, když odsadíte tělo každé z nich. To dělá Editor integrovaného vývojového prostředí (IDE) automaticky.  
  
 V následujícím příkladu postup `sumRows` přidá do sebe kladné prvky každého řádku matice.  
  
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
  
 `Next` V předchozím příkladu první příkaz zavře vnitřní `For` smyčku a poslední `Next` příkaz zavře vnější `For` smyčku.  
  
 Stejně tak ve vnořených `If` příkazech `End If` se příkazy automaticky použijí na nejbližší předchozí `If` příkaz. Vnořené `Do` smyčky fungují podobným způsobem, přičemž vnitřní `Loop` příkaz odpovídá nejvnitřnějšímu `Do` příkazu.  
  
> [!NOTE]
> U mnoha řídicích struktur se při kliknutí na klíčové slovo zvýrazní všechna klíčová slova ve struktuře. `If` Například při kliknutí `If...Then...Else` na `Then` `ElseIf` `End If` konstrukci jsou zvýrazněny všechny`Else`instance,,, a v konstrukci. `If` Chcete-li přejít na další nebo předchozí zvýrazněné klíčové slovo, stiskněte klávesy CTRL + SHIFT + šipka dolů nebo CTRL + SHIFT + šipka nahoru.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Vnořování různých druhů řídicích struktur  
 Jeden druh struktury ovládacího prvku můžete vnořit do jiného typu. Následující příklad používá `With` blok `For Each` uvnitř `If` smyčky`With` a vnořené bloky uvnitř bloku.  
  
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
 Nemůžete překrývat řídicí struktury. To znamená, že všechny vnořené struktury musí být zcela obsaženy v další nejvnitřnější struktuře. Například následující uspořádání je neplatné, `For` protože smyčka končí před ukončením vnitřního `With` bloku.  
  
 ![Diagram, který zobrazuje příklad neplatného vnoření.](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 Kompilátor Visual Basic detekuje takové překrývající se řídicí struktury a signalizuje chybu při kompilaci.  
  
## <a name="see-also"></a>Viz také:

- [Tok řízení](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Rozhodovací struktury](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Struktury smyčky](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Ostatní řídicí struktury](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
