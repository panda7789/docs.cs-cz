---
title: 'Postupy: vytvoření a použití sestavení s pomocí příkazového řádku (C#)'
ms.date: 07/20/2015
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
ms.openlocfilehash: ef872992f17eaaeacf451fa10ef792c47445df80
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a>Postupy: vytvoření a použití sestavení s pomocí příkazového řádku (C#)
Sestavení nebo dynamického propojení knihovna (DLL), je propojen s vaším programem za běhu. Chcete-li ukazují, vytvoření a použití knihovny DLL, zvažte následující scénáře:  
  
-   `MathLibrary.DLL`: Knihovna soubor, který obsahuje metody, která se má volat za běhu. V tomto příkladu knihovnu DLL obsahuje dvě metody, `Add` a `Multiply`.  
  
-   `Add`: Zdrojový soubor, který obsahuje metodu `Add`. Vrátí součet její parametry. Třída `AddClass` obsahující metodu `Add` je členem oboru názvů `UtilityMethods`.  
  
-   `Mult`: Zdrojový kód, který obsahuje metodu `Multiply`. Vrátí součin jeho parametry. Třída `MultiplyClass` obsahující metodu `Multiply` je také členem oboru názvů `UtilityMethods`.  
  
-   `TestCode`: Soubor, který obsahuje `Main` metoda. Metody v souboru DLL používá k výpočtu součet a produktu argumenty běhu.  
  
## <a name="example"></a>Příklad  
  
```csharp  
// File: Add.cs   
namespace UtilityMethods  
{  
    public class AddClass   
    {  
        public static long Add(long i, long j)   
        {   
            return (i + j);  
        }  
    }  
}  
```  
  
```csharp  
// File: Mult.cs  
namespace UtilityMethods   
{  
    public class MultiplyClass  
    {  
        public static long Multiply(long x, long y)   
        {  
            return (x * y);   
        }  
    }  
}  
```  
  
```csharp  
// File: TestCode.cs  
  
using UtilityMethods;  
  
class TestCode  
{  
    static void Main(string[] args)   
    {  
        System.Console.WriteLine("Calling methods from MathLibrary.DLL:");  
  
        if (args.Length != 2)  
        {  
            System.Console.WriteLine("Usage: TestCode <num1> <num2>");  
            return;  
        }  
  
        long num1 = long.Parse(args[0]);  
        long num2 = long.Parse(args[1]);  
  
        long sum = AddClass.Add(num1, num2);  
        long product = MultiplyClass.Multiply(num1, num2);  
  
        System.Console.WriteLine("{0} + {1} = {2}", num1, num2, sum);  
        System.Console.WriteLine("{0} * {1} = {2}", num1, num2, product);  
    }  
}  
/* Output (assuming 1234 and 5678 are entered as command-line arguments):  
    Calling methods from MathLibrary.DLL:  
    1234 + 5678 = 6912  
    1234 * 5678 = 7006652          
*/  
```  
  
 Tento soubor obsahuje algoritmus, který používá metody DLL `Add` a `Multiply`. Začíná Analýza argumentů zadali z příkazového řádku, `num1` a `num2`. Pak se vypočítává součet `Add` metoda na `AddClass` třídy a produktu pomocí `Multiply` metoda na `MultiplyClass` – třída.  
  
 Všimněte si, že `using` – direktiva na začátku souboru umožňuje používat třídu nekvalifikované názvy tak, aby odkazovaly metody DLL při kompilaci, následujícím způsobem:  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 Jinak budete muset použít plně kvalifikované názvy následujícím způsobem:  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a>Spuštění  
 Chcete-li spustit program, zadejte název souboru EXE, za nímž následuje dvou čísel, následujícím způsobem:  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 K vytvoření souboru `MathLibrary.DLL`, zkompilovat dva soubory `Add` a `Mult` pomocí následující příkazový řádek.  
  
```csharp  
csc /target:library /out:MathLibrary.DLL Add.cs Mult.cs  
```  
  
 [/Target: library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) – možnost kompilátoru říká kompilátoru výstup knihovny DLL místo soubor EXE. [/Out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) – možnost kompilátoru a potom podle názvu souboru se používá k určení názvu souboru DLL. Jinak, kompilátor použije první soubor (`Add.cs`) jako název knihovnu DLL.  
  
 K vytvoření spustitelný soubor `TestCode.exe`, použijte následující příkazový řádek:  
  
```csharp  
csc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.cs  
```  
  
 **/Out** – možnost kompilátoru říká kompilátoru do výstupního souboru EXE a určuje název souboru výstupního souboru (`TestCode.exe`). Tato možnost kompilátoru je volitelné. [/Reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) – možnost kompilátoru Určuje soubor knihovny DLL nebo soubory, které tento program používá. Další informace najdete v tématu [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
 Další informace o sestavení z příkazového řádku najdete v tématu [vytváření pomocí příkazového řádku csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)  
 [Sestavení a globální mezipaměti sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [Vytvoření třídy k umístění funkcí DLL](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
