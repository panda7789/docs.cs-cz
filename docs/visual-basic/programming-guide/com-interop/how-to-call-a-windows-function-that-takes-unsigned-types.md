---
title: "Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy (Visual Basic)."
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Windows functions [Visual Basic], calling
- unsigned data types [Visual Basic]
- UShort data type [Visual Basic], using
- functions [Visual Basic], calling Windows functions
- ULong data type [Visual Basic], using
- UInteger data type [Visual Basic], using
- data types [Visual Basic], using
- unsigned types [Visual Basic]
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types [Visual Basic], using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5b1a306ba694d4bbfc4719fc728112964b1ce40f
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy (Visual Basic).
Pokud jsou využívání třídu, modul nebo struktura, která má členů typů celé číslo bez znaménka, dostanete tito členové s [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>Volání funkce systému Windows, která má typ bez znaménka  
  
1.  Použití [deklarovat příkaz](../../../visual-basic/language-reference/statements/declare-statement.md) říct [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] které knihovna obsahuje funkce, jeho název je v této knihovně, co je jeho volací sekvence a jak převést řetězce při volání metody ho.  
  
2.  V `Declare` příkaz, použijte `UInteger`, `ULong`, `UShort`, nebo `Byte` podle potřeby pro každý parametr typu bez znaménka.  
  
3.  V dokumentaci pro funkce systému Windows, ke kterému se připojujete k vyhledání názvy a hodnoty konstant, které používá. Mnoho z těchto jsou definovány v souboru WINUSER.  
  
4.  Deklarujte nezbytné konstanty v kódu. Mnoho konstanty Windows jsou hodnoty bez znaménka 32bitová verze a by měly deklarovat tyto `As``UInteger`.  
  
5.  Volání funkce běžným způsobem. V následujícím příkladu volání funkce systému Windows `MessageBox`, což trvá argument celé číslo bez znaménka.  
  
    ```  
    Public Class windowsMessage  
        Private Declare Auto Function mb Lib "user32.dll" Alias "MessageBox" (  
            ByVal hWnd As Integer,   
            ByVal lpText As String,   
            ByVal lpCaption As String,   
            ByVal uType As UInteger) As Integer  
        Private Const MB_OK As UInteger = 0  
        Private Const MB_ICONEXCLAMATION As UInteger = &H30  
        Private Const IDOK As UInteger = 1  
        Private Const IDCLOSE As UInteger = 8  
        Private Const c As UInteger = MB_OK Or MB_ICONEXCLAMATION  
        Public Function messageThroughWindows() As String  
            Dim r As Integer = mb(0, "Click OK if you see this!",   
                "Windows API call", c)  
            Dim s As String = "Windows API MessageBox returned " &  
                 CStr(r)& vbCrLf & "(IDOK = " & CStr(IDOK) &  
                 ", IDCLOSE = " & CStr(IDCLOSE) & ")"  
            Return s  
        End Function  
    End Class  
    ```  
  
     Můžete otestovat funkci `messageThroughWindows` následujícím kódem.  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  `UInteger`, `ULong`, `UShort`, A `SByte` datové typy nejsou součástí [jazyková nezávislost a jazykově nezávislé komponenty](../../../../docs/standard/language-independence-and-language-independent-components.md) CLS (), takže kompatibilní se specifikací CLS kódu nemůže využívat komponentu, používá je.  
  
    > [!IMPORTANT]
    >  Provádění volání nespravovaného kódu, například rozhraní (API) Windows zpřístupní kódu na potenciální rizika zabezpečení.  
  
    > [!IMPORTANT]
    >  Volání rozhraní API systému Windows vyžaduje oprávnění nespravovaného kódu, což může mít vliv na jeho spuštění v situacích s částečným vztahem důvěryhodnosti. Další informace najdete v tématu <xref:System.Security.Permissions.SecurityPermission> a [přístupová oprávnění kódu](http://msdn.microsoft.com/en-us/e5ae402f-6dda-4732-bbe8-77296630f675).  
  
## <a name="see-also"></a>Viz také  
 [Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Integer – datový typ](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Uinteger – datový typ](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
 [Declare – příkaz](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Návod: Volání rozhraní API systému Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
