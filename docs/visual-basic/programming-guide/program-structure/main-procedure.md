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
ms.openlocfilehash: 1c76e3ade0b383727c3241fdaf5ae44b677559c8
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775697"
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="eaf99-102">Hlavní procedura v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eaf99-102">Main Procedure in Visual Basic</span></span>
<span data-ttu-id="eaf99-103">Každá aplikace Visual Basic musí obsahovat proceduru nazvanou `Main`.</span><span class="sxs-lookup"><span data-stu-id="eaf99-103">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="eaf99-104">Tato procedura slouží jako výchozí bod a celkový ovládací prvek pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="eaf99-104">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="eaf99-105">.NET Framework volá váš `Main` postup, když načte vaši aplikaci a je připravena k předání řízení.</span><span class="sxs-lookup"><span data-stu-id="eaf99-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="eaf99-106">Pokud nevytváříte aplikaci model Windows Forms, je nutné napsat `Main` postup pro aplikace, které se spouštějí sami.</span><span class="sxs-lookup"><span data-stu-id="eaf99-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>

 <span data-ttu-id="eaf99-107">`Main` obsahuje kód, který se spouští jako první.</span><span class="sxs-lookup"><span data-stu-id="eaf99-107">`Main` contains the code that runs first.</span></span> <span data-ttu-id="eaf99-108">V `Main` můžete určit, který formulář se má načíst jako první, když se program spustí, zjistit, jestli je už kopie vaší aplikace spuštěná v systému, vytvořit sadu proměnných pro vaši aplikaci nebo otevřít databázi, kterou aplikace vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="eaf99-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>

## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="eaf99-109">Požadavky na hlavní postup</span><span class="sxs-lookup"><span data-stu-id="eaf99-109">Requirements for the Main Procedure</span></span>
 <span data-ttu-id="eaf99-110">Soubor, který se spouští sám (obvykle s příponou. exe), musí obsahovat `Main` postup.</span><span class="sxs-lookup"><span data-stu-id="eaf99-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="eaf99-111">Knihovnu (například s příponou. dll) neběží sama na sobě a nevyžaduje `Main` postup.</span><span class="sxs-lookup"><span data-stu-id="eaf99-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="eaf99-112">Požadavky pro různé typy projektů, které můžete vytvořit, jsou následující:</span><span class="sxs-lookup"><span data-stu-id="eaf99-112">The requirements for the different types of projects you can create are as follows:</span></span>

- <span data-ttu-id="eaf99-113">Konzolové aplikace běží samy na sobě a Vy musíte dodat aspoň jeden `Main` postup.</span><span class="sxs-lookup"><span data-stu-id="eaf99-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span>

- <span data-ttu-id="eaf99-114">Model Windows Forms aplikace se spouštějí sami.</span><span class="sxs-lookup"><span data-stu-id="eaf99-114">Windows Forms applications run on their own.</span></span> <span data-ttu-id="eaf99-115">Kompilátor Visual Basic však v takové aplikaci automaticky vygeneruje `Main` proceduru a není nutné ji psát.</span><span class="sxs-lookup"><span data-stu-id="eaf99-115">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>

- <span data-ttu-id="eaf99-116">Knihovny tříd nevyžadují `Main` proceduru.</span><span class="sxs-lookup"><span data-stu-id="eaf99-116">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="eaf99-117">Mezi ně patří knihovny ovládacích prvků systému Windows a knihovny webového ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="eaf99-117">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="eaf99-118">Webové aplikace jsou nasazeny jako knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="eaf99-118">Web applications are deployed as class libraries.</span></span>

## <a name="declaring-the-main-procedure"></a><span data-ttu-id="eaf99-119">Deklarace hlavní procedury</span><span class="sxs-lookup"><span data-stu-id="eaf99-119">Declaring the Main Procedure</span></span>
 <span data-ttu-id="eaf99-120">Existují čtyři způsoby, jak deklarovat `Main` proceduru.</span><span class="sxs-lookup"><span data-stu-id="eaf99-120">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="eaf99-121">Může přijmout argumenty nebo ne a může vrátit hodnotu nebo ne.</span><span class="sxs-lookup"><span data-stu-id="eaf99-121">It can take arguments or not, and it can return a value or not.</span></span>

> [!NOTE]
> <span data-ttu-id="eaf99-122">Pokud deklarujete `Main` ve třídě, je nutné použít klíčové slovo `Shared`.</span><span class="sxs-lookup"><span data-stu-id="eaf99-122">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="eaf99-123">V modulu není `Main` nutné `Shared`.</span><span class="sxs-lookup"><span data-stu-id="eaf99-123">In a module, `Main` does not need to be `Shared`.</span></span>

- <span data-ttu-id="eaf99-124">Nejjednodušší způsob je deklarovat `Sub` proceduru, která nepřijímá argumenty nebo vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="eaf99-124">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- <span data-ttu-id="eaf99-125">`Main` může také vracet `Integer` hodnotu, kterou operační systém používá jako ukončovací kód pro váš program.</span><span class="sxs-lookup"><span data-stu-id="eaf99-125">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="eaf99-126">Další programy můžou tento kód otestovat prozkoumáním hodnoty ERRORLEVEL systému Windows.</span><span class="sxs-lookup"><span data-stu-id="eaf99-126">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="eaf99-127">Chcete-li vrátit ukončovací kód, je nutné deklarovat `Main` jako `Function` procedura namísto `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="eaf99-127">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>

    ```vb
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

- <span data-ttu-id="eaf99-128">`Main` může také přebírat pole `String` jako argument.</span><span class="sxs-lookup"><span data-stu-id="eaf99-128">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="eaf99-129">Každý řetězec v poli obsahuje jeden z argumentů příkazového řádku, který se používá k vyvolání programu.</span><span class="sxs-lookup"><span data-stu-id="eaf99-129">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="eaf99-130">V závislosti na jejich hodnotách můžete provádět různé akce.</span><span class="sxs-lookup"><span data-stu-id="eaf99-130">You can take different actions depending on their values.</span></span>

    ```vb
    Module mainModule
        Function Main(ByVal cmdArgs() As String) As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
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

- <span data-ttu-id="eaf99-131">Můžete deklarovat `Main` pro prohlédnutí argumentů příkazového řádku, ale nevrátí ukončovací kód, a to následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="eaf99-131">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>

    ```vb
    Module mainModule
        Sub Main(ByVal cmdArgs() As String)
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```
  
## <a name="see-also"></a><span data-ttu-id="eaf99-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eaf99-132">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="eaf99-133">Struktura Visual Basic programu</span><span class="sxs-lookup"><span data-stu-id="eaf99-133">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="eaf99-134">-main</span><span class="sxs-lookup"><span data-stu-id="eaf99-134">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="eaf99-135">Shared</span><span class="sxs-lookup"><span data-stu-id="eaf99-135">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="eaf99-136">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="eaf99-136">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="eaf99-137">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="eaf99-137">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="eaf99-138">Datový typ Integer</span><span class="sxs-lookup"><span data-stu-id="eaf99-138">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="eaf99-139">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="eaf99-139">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
