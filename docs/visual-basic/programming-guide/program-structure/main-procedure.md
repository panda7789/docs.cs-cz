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
ms.openlocfilehash: b84bf20acaaa912e47102973b0484d635f1aa244
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679419"
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="921bd-102">Hlavní procedura v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="921bd-102">Main Procedure in Visual Basic</span></span>
<span data-ttu-id="921bd-103">Každá aplikace Visual Basic musí obsahovat proceduru volá `Main`.</span><span class="sxs-lookup"><span data-stu-id="921bd-103">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="921bd-104">Tento postup slouží jako počáteční bod a celkové ovládání aplikace.</span><span class="sxs-lookup"><span data-stu-id="921bd-104">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="921bd-105">Volání rozhraní .NET Framework vaší `Main` procedury při načtení aplikace a je připravený k předá řízení.</span><span class="sxs-lookup"><span data-stu-id="921bd-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="921bd-106">Pokud vytváříte aplikace modelu Windows Forms, je nutné napsat `Main` postup pro aplikace, které běží na své vlastní.</span><span class="sxs-lookup"><span data-stu-id="921bd-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>  
  
 <span data-ttu-id="921bd-107">`Main` obsahuje kód, který spustí první.</span><span class="sxs-lookup"><span data-stu-id="921bd-107">`Main` contains the code that runs first.</span></span> <span data-ttu-id="921bd-108">V `Main`, můžete určit, jaký tvar má být načten jako první při spuštění programu, zjistěte, zda kopii aplikace je již spuštěn na systému, vytvořit sadu proměnných pro vaši aplikaci nebo otevřete databázi, která aplikace požaduje.</span><span class="sxs-lookup"><span data-stu-id="921bd-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>  
  
## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="921bd-109">Požadavky pro hlavní procedury</span><span class="sxs-lookup"><span data-stu-id="921bd-109">Requirements for the Main Procedure</span></span>  
 <span data-ttu-id="921bd-110">Musí obsahovat soubor, který běží na své vlastní (obvykle s příponou .exe) `Main` postup.</span><span class="sxs-lookup"><span data-stu-id="921bd-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="921bd-111">Nespouští svůj vlastní knihovny (například s příponou .dll) a nevyžaduje, aby `Main` postup.</span><span class="sxs-lookup"><span data-stu-id="921bd-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="921bd-112">Požadavky pro jiné typy projektů, že které lze vytvořit jsou následující:</span><span class="sxs-lookup"><span data-stu-id="921bd-112">The requirements for the different types of projects you can create are as follows:</span></span>  
  
-   <span data-ttu-id="921bd-113">Konzolová aplikace spouští své vlastní, a je nutné zadat alespoň jeden `Main` postup.</span><span class="sxs-lookup"><span data-stu-id="921bd-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span> <span data-ttu-id="921bd-114">.</span><span class="sxs-lookup"><span data-stu-id="921bd-114">.</span></span>  
  
-   <span data-ttu-id="921bd-115">Spustit na své vlastní aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="921bd-115">Windows Forms applications run on their own.</span></span> <span data-ttu-id="921bd-116">Však automaticky generuje kompilátor jazyka Visual Basic `Main` postup uvedený v takové aplikace a není nutné napsat jednu.</span><span class="sxs-lookup"><span data-stu-id="921bd-116">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>  
  
-   <span data-ttu-id="921bd-117">Knihovny tříd nevyžadují, aby `Main` postup.</span><span class="sxs-lookup"><span data-stu-id="921bd-117">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="921bd-118">Patří mezi ně ovládacího prvku knihovny Windows a knihovny webových ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="921bd-118">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="921bd-119">Webové aplikace jsou nasazeny jako knihoven tříd.</span><span class="sxs-lookup"><span data-stu-id="921bd-119">Web applications are deployed as class libraries.</span></span>  
  
## <a name="declaring-the-main-procedure"></a><span data-ttu-id="921bd-120">Deklarace hlavní procedury</span><span class="sxs-lookup"><span data-stu-id="921bd-120">Declaring the Main Procedure</span></span>  
 <span data-ttu-id="921bd-121">Existují čtyři způsoby, jak deklarovat `Main` postup.</span><span class="sxs-lookup"><span data-stu-id="921bd-121">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="921bd-122">Můžete převzít argumenty nebo Ne, a může vrátit hodnotu či nikoli.</span><span class="sxs-lookup"><span data-stu-id="921bd-122">It can take arguments or not, and it can return a value or not.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="921bd-123">Pokud deklarujete `Main` ve třídě, je nutné použít `Shared` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="921bd-123">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="921bd-124">V modulu `Main` nemusí být `Shared`.</span><span class="sxs-lookup"><span data-stu-id="921bd-124">In a module, `Main` does not need to be `Shared`.</span></span>  
  
-   <span data-ttu-id="921bd-125">Nejjednodušší způsob je deklarovat `Sub` proceduru, která přijímají argumenty nebo vracet hodnotu.</span><span class="sxs-lookup"><span data-stu-id="921bd-125">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   <span data-ttu-id="921bd-126">`Main` Můžete také vrátit `Integer` hodnotu, která používá operační systém jako ukončovací kód pro váš program.</span><span class="sxs-lookup"><span data-stu-id="921bd-126">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="921bd-127">Další programy můžete otestovat tento kód tím, že kontroluje hodnotu Windows.</span><span class="sxs-lookup"><span data-stu-id="921bd-127">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="921bd-128">Pokud chcete vrátit ukončovací kód, je třeba deklarovat `Main` jako `Function` postupu namísto `Sub` postup.</span><span class="sxs-lookup"><span data-stu-id="921bd-128">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>  
  
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
  
-   <span data-ttu-id="921bd-129">`Main` Můžete taky využít `String` pole jako argument.</span><span class="sxs-lookup"><span data-stu-id="921bd-129">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="921bd-130">Každý řetězec v poli obsahuje jeden z argumentů příkazového řádku použít k vyvolání programu.</span><span class="sxs-lookup"><span data-stu-id="921bd-130">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="921bd-131">Můžete provádět různé akce v závislosti na jejich hodnoty.</span><span class="sxs-lookup"><span data-stu-id="921bd-131">You can take different actions depending on their values.</span></span>  
  
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
  
-   <span data-ttu-id="921bd-132">Je možné deklarovat `Main` Zkontrolujte argumenty příkazového řádku, ale nevrátí ukončovací kód, následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="921bd-132">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="921bd-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="921bd-133">See also</span></span>
- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="921bd-134">Struktura programu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="921bd-134">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="921bd-135">/main</span><span class="sxs-lookup"><span data-stu-id="921bd-135">/main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="921bd-136">Shared</span><span class="sxs-lookup"><span data-stu-id="921bd-136">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="921bd-137">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="921bd-137">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="921bd-138">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="921bd-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="921bd-139">Datový typ Integer</span><span class="sxs-lookup"><span data-stu-id="921bd-139">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="921bd-140">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="921bd-140">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
