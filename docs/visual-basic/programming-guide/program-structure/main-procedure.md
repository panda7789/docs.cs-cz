---
title: "Hlavní procedura v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6de98ad4e470cd0becaf25f5a9a00c8095e44b15
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="33762-102">Hlavní procedura v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="33762-102">Main Procedure in Visual Basic</span></span>
<span data-ttu-id="33762-103">Každá aplikace Visual Basic musí obsahovat proceduře volána `Main`.</span><span class="sxs-lookup"><span data-stu-id="33762-103">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="33762-104">Tento postup slouží jako počáteční bod a celkové řízení pro vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="33762-104">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="33762-105">Volání rozhraní .NET Framework vaší `Main` procedury při načetl vaší aplikace a chce předá řízení.</span><span class="sxs-lookup"><span data-stu-id="33762-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="33762-106">Pokud vytváříte aplikace Windows Forms, musíte napsat `Main` postup pro aplikace, které běží na své vlastní.</span><span class="sxs-lookup"><span data-stu-id="33762-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>  
  
 <span data-ttu-id="33762-107">`Main`obsahuje kód, který spustí první.</span><span class="sxs-lookup"><span data-stu-id="33762-107">`Main` contains the code that runs first.</span></span> <span data-ttu-id="33762-108">V `Main`, můžete určit, jaký typ je nejdřív načíst při spuštění programu, zjistěte, zda kopie aplikace je již spuštěn na systém, vytvořit sadu proměnných pro vaši aplikaci nebo otevřít databázi, která aplikace vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="33762-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>  
  
## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="33762-109">Požadavky na hlavní procedury</span><span class="sxs-lookup"><span data-stu-id="33762-109">Requirements for the Main Procedure</span></span>  
 <span data-ttu-id="33762-110">Musí obsahovat soubor, který běží na svůj vlastní (obvykle s příponou .exe) `Main` postupu.</span><span class="sxs-lookup"><span data-stu-id="33762-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="33762-111">Nejde spustit svůj vlastní knihovny (například s příponou .dll) a nevyžaduje `Main` postupu.</span><span class="sxs-lookup"><span data-stu-id="33762-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="33762-112">Požadavky pro různé typy projektů, že které lze vytvořit jsou následující:</span><span class="sxs-lookup"><span data-stu-id="33762-112">The requirements for the different types of projects you can create are as follows:</span></span>  
  
-   <span data-ttu-id="33762-113">Konzolové aplikace spustit na své vlastní, a je nutné zadat alespoň jeden `Main` postupu.</span><span class="sxs-lookup"><span data-stu-id="33762-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span> <span data-ttu-id="33762-114">.</span><span class="sxs-lookup"><span data-stu-id="33762-114">.</span></span>  
  
-   <span data-ttu-id="33762-115">Windows Forms aplikace spustit na své vlastní.</span><span class="sxs-lookup"><span data-stu-id="33762-115">Windows Forms applications run on their own.</span></span> <span data-ttu-id="33762-116">Ale Visual Basic – kompilátor automaticky generuje `Main` postup v například aplikace a není nutné zapsat jeden.</span><span class="sxs-lookup"><span data-stu-id="33762-116">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>  
  
-   <span data-ttu-id="33762-117">Knihovny tříd nevyžadují `Main` postupu.</span><span class="sxs-lookup"><span data-stu-id="33762-117">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="33762-118">Mezi ně patří Windows řízení knihoven a knihovny webových ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="33762-118">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="33762-119">Webové aplikace jsou nasazeny jako knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="33762-119">Web applications are deployed as class libraries.</span></span>  
  
## <a name="declaring-the-main-procedure"></a><span data-ttu-id="33762-120">Deklarace hlavní procedura</span><span class="sxs-lookup"><span data-stu-id="33762-120">Declaring the Main Procedure</span></span>  
 <span data-ttu-id="33762-121">Existují čtyři způsoby deklarovat `Main` postupu.</span><span class="sxs-lookup"><span data-stu-id="33762-121">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="33762-122">Argumenty může trvat nebo Ne, a můžete vrátit hodnotu, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="33762-122">It can take arguments or not, and it can return a value or not.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33762-123">Pokud je deklarovat `Main` v třídě, je nutné použít `Shared` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="33762-123">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="33762-124">V modulu `Main` nemusí být `Shared`.</span><span class="sxs-lookup"><span data-stu-id="33762-124">In a module, `Main` does not need to be `Shared`.</span></span>  
  
-   <span data-ttu-id="33762-125">Nejjednodušší způsob je deklarovat `Sub` procedury, která nemá trvat argumenty nebo vrátit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="33762-125">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   <span data-ttu-id="33762-126">`Main`Můžete se taky vrátit `Integer` hodnotu, kterou používá operační systém jako ukončovací kód k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="33762-126">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="33762-127">Další programy můžete otestovat tento kód tak, že prověří hodnotu Windows.</span><span class="sxs-lookup"><span data-stu-id="33762-127">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="33762-128">Pokud chcete vrátit ukončovací kód, je potřeba deklarovat `Main` jako `Function` postup místo `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="33762-128">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>  
  
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
  
-   <span data-ttu-id="33762-129">`Main`Můžete taky využít `String` pole jako argument.</span><span class="sxs-lookup"><span data-stu-id="33762-129">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="33762-130">Každý řetězec v poli, obsahuje jeden z argumentů příkazového řádku, použije k vyvolání vašeho programu.</span><span class="sxs-lookup"><span data-stu-id="33762-130">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="33762-131">Můžete využít různé akce v závislosti na jejich hodnot.</span><span class="sxs-lookup"><span data-stu-id="33762-131">You can take different actions depending on their values.</span></span>  
  
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
  
-   <span data-ttu-id="33762-132">Je možné deklarovat `Main` Zkontrolujte argumenty příkazového řádku, ale není vrátí ukončovací kód, následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="33762-132">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="33762-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="33762-133">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
 <xref:System.Array.Length%2A>  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [<span data-ttu-id="33762-134">Struktura programu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="33762-134">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [<span data-ttu-id="33762-135">/main</span><span class="sxs-lookup"><span data-stu-id="33762-135">/main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)  
 [<span data-ttu-id="33762-136">Shared</span><span class="sxs-lookup"><span data-stu-id="33762-136">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="33762-137">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="33762-137">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="33762-138">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="33762-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="33762-139">Datový typ Integer</span><span class="sxs-lookup"><span data-stu-id="33762-139">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="33762-140">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="33762-140">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
