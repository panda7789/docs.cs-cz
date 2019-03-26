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
ms.openlocfilehash: 13e2c5c8d818a09ec5e77ec47fe8a2c83b675d82
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409793"
---
# <a name="nested-control-structures-visual-basic"></a>Vnořené řídicí struktury (Visual Basic)
Můžete například umístit řídicí příkazy uvnitř jiné řídicí příkazy `If...Then...Else` blokovat v rámci `For...Next` smyčky. Ovládací prvek příkaz umístit do jiného příkazu ovládacího prvku se říká, že *vnořené*.  
  
## <a name="nesting-levels"></a>Vnořování úrovní  
 Pro libovolný počet úrovní, mohou být vnořené řídicí struktury v jazyce Visual Basic. Je obvyklé, aby byl čitelnější vnořené struktury odsazením tělo každé z nich. Editor integrované vývojové prostředí (IDE) to provede automaticky.  
  
 V následujícím příkladu, postup `sumRows` sečte pozitivní prvky každý řádek v matici.  
  
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
  
 V předchozím příkladu první `Next` příkaz zavře vnitřní `For` smyčky a poslední `Next` příkaz zavře vnější `For` smyčky.  
  
 Podobně ve vnořené `If` příkazy, `End If` příkazy automaticky použít k nejbližší předchozí `If` příkazu. Vnořené `Do` smyčky fungovat podobným způsobem, s nejvnitřnější `Loop` příkaz odpovídající nejvnitřnější `Do` příkazu.  
  
> [!NOTE]
>  Pro mnoho řídících struktur po kliknutí na klíčové slovo, všechna klíčová slova ve struktuře jsou zvýrazněné. Například po kliknutí na `If` v `If...Then...Else` konstrukce, všechny výskyty `If`, `Then`, `ElseIf`, `Else`, a `End If` jsou zvýrazněné v procesu vytváření. Přesunout další nebo předchozí zvýrazněný – klíčové slovo, stiskněte kombinaci kláves CTRL + SHIFT + šipka dolů nebo CTRL + SHIFT + šipka nahoru.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Vnoření různé druhy řídicích struktur  
 Je možné vnořovat jednoho druhu struktury ovládací prvek v rámci jiného druhu. Následující příklad používá `With` uvnitř bloku `For Each` smyčky a vnořené `If` blokuje uvnitř `With` bloku.  
  
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
 Řídicí struktury nemůžou překrývat. To znamená, že všechny vnořené struktury musí být zcela obsažen v rámci další vnitřní struktury. Například následující uspořádání je neplatný protože `For` smyčku ukončí před vnitřní `With` blok ukončí.  
  
 ![Diagram zobrazující příklad neplatné vnoření.](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 Kompilátor jazyka Visual Basic zjistí překrývající se ovládací prvek struktur a signály chybu v době kompilace.  
  
## <a name="see-also"></a>Viz také:
- [Tok řízení](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Rozhodovací struktury](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Struktury smyčky](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Ostatní řídicí struktury](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
