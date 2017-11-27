---
title: "Postupy: vytvoření a použití sestavení s pomocí příkazového řádku (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 72f3e91f9fb88019f937dcd281aa14ab4e887daf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a><span data-ttu-id="ff700-102">Postupy: vytvoření a použití sestavení s pomocí příkazového řádku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff700-102">How to: Create and Use Assemblies Using the Command Line (Visual Basic)</span></span>
<span data-ttu-id="ff700-103">Sestavení nebo dynamického propojení knihovna (DLL), je propojen s vaším programem za běhu.</span><span class="sxs-lookup"><span data-stu-id="ff700-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="ff700-104">Chcete-li ukazují, vytvoření a použití knihovny DLL, zvažte následující scénáře:</span><span class="sxs-lookup"><span data-stu-id="ff700-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
-   <span data-ttu-id="ff700-105">`MathLibrary.DLL`: Knihovna soubor, který obsahuje metody, která se má volat za běhu.</span><span class="sxs-lookup"><span data-stu-id="ff700-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="ff700-106">V tomto příkladu knihovnu DLL obsahuje dvě metody, `Add` a `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="ff700-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
-   <span data-ttu-id="ff700-107">`Add`: Zdrojový soubor, který obsahuje metodu `Add`.</span><span class="sxs-lookup"><span data-stu-id="ff700-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="ff700-108">Vrátí součet její parametry.</span><span class="sxs-lookup"><span data-stu-id="ff700-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="ff700-109">Třída `AddClass` obsahující metodu `Add` je členem oboru názvů `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="ff700-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="ff700-110">`Mult`: Zdrojový kód, který obsahuje metodu `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="ff700-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="ff700-111">Vrátí součin jeho parametry.</span><span class="sxs-lookup"><span data-stu-id="ff700-111">It returns the product of its parameters.</span></span> <span data-ttu-id="ff700-112">Třída `MultiplyClass` obsahující metodu `Multiply` je také členem oboru názvů `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="ff700-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="ff700-113">`TestCode`: Soubor, který obsahuje `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="ff700-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="ff700-114">Metody v souboru DLL používá k výpočtu součet a produktu argumenty běhu.</span><span class="sxs-lookup"><span data-stu-id="ff700-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff700-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff700-115">Example</span></span>  
  
```vb  
' File: Add.vb   
Namespace UtilityMethods  
    Public Class AddClass  
        Public Shared Function Add(ByVal i As Long, ByVal j As Long) As Long  
            Return i + j  
        End Function  
    End Class  
End Namespace  
```  
  
```vb  
' File: Mult.vb  
Namespace UtilityMethods  
    Public Class MultiplyClass  
        Public Shared Function Multiply(ByVal x As Long, ByVal y As Long) As Long  
            Return x * y  
        End Function  
    End Class  
End Namespace  
```  
  
```vb  
' File: TestCode.vb  
  
Imports UtilityMethods  
  
Module Test  
  
    Sub Main(ByVal args As String())  
  
        System.Console.WriteLine("Calling methods from MathLibrary.DLL:")  
  
        If args.Length <> 2 Then  
            System.Console.WriteLine("Usage: TestCode <num1> <num2>")  
            Return  
        End If  
  
        Dim num1 As Long = Long.Parse(args(0))  
        Dim num2 As Long = Long.Parse(args(1))  
  
        Dim sum As Long = AddClass.Add(num1, num2)  
        Dim product As Long = MultiplyClass.Multiply(num1, num2)  
  
        System.Console.WriteLine("{0} + {1} = {2}", num1, num2, sum)  
        System.Console.WriteLine("{0} * {1} = {2}", num1, num2, product)  
  
    End Sub  
  
End Module  
  
' Output (assuming 1234 and 5678 are entered as command-line arguments):  
' Calling methods from MathLibrary.DLL:  
' 1234 + 5678 = 6912  
' 1234 * 5678 = 7006652  
```  
  
 <span data-ttu-id="ff700-116">Tento soubor obsahuje algoritmus, který používá metody DLL `Add` a `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="ff700-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="ff700-117">Začíná Analýza argumentů zadali z příkazového řádku, `num1` a `num2`.</span><span class="sxs-lookup"><span data-stu-id="ff700-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="ff700-118">Pak se vypočítává součet `Add` metoda na `AddClass` třídy a produktu pomocí `Multiply` metoda na `MultiplyClass` – třída.</span><span class="sxs-lookup"><span data-stu-id="ff700-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="ff700-119">Všimněte si, že `Imports` příkaz na začátku souboru umožňuje používat třídu nekvalifikované názvy tak, aby odkazovaly metody DLL při kompilaci, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ff700-119">Notice that the  `Imports` statement at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 <span data-ttu-id="ff700-120">Jinak budete muset použít plně kvalifikované názvy následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ff700-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a><span data-ttu-id="ff700-121">Spuštění</span><span class="sxs-lookup"><span data-stu-id="ff700-121">Execution</span></span>  
 <span data-ttu-id="ff700-122">Chcete-li spustit program, zadejte název souboru EXE, za nímž následuje dvou čísel, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ff700-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ff700-123">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ff700-123">Compiling the Code</span></span>  
 <span data-ttu-id="ff700-124">K vytvoření souboru `MathLibrary.DLL`, zkompilovat dva soubory `Add` a `Mult` pomocí následující příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="ff700-124">To build the file `MathLibrary.DLL`, compile the two files `Add` and `Mult` by using the following command line.</span></span>  
  
```vb  
vbc /target:library /out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 <span data-ttu-id="ff700-125">[/Target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) – možnost kompilátoru říká kompilátoru výstup knihovny DLL místo soubor EXE.</span><span class="sxs-lookup"><span data-stu-id="ff700-125">The [/target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) compiler option tells the compiler to output a DLL instead of an EXE file.</span></span> <span data-ttu-id="ff700-126">[/Out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) – možnost kompilátoru a potom podle názvu souboru se používá k určení názvu souboru DLL.</span><span class="sxs-lookup"><span data-stu-id="ff700-126">The [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) compiler option followed by a file name is used to specify the DLL file name.</span></span> <span data-ttu-id="ff700-127">Jinak, kompilátor použije první soubor (`Add.vb`) jako název knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="ff700-127">Otherwise, the compiler uses the first file (`Add.vb`) as the name of the DLL.</span></span>  
  
 <span data-ttu-id="ff700-128">K vytvoření spustitelný soubor `TestCode.exe`, použijte následující příkazový řádek:</span><span class="sxs-lookup"><span data-stu-id="ff700-128">To build the executable file, `TestCode.exe`, use the following command line:</span></span>  
  
```vb  
vbc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.vb  
```  
  
 <span data-ttu-id="ff700-129">**/Out** – možnost kompilátoru říká kompilátoru do výstupního souboru EXE a určuje název souboru výstupního souboru (`TestCode.exe`).</span><span class="sxs-lookup"><span data-stu-id="ff700-129">The **/out** compiler option tells the compiler to output an EXE file and specifies the name of the output file (`TestCode.exe`).</span></span> <span data-ttu-id="ff700-130">Tato možnost kompilátoru je volitelné.</span><span class="sxs-lookup"><span data-stu-id="ff700-130">This compiler option is optional.</span></span> <span data-ttu-id="ff700-131">[/Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) – možnost kompilátoru Určuje soubor knihovny DLL nebo soubory, které tento program používá.</span><span class="sxs-lookup"><span data-stu-id="ff700-131">The [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) compiler option specifies the DLL file or files that this program uses.</span></span>  
  
 <span data-ttu-id="ff700-132">Další informace o sestavení z příkazového řádku najdete v tématu a [sestavení z příkazového řádku](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="ff700-132">For more information about building from the command line, see  and [Building from the Command Line](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff700-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff700-133">See Also</span></span>  
 [<span data-ttu-id="ff700-134">Programování konceptů</span><span class="sxs-lookup"><span data-stu-id="ff700-134">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="ff700-135">Sestavení a globální mezipaměti sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff700-135">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="ff700-136">Vytvoření třídy k umístění funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="ff700-136">Creating a Class to Hold DLL Functions</span></span>](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
