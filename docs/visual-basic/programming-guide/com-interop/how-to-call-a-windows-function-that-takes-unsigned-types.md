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
ms.openlocfilehash: d1a679242f89c17e58a837ac2d356e1594972fb3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374554"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="0f449-102">Postupy: Volání funkce Windows, která přebírá nepřiřazené typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f449-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>

<span data-ttu-id="0f449-103">Pokud spotřebovávají třídy, modulu nebo struktura, která obsahuje členy typů celé číslo bez znaménka, získáte přístup k těmto členům s jazykem Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0f449-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with Visual Basic.</span></span>

### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="0f449-104">Pro volání funkce Windows, která přebírá typ bez znaménka</span><span class="sxs-lookup"><span data-stu-id="0f449-104">To call a Windows function that takes an unsigned type</span></span>

1. <span data-ttu-id="0f449-105">Použití [deklaraci příkazu](../../../visual-basic/language-reference/statements/declare-statement.md) říct jazyka Visual Basic, která knihovna obsahuje funkce, jeho název je v této knihovně, co je jeho volací sekvence a převod řetězce při svém volání.</span><span class="sxs-lookup"><span data-stu-id="0f449-105">Use a [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) to tell Visual Basic which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>

2. <span data-ttu-id="0f449-106">V `Declare` příkazu, použijte `UInteger`, `ULong`, `UShort`, nebo `Byte` podle potřeby pro každý parametr s typem bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="0f449-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>

3. <span data-ttu-id="0f449-107">V dokumentaci pro funkci Windows, ke kterému se připojujete k vyhledání názvy a hodnoty konstant, které používá.</span><span class="sxs-lookup"><span data-stu-id="0f449-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="0f449-108">Mnohé z nich jsou definovány v souboru WINUSER.</span><span class="sxs-lookup"><span data-stu-id="0f449-108">Many of these are defined in the WinUser.h file.</span></span>

4. <span data-ttu-id="0f449-109">Deklarujte nezbytné konstanty ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="0f449-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="0f449-110">Řada Windows konstanty jsou 32bitové hodnoty bez znaménka a by měla deklarovat tyto `As UInteger`.</span><span class="sxs-lookup"><span data-stu-id="0f449-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As UInteger`.</span></span>

5. <span data-ttu-id="0f449-111">Volání funkce běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="0f449-111">Call the function in the normal way.</span></span> <span data-ttu-id="0f449-112">Následující příklad volá funkci Windows `MessageBox`, která přebírá argument, celé číslo bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="0f449-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>

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

     <span data-ttu-id="0f449-113">Můžete otestovat funkci `messageThroughWindows` následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="0f449-113">You can test the function `messageThroughWindows` with the following code.</span></span>

    ```vb
    Public Sub consumeWindowsMessage()
        Dim w As New windowsMessage
        w.messageThroughWindows()
    End Sub
    ```

    > [!CAUTION]
    > <span data-ttu-id="0f449-114">`UInteger`, `ULong`, `UShort`, A `SByte` datových typů nejsou součástí [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), takže kód kompatibilní se Specifikací CLS nemůže využívat komponentu, která je využívá.</span><span class="sxs-lookup"><span data-stu-id="0f449-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="0f449-115">Volání nespravovaného kódu, jako je například rozhraní (API), Windows poskytuje kódu na potenciální rizika zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0f449-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="0f449-116">Volání rozhraní API pro Windows vyžaduje oprávnění nespravovaného kódu, který může mít vliv na jeho spuštění v situacích částečné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="0f449-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="0f449-117">Další informace najdete v tématu <xref:System.Security.Permissions.SecurityPermission> a [oprávnění přístupu ke kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0f449-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f449-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f449-118">See also</span></span>

- [<span data-ttu-id="0f449-119">Datové typy</span><span class="sxs-lookup"><span data-stu-id="0f449-119">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="0f449-120">Datový typ Integer</span><span class="sxs-lookup"><span data-stu-id="0f449-120">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="0f449-121">Datový typ UInteger</span><span class="sxs-lookup"><span data-stu-id="0f449-121">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)
- [<span data-ttu-id="0f449-122">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="0f449-122">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="0f449-123">Návod: Volání rozhraní API systému Windows</span><span class="sxs-lookup"><span data-stu-id="0f449-123">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
