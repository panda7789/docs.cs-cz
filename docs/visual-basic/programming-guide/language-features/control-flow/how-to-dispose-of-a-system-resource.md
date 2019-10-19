---
title: 'Postupy: Odstranění systémového prostředku (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: c780ee1a174ad044593960bc30a3ee2e1f929390
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583148"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="1deb3-102">Postupy: Odstranění systémového prostředku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1deb3-102">How to: Dispose of a System Resource (Visual Basic)</span></span>
<span data-ttu-id="1deb3-103">Můžete použít `Using` blok k zajištění toho, aby systém odstranil prostředek, když váš kód ukončuje blok.</span><span class="sxs-lookup"><span data-stu-id="1deb3-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="1deb3-104">To je užitečné v případě, že používáte systémový prostředek, který spotřebovává velké množství paměti, nebo že jiné komponenty mají být také používány.</span><span class="sxs-lookup"><span data-stu-id="1deb3-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="1deb3-105">Vyřazení databázového připojení, když je kód dokončen</span><span class="sxs-lookup"><span data-stu-id="1deb3-105">To dispose of a database connection when your code is finished with it</span></span>  
  
1. <span data-ttu-id="1deb3-106">Ujistěte se, že jste zahrnuli příslušný [příkaz Imports (obor názvů a typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro připojení k databázi na začátku zdrojového souboru (v tomto případě <xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="1deb3-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2. <span data-ttu-id="1deb3-107">Vytvořte `Using` blok s příkazy `Using` a `End Using`.</span><span class="sxs-lookup"><span data-stu-id="1deb3-107">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="1deb3-108">Uvnitř bloku vložte kód, který se zabývá připojením k databázi.</span><span class="sxs-lookup"><span data-stu-id="1deb3-108">Inside the block, put the code that deals with the database connection.</span></span>  
  
3. <span data-ttu-id="1deb3-109">Deklarujte připojení a vytvořte jeho instanci jako součást příkazu `Using`.</span><span class="sxs-lookup"><span data-stu-id="1deb3-109">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```vb  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="1deb3-110">Systém uvolní prostředek bez ohledu na to, jakým způsobem ukončujete blok, včetně případu neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="1deb3-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="1deb3-111">Všimněte si, že nemůžete získat přístup k `sqc` mimo blok `Using`, protože jeho rozsah je omezen na blok.</span><span class="sxs-lookup"><span data-stu-id="1deb3-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="1deb3-112">Stejnou techniku můžete použít pro systémový prostředek, jako je například popisovač souboru nebo Obálka COM.</span><span class="sxs-lookup"><span data-stu-id="1deb3-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="1deb3-113">@No__t_0 blok použijete, pokud chcete mít jistotu, že je prostředek k dispozici pro jiné součásti po ukončení bloku `Using`.</span><span class="sxs-lookup"><span data-stu-id="1deb3-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1deb3-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1deb3-114">See also</span></span>

- <xref:System.Data.SqlClient.SqlConnection>
- [<span data-ttu-id="1deb3-115">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="1deb3-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="1deb3-116">Rozhodovací struktury</span><span class="sxs-lookup"><span data-stu-id="1deb3-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="1deb3-117">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="1deb3-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="1deb3-118">Ostatní řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="1deb3-118">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="1deb3-119">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="1deb3-119">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="1deb3-120">Příkaz Using</span><span class="sxs-lookup"><span data-stu-id="1deb3-120">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
