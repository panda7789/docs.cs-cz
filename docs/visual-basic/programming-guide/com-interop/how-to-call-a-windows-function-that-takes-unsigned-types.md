---
title: 'Postupy: Volání funkce Windows, která přebírá nepřiřazené typy (Visual Basic)'
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
ms.openlocfilehash: dbe73ed5574261f1aab6134a15a5aeb5fbb8596c
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2019
ms.locfileid: "55065853"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>Postupy: Volání funkce Windows, která přebírá nepřiřazené typy (Visual Basic)
Pokud spotřebovávají třídy, modulu nebo struktura, která obsahuje členy typů celé číslo bez znaménka, získáte přístup k těmto členům s jazykem Visual Basic.  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>Pro volání funkce Windows, která přebírá typ bez znaménka  
  
1.  Použití [deklaraci příkazu](../../../visual-basic/language-reference/statements/declare-statement.md) říct jazyka Visual Basic, která knihovna obsahuje funkce, jeho název je v této knihovně, co je jeho volací sekvence a převod řetězce při svém volání.  
  
2.  V `Declare` příkazu, použijte `UInteger`, `ULong`, `UShort`, nebo `Byte` podle potřeby pro každý parametr s typem bez znaménka.  
  
3.  V dokumentaci pro funkci Windows, ke kterému se připojujete k vyhledání názvy a hodnoty konstant, které používá. Mnohé z nich jsou definovány v souboru WINUSER.  
  
4.  Deklarujte nezbytné konstanty ve vašem kódu. Řada Windows konstanty jsou 32bitové hodnoty bez znaménka a by měla deklarovat tyto `As UInteger`.  
  
5.  Volání funkce běžným způsobem. Následující příklad volá funkci Windows `MessageBox`, která přebírá argument, celé číslo bez znaménka.  
  
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
    >  `UInteger`, `ULong`, `UShort`, A `SByte` datových typů nejsou součástí [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), takže kód kompatibilní se Specifikací CLS nemůže využívat komponentu, která je využívá.  
  
    > [!IMPORTANT]
    >  Volání nespravovaného kódu, jako je například rozhraní (API), Windows poskytuje kódu na potenciální rizika zabezpečení.  
  
    > [!IMPORTANT]
    >  Volání rozhraní API pro Windows vyžaduje oprávnění nespravovaného kódu, který může mít vliv na jeho spuštění v situacích částečné důvěryhodnosti. Další informace najdete v tématu <xref:System.Security.Permissions.SecurityPermission> a [oprávnění přístupu ke kódu](https://msdn.microsoft.com/library/e5ae402f-6dda-4732-bbe8-77296630f675).  
  
## <a name="see-also"></a>Viz také:
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Datový typ Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Datový typ UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)
- [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Návod: Volání rozhraní API systému Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
