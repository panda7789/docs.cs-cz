---
title: 'Postupy: Volání funkce Windows, která přebírá typy bez znaménka'
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
ms.openlocfilehash: f30b78a2f0c38f233796e18006c889438dce4c58
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396827"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy (Visual Basic).

Pokud pracujete se třídou, modulem nebo strukturou, která má členy unsigned integerch typů, můžete k těmto členům přistupovat pomocí Visual Basic.

## <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>Volání funkce systému Windows, která přebírá typ bez znaménka

1. Použijte [příkaz Declare](../../language-reference/statements/declare-statement.md) k oznámení Visual Basic, která knihovna obsahuje funkci, co je jeho název v této knihovně, co je jeho volající sekvence a jak převést řetězce při volání.

2. V `Declare` příkazu použijte,, `UInteger` `ULong` `UShort` nebo `Byte` jako vhodný pro každý parametr s typem bez znaménka.

3. V dokumentaci pro funkci Windows, kterou voláte, vyhledejte názvy a hodnoty konstant, které používá. Mnohé z těchto jsou definovány v souboru WinUser. h.

4. Deklaruje nezbytné konstanty ve vašem kódu. Mnoho konstant systému Windows je 32 hodnot bez znaménka a je nutné je deklarovat `As UInteger` .

5. Volejte funkci normálním způsobem. Následující příklad volá funkci systému Windows `MessageBox` , která přebírá unsigned integer argument.

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

     Funkci lze otestovat `messageThroughWindows` pomocí následujícího kódu.

    ```vb
    Public Sub consumeWindowsMessage()
        Dim w As New windowsMessage
        w.messageThroughWindows()
    End Sub
    ```

    > [!CAUTION]
    > `UInteger` `ULong` Datové typy,, a nejsou součástí nezávislého `UShort` `SByte` [jazyka a jazykově nezávislých komponent](../../../standard/language-independence-and-language-independent-components.md) (CLS), takže kód kompatibilní se specifikací CLS nemůže spotřebovat komponentu, která je používá.

    > [!IMPORTANT]
    > Volání nespravovaného kódu, jako je rozhraní API (Application Programming Interface) systému Windows, zpřístupňuje váš kód potenciálním bezpečnostním rizikům.

    > [!IMPORTANT]
    > Volání rozhraní API systému Windows vyžaduje oprávnění nespravovaného kódu, které může ovlivnit jeho spuštění v situacích s částečnou důvěryhodností. Další informace naleznete v tématu <xref:System.Security.Permissions.SecurityPermission> a [oprávnění k přístupu kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).

## <a name="see-also"></a>Viz také

- [Datové typy](../../language-reference/data-types/index.md)
- [Integer – datový typ](../../language-reference/data-types/integer-data-type.md)
- [UInteger – datový typ](../../language-reference/data-types/uinteger-data-type.md)
- [Declare – příkaz](../../language-reference/statements/declare-statement.md)
- [Návod: Volání rozhraní API systému Windows](walkthrough-calling-windows-apis.md)
