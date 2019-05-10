---
title: 'Postupy: Vytvoření a použití sestavení s pomocí příkazového řádku (Visual Basic)'
ms.date: 03/14/2018
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
ms.openlocfilehash: d58109dfbb03b752f4a46f895fa1093e4f37df71
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624771"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a><span data-ttu-id="daf73-102">Postupy: Vytvoření a použití sestavení s pomocí příkazového řádku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="daf73-102">How to: Create and Use Assemblies Using the Command Line (Visual Basic)</span></span>
<span data-ttu-id="daf73-103">Sestavení nebo dynamické propojení knihovny (DLL), je propojen s program za běhu.</span><span class="sxs-lookup"><span data-stu-id="daf73-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="daf73-104">Abychom si předvedli, vytvoření a použití knihovny DLL, zvažte následující scénáře:</span><span class="sxs-lookup"><span data-stu-id="daf73-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
- <span data-ttu-id="daf73-105">`MathLibrary.DLL`: Soubor knihovny, která obsahuje metody pro volaných za běhu.</span><span class="sxs-lookup"><span data-stu-id="daf73-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="daf73-106">V tomto příkladu knihovna DLL obsahuje dvě metody, `Add` a `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="daf73-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
- <span data-ttu-id="daf73-107">`Add`: Zdrojový soubor, který obsahuje metodu `Add`.</span><span class="sxs-lookup"><span data-stu-id="daf73-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="daf73-108">Vrátí součet svých parametrů.</span><span class="sxs-lookup"><span data-stu-id="daf73-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="daf73-109">Třída `AddClass` , který obsahuje metodu `Add` patří do oboru názvů `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="daf73-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
- <span data-ttu-id="daf73-110">`Mult`: Zdrojový kód, který obsahuje metodu `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="daf73-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="daf73-111">Vrátí součin její parametry.</span><span class="sxs-lookup"><span data-stu-id="daf73-111">It returns the product of its parameters.</span></span> <span data-ttu-id="daf73-112">Třída `MultiplyClass` , který obsahuje metodu `Multiply` je také členem oboru názvů `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="daf73-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
- <span data-ttu-id="daf73-113">`TestCode`: Soubor, který obsahuje `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="daf73-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="daf73-114">Používá metody v souboru knihovny DLL pro výpočet součtu a produktu argumenty za běhu.</span><span class="sxs-lookup"><span data-stu-id="daf73-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="daf73-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="daf73-115">Example</span></span>  
  
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
  
 <span data-ttu-id="daf73-116">Tento soubor obsahuje algoritmus, který používá knihovnu DLL metody `Add` a `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="daf73-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="daf73-117">Začíná Analýza argumentů z příkazového řádku zadané `num1` a `num2`.</span><span class="sxs-lookup"><span data-stu-id="daf73-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="daf73-118">Pak vypočítá součet pomocí `Add` metodu `AddClass` třídy a produktu s použitím `Multiply` metodu na `MultiplyClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="daf73-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="daf73-119">Všimněte si, že `Imports` příkaz na začátku souboru umožňuje pomocí názvů nekvalifikované tříd k odkazování knihoven DLL metody v době kompilace, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="daf73-119">Notice that the  `Imports` statement at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 <span data-ttu-id="daf73-120">V opačném případě je nutné použít plně kvalifikované názvy, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="daf73-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a><span data-ttu-id="daf73-121">Spuštění</span><span class="sxs-lookup"><span data-stu-id="daf73-121">Execution</span></span>  
 <span data-ttu-id="daf73-122">Chcete-li spustit program, zadejte název souboru EXE, za nímž následuje dvě čísla, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="daf73-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a><span data-ttu-id="daf73-123">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="daf73-123">Compiling the Code</span></span>  
 <span data-ttu-id="daf73-124">Pro sestavení souboru `MathLibrary.DLL`, zkompilujte příslušné dva soubory `Add` a `Mult` pomocí následující příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="daf73-124">To build the file `MathLibrary.DLL`, compile the two files `Add` and `Mult` by using the following command line.</span></span>  
  
```console  
vbc -target:library -out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 <span data-ttu-id="daf73-125">[-Target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) – možnost kompilátoru instruuje kompilátor, aby výstupní knihovnu DLL místo souboru EXE.</span><span class="sxs-lookup"><span data-stu-id="daf73-125">The [-target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) compiler option tells the compiler to output a DLL instead of an EXE file.</span></span> <span data-ttu-id="daf73-126">[-Out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) – možnost kompilátoru následovaný názvem souboru se používá k určení názvu souboru knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="daf73-126">The [-out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) compiler option followed by a file name is used to specify the DLL file name.</span></span> <span data-ttu-id="daf73-127">V opačném případě kompilátor použije první soubor (`Add.vb`) jako název knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="daf73-127">Otherwise, the compiler uses the first file (`Add.vb`) as the name of the DLL.</span></span>  
  
 <span data-ttu-id="daf73-128">K sestavení spustitelného souboru `TestCode.exe`, použijte následující příkazový řádek:</span><span class="sxs-lookup"><span data-stu-id="daf73-128">To build the executable file, `TestCode.exe`, use the following command line:</span></span>  
  
```console  
vbc -out:TestCode.exe -reference:MathLibrary.DLL TestCode.vb  
```  
  
 <span data-ttu-id="daf73-129">**-Out** – možnost kompilátoru instruuje kompilátor, aby výstupní soubor EXE a určuje název výstupního souboru (`TestCode.exe`).</span><span class="sxs-lookup"><span data-stu-id="daf73-129">The **-out** compiler option tells the compiler to output an EXE file and specifies the name of the output file (`TestCode.exe`).</span></span> <span data-ttu-id="daf73-130">Tato možnost kompilátoru je volitelné.</span><span class="sxs-lookup"><span data-stu-id="daf73-130">This compiler option is optional.</span></span> <span data-ttu-id="daf73-131">[– Referenční dokumentace (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) – možnost kompilátoru Určuje soubor knihovny DLL nebo soubory, které tento program využívá.</span><span class="sxs-lookup"><span data-stu-id="daf73-131">The [-reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) compiler option specifies the DLL file or files that this program uses.</span></span>  
  
 <span data-ttu-id="daf73-132">Další informace o sestavování z příkazového řádku najdete v tématu a [sestavení z příkazového řádku](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="daf73-132">For more information about building from the command line, see  and [Building from the Command Line](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daf73-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="daf73-133">See also</span></span>

- [<span data-ttu-id="daf73-134">Koncepty programování</span><span class="sxs-lookup"><span data-stu-id="daf73-134">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="daf73-135">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="daf73-135">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
- [<span data-ttu-id="daf73-136">Vytvoření třídy k umístění funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="daf73-136">Creating a Class to Hold DLL Functions</span></span>](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
