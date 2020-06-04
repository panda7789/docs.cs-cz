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
# <a name="nested-control-structures-visual-basic"></a>Vnořené řídicí struktury (Visual Basic)
Řídicí příkazy lze umístit do jiných řídicích příkazů, například `If...Then...Else` bloku v rámci `For...Next` smyčky. Řídicí příkaz umístěný uvnitř jiného kontrolního příkazu je označován jako *vnořený*.  
  
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
  
 V předchozím příkladu první `Next` příkaz zavře vnitřní `For` smyčku a poslední `Next` příkaz zavře vnější `For` smyčku.  
  
 Stejně tak ve vnořených `If` příkazech se `End If` příkazy automaticky použijí na nejbližší předchozí `If` příkaz. Vnořené `Do` smyčky fungují podobným způsobem, přičemž vnitřní `Loop` příkaz odpovídá nejvnitřnějšímu `Do` příkazu.  
  
> [!NOTE]
> U mnoha řídicích struktur se při kliknutí na klíčové slovo zvýrazní všechna klíčová slova ve struktuře. Například při kliknutí na `If` `If...Then...Else` konstrukci `If` `Then` jsou zvýrazněny všechny instance,,, `ElseIf` `Else` a `End If` v konstrukci. Chcete-li přejít na další nebo předchozí zvýrazněné klíčové slovo, stiskněte klávesy CTRL + SHIFT + šipka dolů nebo CTRL + SHIFT + šipka nahoru.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Vnořování různých druhů řídicích struktur  
 Jeden druh struktury ovládacího prvku můžete vnořit do jiného typu. Následující příklad používá `With` blok uvnitř `For Each` smyčky a vnořené `If` bloky uvnitř `With` bloku.  
  
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
 Nemůžete překrývat řídicí struktury. To znamená, že všechny vnořené struktury musí být zcela obsaženy v další nejvnitřnější struktuře. Například následující uspořádání je neplatné, protože `For` smyčka končí před `With` ukončením vnitřního bloku.  
  
 ![Diagram, který zobrazuje příklad neplatného vnoření.](./media/nested-control-structures/example-invalid-nesting.gif)
  
 Kompilátor Visual Basic detekuje takové překrývající se řídicí struktury a signalizuje chybu při kompilaci.  
  
## <a name="see-also"></a>Viz také

- [Tok řízení](index.md)
- [Struktury rozhodování](decision-structures.md)
- [Struktury smyčky](loop-structures.md)
- [Ostatní řídicí struktury](other-control-structures.md)
