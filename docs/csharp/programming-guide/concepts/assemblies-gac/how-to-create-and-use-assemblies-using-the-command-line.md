---
title: 'Postupy: Vytvoření a použití sestavení s pomocí příkazového řádku (C#)'
ms.date: 07/20/2015
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
ms.openlocfilehash: 12d23816b740816bd357c3c2ac57583f31bf3cb3
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586035"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a>Postupy: Vytvoření a použití sestavení s pomocí příkazového řádku (C#)
Sestavení nebo dynamické propojení knihovny (DLL), je propojen s program za běhu. Abychom si předvedli, vytvoření a použití knihovny DLL, zvažte následující scénáře:  
  
- `MathLibrary.DLL`: Soubor knihovny, která obsahuje metody pro volaných za běhu. V tomto příkladu knihovna DLL obsahuje dvě metody, `Add` a `Multiply`.  
  
- `Add`: Zdrojový soubor, který obsahuje metodu `Add`. Vrátí součet svých parametrů. Třída `AddClass` , který obsahuje metodu `Add` patří do oboru názvů `UtilityMethods`.  
  
- `Mult`: Zdrojový kód, který obsahuje metodu `Multiply`. Vrátí součin její parametry. Třída `MultiplyClass` , který obsahuje metodu `Multiply` je také členem oboru názvů `UtilityMethods`.  
  
- `TestCode`: Soubor, který obsahuje `Main` metody. Používá metody v souboru knihovny DLL pro výpočet součtu a produktu argumenty za běhu.  
  
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
  
 Tento soubor obsahuje algoritmus, který používá knihovnu DLL metody `Add` a `Multiply`. Začíná Analýza argumentů z příkazového řádku zadané `num1` a `num2`. Pak vypočítá součet pomocí `Add` metodu `AddClass` třídy a produktu s použitím `Multiply` metodu na `MultiplyClass` třídy.  
  
 Všimněte si, že `using` – direktiva na začátku souboru umožňuje pomocí názvů nekvalifikované tříd k odkazování knihoven DLL metody v době kompilace, následujícím způsobem:  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 V opačném případě je nutné použít plně kvalifikované názvy, následujícím způsobem:  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a>Spuštění  
 Chcete-li spustit program, zadejte název souboru EXE, za nímž následuje dvě čísla, následujícím způsobem:  
  
 `TestCode 1234 5678`  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)
- [Sestavení v .NET](../../../../standard/assembly/index.md)
- [Vytvoření třídy k umístění funkcí DLL](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
