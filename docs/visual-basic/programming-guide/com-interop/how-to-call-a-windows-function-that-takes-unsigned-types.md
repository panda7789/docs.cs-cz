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
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="40f72-102">Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="40f72-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>
<span data-ttu-id="40f72-103">Pokud jsou využívání třídu, modul nebo struktura, která má členů typů celé číslo bez znaménka, dostanete tito členové s [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40f72-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="40f72-104">Volání funkce systému Windows, která má typ bez znaménka</span><span class="sxs-lookup"><span data-stu-id="40f72-104">To call a Windows function that takes an unsigned type</span></span>  
  
1.  <span data-ttu-id="40f72-105">Použití [deklarovat příkaz](../../../visual-basic/language-reference/statements/declare-statement.md) říct [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] které knihovna obsahuje funkce, jeho název je v této knihovně, co je jeho volací sekvence a jak převést řetězce při volání metody ho.</span><span class="sxs-lookup"><span data-stu-id="40f72-105">Use a [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) to tell [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>  
  
2.  <span data-ttu-id="40f72-106">V `Declare` příkaz, použijte `UInteger`, `ULong`, `UShort`, nebo `Byte` podle potřeby pro každý parametr typu bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="40f72-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>  
  
3.  <span data-ttu-id="40f72-107">V dokumentaci pro funkce systému Windows, ke kterému se připojujete k vyhledání názvy a hodnoty konstant, které používá.</span><span class="sxs-lookup"><span data-stu-id="40f72-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="40f72-108">Mnoho z těchto jsou definovány v souboru WINUSER.</span><span class="sxs-lookup"><span data-stu-id="40f72-108">Many of these are defined in the WinUser.h file.</span></span>  
  
4.  <span data-ttu-id="40f72-109">Deklarujte nezbytné konstanty v kódu.</span><span class="sxs-lookup"><span data-stu-id="40f72-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="40f72-110">Mnoho konstanty Windows jsou hodnoty bez znaménka 32bitová verze a by měly deklarovat tyto `As``UInteger`.</span><span class="sxs-lookup"><span data-stu-id="40f72-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As``UInteger`.</span></span>  
  
5.  <span data-ttu-id="40f72-111">Volání funkce běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="40f72-111">Call the function in the normal way.</span></span> <span data-ttu-id="40f72-112">V následujícím příkladu volání funkce systému Windows `MessageBox`, což trvá argument celé číslo bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="40f72-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>  
  
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
  
     <span data-ttu-id="40f72-113">Můžete otestovat funkci `messageThroughWindows` následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="40f72-113">You can test the function `messageThroughWindows` with the following code.</span></span>  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  <span data-ttu-id="40f72-114">`UInteger`, `ULong`, `UShort`, A `SByte` datové typy nejsou součástí [jazyková nezávislost a jazykově nezávislé komponenty](../../../../docs/standard/language-independence-and-language-independent-components.md) CLS (), takže kompatibilní se specifikací CLS kódu nemůže využívat komponentu, používá je.</span><span class="sxs-lookup"><span data-stu-id="40f72-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="40f72-115">Provádění volání nespravovaného kódu, například rozhraní (API) Windows zpřístupní kódu na potenciální rizika zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="40f72-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="40f72-116">Volání rozhraní API systému Windows vyžaduje oprávnění nespravovaného kódu, což může mít vliv na jeho spuštění v situacích s částečným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="40f72-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="40f72-117">Další informace najdete v tématu <xref:System.Security.Permissions.SecurityPermission> a [přístupová oprávnění kódu](http://msdn.microsoft.com/en-us/e5ae402f-6dda-4732-bbe8-77296630f675).</span><span class="sxs-lookup"><span data-stu-id="40f72-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](http://msdn.microsoft.com/en-us/e5ae402f-6dda-4732-bbe8-77296630f675).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40f72-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="40f72-118">See Also</span></span>  
 [<span data-ttu-id="40f72-119">Datové typy</span><span class="sxs-lookup"><span data-stu-id="40f72-119">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="40f72-120">Integer – datový typ</span><span class="sxs-lookup"><span data-stu-id="40f72-120">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="40f72-121">Uinteger – datový typ</span><span class="sxs-lookup"><span data-stu-id="40f72-121">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
 [<span data-ttu-id="40f72-122">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="40f72-122">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="40f72-123">Návod: Volání rozhraní API systému Windows</span><span class="sxs-lookup"><span data-stu-id="40f72-123">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
