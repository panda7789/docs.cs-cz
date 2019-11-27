---
title: 'Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy.'
ms.date: 07/20/2015
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
ms.openlocfilehash: 790c680744e2100a40a7cea8b8cef80c68d586bb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348736"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy (Visual Basic).

Pokud pracujete se třídou, modulem nebo strukturou, která má členy unsigned integerch typů, můžete k těmto členům přistupovat pomocí Visual Basic.

## <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>Volání funkce systému Windows, která přebírá typ bez znaménka

1. Použijte [příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md) k oznámení Visual Basic, která knihovna obsahuje funkci, co je jeho název v této knihovně, co je jeho volající sekvence a jak převést řetězce při volání.

2. V příkazu `Declare` použijte `UInteger`, `ULong`, `UShort`nebo `Byte` jako vhodný pro každý parametr s typem bez znaménka.

3. V dokumentaci pro funkci Windows, kterou voláte, vyhledejte názvy a hodnoty konstant, které používá. Mnohé z těchto jsou definovány v souboru WinUser. h.

4. Deklaruje nezbytné konstanty ve vašem kódu. Mnoho konstant systému Windows je 32 nepodepsaných hodnot, které byste měli deklarovat `As UInteger`.

5. Volejte funkci normálním způsobem. Následující příklad volá funkci Windows `MessageBox`, která přijímá argument unsigned integer.

    ```vb
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

     Funkci můžete testovat `messageThroughWindows` s následujícím kódem.

    ```vb
    Public Sub consumeWindowsMessage()
        Dim w As New windowsMessage
        w.messageThroughWindows()
    End Sub
    ```

    > [!CAUTION]
    > Datové typy `UInteger`, `ULong`, `UShort`a `SByte` nejsou součástí [nezávislosti jazyka a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), takže kód kompatibilní se specifikací CLS nemůže spotřebovat komponentu, která je používá.

    > [!IMPORTANT]
    > Volání nespravovaného kódu, jako je rozhraní API (Application Programming Interface) systému Windows, zpřístupňuje váš kód potenciálním bezpečnostním rizikům.

    > [!IMPORTANT]
    > Volání rozhraní API systému Windows vyžaduje oprávnění nespravovaného kódu, které může ovlivnit jeho spuštění v situacích s částečnou důvěryhodností. Další informace najdete v tématu <xref:System.Security.Permissions.SecurityPermission> a [přístupová oprávnění kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).

## <a name="see-also"></a>Viz také:

- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Datový typ Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Datový typ UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)
- [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Návod: Volání rozhraní API systému Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
