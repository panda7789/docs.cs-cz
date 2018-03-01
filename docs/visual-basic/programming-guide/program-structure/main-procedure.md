---
title: "Hlavní procedura v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6de98ad4e470cd0becaf25f5a9a00c8095e44b15
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="main-procedure-in-visual-basic"></a>Hlavní procedura v jazyce Visual Basic
Každá aplikace Visual Basic musí obsahovat proceduře volána `Main`. Tento postup slouží jako počáteční bod a celkové řízení pro vaše aplikace. Volání rozhraní .NET Framework vaší `Main` procedury při načetl vaší aplikace a chce předá řízení. Pokud vytváříte aplikace Windows Forms, musíte napsat `Main` postup pro aplikace, které běží na své vlastní.  
  
 `Main`obsahuje kód, který spustí první. V `Main`, můžete určit, jaký typ je nejdřív načíst při spuštění programu, zjistěte, zda kopie aplikace je již spuštěn na systém, vytvořit sadu proměnných pro vaši aplikaci nebo otevřít databázi, která aplikace vyžaduje.  
  
## <a name="requirements-for-the-main-procedure"></a>Požadavky na hlavní procedury  
 Musí obsahovat soubor, který běží na svůj vlastní (obvykle s příponou .exe) `Main` postupu. Nejde spustit svůj vlastní knihovny (například s příponou .dll) a nevyžaduje `Main` postupu. Požadavky pro různé typy projektů, že které lze vytvořit jsou následující:  
  
-   Konzolové aplikace spustit na své vlastní, a je nutné zadat alespoň jeden `Main` postupu. .  
  
-   Windows Forms aplikace spustit na své vlastní. Ale Visual Basic – kompilátor automaticky generuje `Main` postup v například aplikace a není nutné zapsat jeden.  
  
-   Knihovny tříd nevyžadují `Main` postupu. Mezi ně patří Windows řízení knihoven a knihovny webových ovládacích prvků. Webové aplikace jsou nasazeny jako knihovny tříd.  
  
## <a name="declaring-the-main-procedure"></a>Deklarace hlavní procedura  
 Existují čtyři způsoby deklarovat `Main` postupu. Argumenty může trvat nebo Ne, a můžete vrátit hodnotu, nebo ne.  
  
> [!NOTE]
>  Pokud je deklarovat `Main` v třídě, je nutné použít `Shared` – klíčové slovo. V modulu `Main` nemusí být `Shared`.  
  
-   Nejjednodušší způsob je deklarovat `Sub` procedury, která nemá trvat argumenty nebo vrátit hodnotu.  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   `Main`Můžete se taky vrátit `Integer` hodnotu, kterou používá operační systém jako ukončovací kód k aplikaci. Další programy můžete otestovat tento kód tak, že prověří hodnotu Windows. Pokud chcete vrátit ukončovací kód, je potřeba deklarovat `Main` jako `Function` postup místo `Sub` postupu.  
  
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
  
-   `Main`Můžete taky využít `String` pole jako argument. Každý řetězec v poli, obsahuje jeden z argumentů příkazového řádku, použije k vyvolání vašeho programu. Můžete využít různé akce v závislosti na jejich hodnot.  
  
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
  
-   Je možné deklarovat `Main` Zkontrolujte argumenty příkazového řádku, ale není vrátí ukončovací kód, následujícím způsobem.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
 <xref:System.Array.Length%2A>  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [Struktura programu v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [/main](../../../visual-basic/reference/command-line-compiler/main.md)  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Datový typ Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Datový typ String](../../../visual-basic/language-reference/data-types/string-data-type.md)
