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
# <a name="nested-control-structures-visual-basic"></a>Vnořené řídicí struktury (Visual Basic)
Můžete umístit řídicí příkazy uvnitř jiné řídicí příkazy, například `If...Then...Else` blokovat v rámci `For...Next` smyčky. Příkaz Ovládací prvek umístěn uvnitř jiného příkazu ovládací prvek se říká, že *vnořené*.  
  
## <a name="nesting-levels"></a>Úrovně vnoření  
 Na libovolný počet úrovní můžete vnořené řídicí struktury v jazyku Visual Basic. Je obvyklé, aby byl čitelnější vnořené struktury odsazením text každé z nich. Integrované vývojové prostředí (IDE) editoru automaticky tomu.  
  
 V následujícím příkladu, postup `sumRows` přidá společně kladné elementy každý řádek matice.  
  
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
  
 V předchozím příkladu první `Next` příkaz zavře vnitřní `For` smyčky a poslední `Next` příkaz zavře vnější `For` smyčky.  
  
 Podobně ve vnořených `If` příkazy, `End If` příkazy automaticky použít pro nejbližší před `If` příkaz. Vnořené `Do` smyčky fungovat podobným způsobem, s nejvnitřnější `Loop` příkaz odpovídající nejvnitřnější `Do` příkaz.  
  
> [!NOTE]
>  Pro mnoho řídicí struktury po kliknutí na tlačítko klíčové slovo, všechny klíčová slova ve struktuře jsou vyznačené. Například když kliknete na tlačítko `If` v `If...Then...Else` konstrukce, všechny instance `If`, `Then`, `ElseIf`, `Else`, a `End If` jsou vyznačené při sestavování. Chcete-li přesunout další nebo předchozí zvýrazněný – klíčové slovo, stiskněte CTRL + SHIFT + šipka dolů nebo CTRL + SHIFT + šipka nahoru.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Vnoření různé druhy řídicí struktury  
 Lze vnořit jednoho druhu řízení struktury v rámci jiného typu. Následující příklad používá `With` blokovat uvnitř `For Each` smyčky a vnořené `If` blokuje uvnitř `With` bloku.  
  
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
  
## <a name="overlapping-control-structures"></a>Překrývající se řídicí struktury  
 Řídicí struktury nesmí překrývat. To znamená, že všechny vnořené struktury musí být zcela obsažen v další nejvnitřnější strukturu. Například následující uspořádání je neplatný protože `For` smyčky ukončí před vnitřní `With` ukončí bloku.  
  
 ![Grafický diagram neplatný vnoření](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")  
Neplatný vnořené pro a struktury  
  
 Visual Basic – kompilátor zjistí takové překrývající se řídicí struktury a signály chyby kompilace.  
  
## <a name="see-also"></a>Viz také  
 [Tok řízení](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Rozhodovací struktury](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Struktury smyčky](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Ostatní řídicí struktury](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
