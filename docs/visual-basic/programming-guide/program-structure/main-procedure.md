---
title: Hlavní procedura v jazyce Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: 19c6fcb04a373d782db3deafc732f69bf20e7f0e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962764"
---
# <a name="main-procedure-in-visual-basic"></a>Hlavní procedura v jazyce Visual Basic
Každá aplikace Visual Basic musí obsahovat proceduru nazvanou `Main`. Tato procedura slouží jako výchozí bod a celkový ovládací prvek pro vaši aplikaci. .NET Framework volá `Main` proceduru, když načte vaši aplikaci a je připravena k předání řízení. Pokud nevytváříte aplikaci model Windows Forms, musíte napsat `Main` postup pro aplikace, které se spouštějí sami.

 `Main`obsahuje kód, který se spouští jako první. V `Main`nástroji můžete určit, který formulář se má načíst jako první, když se program spustí, zjistit, jestli je už kopie aplikace spuštěná v systému, vytvořit sadu proměnných pro vaši aplikaci nebo otevřít databázi, kterou aplikace vyžaduje.

## <a name="requirements-for-the-main-procedure"></a>Požadavky na hlavní postup
 Soubor, který se spouští sám (obvykle s příponou. exe), musí obsahovat `Main` proceduru. Knihovnu (například s příponou. dll) neběží sama o sobě a `Main` nevyžaduje postup. Požadavky pro různé typy projektů, které můžete vytvořit, jsou následující:

- Konzolové aplikace běží samy na sobě a Vy musíte dodat aspoň jeden `Main` postup.

- Model Windows Forms aplikace se spouštějí sami. Kompilátor Visual Basic však v takové aplikaci automaticky vygeneruje `Main` proceduru a není nutné ji psát.

- Knihovny tříd nevyžadují `Main` proceduru. Mezi ně patří knihovny ovládacích prvků systému Windows a knihovny webového ovládacího prvku. Webové aplikace jsou nasazeny jako knihovny tříd.

## <a name="declaring-the-main-procedure"></a>Deklarace hlavní procedury
 Existují čtyři způsoby, jak deklarovat `Main` proceduru. Může přijmout argumenty nebo ne a může vrátit hodnotu nebo ne.

> [!NOTE]
> Pokud deklarujete `Main` ve třídě, je nutné `Shared` použít klíčové slovo. V modulu `Main` nemusí být `Shared`.

- Nejjednodušší způsob je deklarovat `Sub` proceduru, která nepřijímá argumenty nebo vrací hodnotu.

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- `Main`může také vracet `Integer` hodnotu, kterou operační systém používá jako ukončovací kód pro váš program. Další programy můžou tento kód otestovat prozkoumáním hodnoty ERRORLEVEL systému Windows. Chcete-li vrátit ukončovací kód, musíte deklarovat `Main` `Function` jako proceduru namísto `Sub` procedury.

    ```vb
    Module mainModule
        Function Main() As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' Insert call to appropriate starting place in your code.
            ' On return, assign appropriate value to returnValue.
            ' 0 usually means successful completion.
            MsgBox("The application is terminating with error level " &
                 CStr(returnValue) & ".")
            Return returnValue
        End Function
    End Module
    ```

- `Main`může také převzít `String` pole jako argument. Každý řetězec v poli obsahuje jeden z argumentů příkazového řádku, který se používá k vyvolání programu. V závislosti na jejich hodnotách můžete provádět různé akce.

    ```vb
    Module mainModule
        Function Main(ByVal cmdArgs() As String) As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            ' On return, assign appropriate value to returnValue.
            ' 0 usually means successful completion.
            MsgBox("The application is terminating with error level " &
                 CStr(returnValue) & ".")
            Return returnValue
        End Function
    End Module
    ```

- Můžete deklarovat `Main` pro prohlédnutí argumentů příkazového řádku, ale nevrátí ukončovací kód, a to následujícím způsobem.

    ```vb
    Module mainModule
        Sub Main(ByVal cmdArgs() As String)
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [Struktura Visual Basic programu](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [/main](../../../visual-basic/reference/command-line-compiler/main.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Datový typ Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Datový typ String](../../../visual-basic/language-reference/data-types/string-data-type.md)
