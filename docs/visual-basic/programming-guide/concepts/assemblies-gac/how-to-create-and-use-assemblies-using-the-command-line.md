---
title: 'Postupy: Vytvoření a použití sestavení s pomocí příkazového řádku (Visual Basic)'
ms.date: 03/14/2018
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
ms.openlocfilehash: a30d4b3ea203a8b4d3ba621fc7b0310477ddf10d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592682"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a>Postupy: Vytvoření a použití sestavení s pomocí příkazového řádku (Visual Basic)
Sestavení nebo dynamické propojení knihovny (DLL), je propojen s program za běhu. Abychom si předvedli, vytvoření a použití knihovny DLL, zvažte následující scénáře:  
  
- `MathLibrary.DLL`: Soubor knihovny, která obsahuje metody pro volaných za běhu. V tomto příkladu knihovna DLL obsahuje dvě metody, `Add` a `Multiply`.  
  
- `Add`: Zdrojový soubor, který obsahuje metodu `Add`. Vrátí součet svých parametrů. Třída `AddClass` , který obsahuje metodu `Add` patří do oboru názvů `UtilityMethods`.  
  
- `Mult`: Zdrojový kód, který obsahuje metodu `Multiply`. Vrátí součin její parametry. Třída `MultiplyClass` , který obsahuje metodu `Multiply` je také členem oboru názvů `UtilityMethods`.  
  
- `TestCode`: Soubor, který obsahuje `Main` metody. Používá metody v souboru knihovny DLL pro výpočet součtu a produktu argumenty za běhu.  
  
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
  
 Tento soubor obsahuje algoritmus, který používá knihovnu DLL metody `Add` a `Multiply`. Začíná Analýza argumentů z příkazového řádku zadané `num1` a `num2`. Pak vypočítá součet pomocí `Add` metodu `AddClass` třídy a produktu s použitím `Multiply` metodu na `MultiplyClass` třídy.  
  
 Všimněte si, že `Imports` příkaz na začátku souboru umožňuje pomocí názvů nekvalifikované tříd k odkazování knihoven DLL metody v době kompilace, následujícím způsobem:  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 V opačném případě je nutné použít plně kvalifikované názvy, následujícím způsobem:  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a>Spuštění  
 Chcete-li spustit program, zadejte název souboru EXE, za nímž následuje dvě čísla, následujícím způsobem:  
  
 `TestCode 1234 5678`  
  
## <a name="see-also"></a>Viz také:

- [Koncepty programování](../../../../visual-basic/programming-guide/concepts/index.md)
- [Sestavení v .NET](../../../../standard/assembly/index.md)
- [Vytvoření třídy k umístění funkcí DLL](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
