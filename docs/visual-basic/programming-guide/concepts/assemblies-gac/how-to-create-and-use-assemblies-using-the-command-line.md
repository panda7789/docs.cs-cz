---
title: 'Postupy: vytvoření a použití sestavení s pomocí příkazového řádku (Visual Basic)'
ms.date: 03/14/2018
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c02f694da4e03b666fa88ea6db8ddb2db4c9637d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643286"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a>Postupy: vytvoření a použití sestavení s pomocí příkazového řádku (Visual Basic)
Sestavení nebo dynamického propojení knihovna (DLL), je propojen s vaším programem za běhu. Chcete-li ukazují, vytvoření a použití knihovny DLL, zvažte následující scénáře:  
  
-   `MathLibrary.DLL`: Knihovna soubor, který obsahuje metody, která se má volat za běhu. V tomto příkladu knihovnu DLL obsahuje dvě metody, `Add` a `Multiply`.  
  
-   `Add`: Zdrojový soubor, který obsahuje metodu `Add`. Vrátí součet její parametry. Třída `AddClass` obsahující metodu `Add` je členem oboru názvů `UtilityMethods`.  
  
-   `Mult`: Zdrojový kód, který obsahuje metodu `Multiply`. Vrátí součin jeho parametry. Třída `MultiplyClass` obsahující metodu `Multiply` je také členem oboru názvů `UtilityMethods`.  
  
-   `TestCode`: Soubor, který obsahuje `Main` metoda. Metody v souboru DLL používá k výpočtu součet a produktu argumenty běhu.  
  
## <a name="example"></a>Příklad  
  
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
  
 Tento soubor obsahuje algoritmus, který používá metody DLL `Add` a `Multiply`. Začíná Analýza argumentů zadali z příkazového řádku, `num1` a `num2`. Pak se vypočítává součet `Add` metoda na `AddClass` třídy a produktu pomocí `Multiply` metoda na `MultiplyClass` – třída.  
  
 Všimněte si, že `Imports` příkaz na začátku souboru umožňuje používat třídu nekvalifikované názvy tak, aby odkazovaly metody DLL při kompilaci, následujícím způsobem:  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 Jinak budete muset použít plně kvalifikované názvy následujícím způsobem:  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a>Spuštění  
 Chcete-li spustit program, zadejte název souboru EXE, za nímž následuje dvou čísel, následujícím způsobem:  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 K vytvoření souboru `MathLibrary.DLL`, zkompilovat dva soubory `Add` a `Mult` pomocí následující příkazový řádek.  
  
```console  
vbc -target:library -out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 [-Target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) – možnost kompilátoru říká kompilátoru výstup knihovny DLL místo soubor EXE. [-Out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) – možnost kompilátoru a potom podle názvu souboru se používá k určení názvu souboru DLL. Jinak, kompilátor použije první soubor (`Add.vb`) jako název knihovnu DLL.  
  
 K vytvoření spustitelný soubor `TestCode.exe`, použijte následující příkazový řádek:  
  
```console  
vbc -out:TestCode.exe -reference:MathLibrary.DLL TestCode.vb  
```  
  
 **-Out** – možnost kompilátoru říká kompilátoru do výstupního souboru EXE a určuje název souboru výstupního souboru (`TestCode.exe`). Tato možnost kompilátoru je volitelné. [– Referenční dokumentace (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) – možnost kompilátoru Určuje soubor knihovny DLL nebo soubory, které tento program používá.  
  
 Další informace o sestavení z příkazového řádku najdete v tématu a [sestavení z příkazového řádku](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
## <a name="see-also"></a>Viz také  
 [Koncepty programování](../../../../visual-basic/programming-guide/concepts/index.md)  
 [Sestavení a globální mezipaměti sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Vytvoření třídy k umístění funkcí DLL](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
