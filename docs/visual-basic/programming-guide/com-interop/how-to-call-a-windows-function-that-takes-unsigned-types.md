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
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="4edf7-102">Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="4edf7-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>

<span data-ttu-id="4edf7-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4edf7-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with Visual Basic.</span></span>

## <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="4edf7-104">To call a Windows function that takes an unsigned type</span><span class="sxs-lookup"><span data-stu-id="4edf7-104">To call a Windows function that takes an unsigned type</span></span>

1. <span data-ttu-id="4edf7-105">Use a [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) to tell Visual Basic which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span><span class="sxs-lookup"><span data-stu-id="4edf7-105">Use a [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) to tell Visual Basic which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>

2. <span data-ttu-id="4edf7-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span><span class="sxs-lookup"><span data-stu-id="4edf7-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>

3. <span data-ttu-id="4edf7-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span><span class="sxs-lookup"><span data-stu-id="4edf7-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="4edf7-108">Many of these are defined in the WinUser.h file.</span><span class="sxs-lookup"><span data-stu-id="4edf7-108">Many of these are defined in the WinUser.h file.</span></span>

4. <span data-ttu-id="4edf7-109">Declare the necessary constants in your code.</span><span class="sxs-lookup"><span data-stu-id="4edf7-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="4edf7-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As UInteger`.</span><span class="sxs-lookup"><span data-stu-id="4edf7-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As UInteger`.</span></span>

5. <span data-ttu-id="4edf7-111">Call the function in the normal way.</span><span class="sxs-lookup"><span data-stu-id="4edf7-111">Call the function in the normal way.</span></span> <span data-ttu-id="4edf7-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span><span class="sxs-lookup"><span data-stu-id="4edf7-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>

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

     <span data-ttu-id="4edf7-113">You can test the function `messageThroughWindows` with the following code.</span><span class="sxs-lookup"><span data-stu-id="4edf7-113">You can test the function `messageThroughWindows` with the following code.</span></span>

    ```vb
    Public Sub consumeWindowsMessage()
        Dim w As New windowsMessage
        w.messageThroughWindows()
    End Sub
    ```

    > [!CAUTION]
    > <span data-ttu-id="4edf7-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span><span class="sxs-lookup"><span data-stu-id="4edf7-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="4edf7-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span><span class="sxs-lookup"><span data-stu-id="4edf7-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="4edf7-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span><span class="sxs-lookup"><span data-stu-id="4edf7-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="4edf7-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4edf7-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="4edf7-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4edf7-118">See also</span></span>

- [<span data-ttu-id="4edf7-119">Datové typy</span><span class="sxs-lookup"><span data-stu-id="4edf7-119">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="4edf7-120">Datový typ Integer</span><span class="sxs-lookup"><span data-stu-id="4edf7-120">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="4edf7-121">Datový typ UInteger</span><span class="sxs-lookup"><span data-stu-id="4edf7-121">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)
- [<span data-ttu-id="4edf7-122">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="4edf7-122">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="4edf7-123">Návod: Volání rozhraní API systému Windows</span><span class="sxs-lookup"><span data-stu-id="4edf7-123">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
