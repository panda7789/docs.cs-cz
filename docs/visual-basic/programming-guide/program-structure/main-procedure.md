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
ms.openlocfilehash: 641edd2d0e0dde5f509c8fa77ccf65358fa76a31
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833666"
---
# <a name="main-procedure-in-visual-basic"></a>Hlavní procedura v jazyce Visual Basic
Každá aplikace Visual Basic musí obsahovat proceduru volá `Main`. Tento postup slouží jako počáteční bod a celkové ovládání aplikace. Volání rozhraní .NET Framework vaší `Main` procedury při načtení aplikace a je připravený k předá řízení. Pokud vytváříte aplikace modelu Windows Forms, je nutné napsat `Main` postup pro aplikace, které běží na své vlastní.  
  
 `Main` obsahuje kód, který spustí první. V `Main`, můžete určit, jaký tvar má být načten jako první při spuštění programu, zjistěte, zda kopii aplikace je již spuštěn na systému, vytvořit sadu proměnných pro vaši aplikaci nebo otevřete databázi, která aplikace požaduje.  
  
## <a name="requirements-for-the-main-procedure"></a>Požadavky pro hlavní procedury  
 Musí obsahovat soubor, který běží na své vlastní (obvykle s příponou .exe) `Main` postup. Nespouští svůj vlastní knihovny (například s příponou .dll) a nevyžaduje, aby `Main` postup. Požadavky pro jiné typy projektů, že které lze vytvořit jsou následující:  
  
-   Konzolová aplikace spouští své vlastní, a je nutné zadat alespoň jeden `Main` postup. .  
  
-   Spustit na své vlastní aplikace Windows Forms. Však automaticky generuje kompilátor jazyka Visual Basic `Main` postup uvedený v takové aplikace a není nutné napsat jednu.  
  
-   Knihovny tříd nevyžadují, aby `Main` postup. Patří mezi ně ovládacího prvku knihovny Windows a knihovny webových ovládacích prvků. Webové aplikace jsou nasazeny jako knihoven tříd.  
  
## <a name="declaring-the-main-procedure"></a>Deklarace hlavní procedury  
 Existují čtyři způsoby, jak deklarovat `Main` postup. Můžete převzít argumenty nebo Ne, a může vrátit hodnotu či nikoli.  
  
> [!NOTE]
>  Pokud deklarujete `Main` ve třídě, je nutné použít `Shared` – klíčové slovo. V modulu `Main` nemusí být `Shared`.  
  
-   Nejjednodušší způsob je deklarovat `Sub` proceduru, která přijímají argumenty nebo vracet hodnotu.  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   `Main` Můžete také vrátit `Integer` hodnotu, která používá operační systém jako ukončovací kód pro váš program. Další programy můžete otestovat tento kód tím, že kontroluje hodnotu Windows. Pokud chcete vrátit ukončovací kód, je třeba deklarovat `Main` jako `Function` postupu namísto `Sub` postup.  
  
    ```  
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
  
-   `Main` Můžete taky využít `String` pole jako argument. Každý řetězec v poli obsahuje jeden z argumentů příkazového řádku použít k vyvolání programu. Můžete provádět různé akce v závislosti na jejich hodnoty.  
  
    ```  
    Module mainModule  
        Function Main(ByVal cmdArgs() As String) As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
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
  
-   Je možné deklarovat `Main` Zkontrolujte argumenty příkazového řádku, ale nevrátí ukončovací kód, následujícím způsobem.  
  
    ```  
    Module mainModule  
        Sub Main(ByVal cmdArgs() As String)  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
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
- [Struktura programu v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [/main](../../../visual-basic/reference/command-line-compiler/main.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Datový typ Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Datový typ String](../../../visual-basic/language-reference/data-types/string-data-type.md)
