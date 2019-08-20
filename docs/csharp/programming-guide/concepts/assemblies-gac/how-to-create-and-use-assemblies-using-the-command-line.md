---
title: 'Postupy: Vytvoření a použití sestavení pomocí příkazového řádku (C#)'
ms.date: 07/20/2015
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
ms.openlocfilehash: 0a8db22a05d834d15f6e6b7f049f59f86bc1fe1d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595963"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a>Postupy: Vytvoření a použití sestavení pomocí příkazového řádku (C#)
Sestavení, nebo dynamická propojovací knihovna (DLL), jsou v době běhu propojena s vaším programem. K předvedení sestavování a používání knihoven DLL Vezměte v úvahu následující scénář:  
  
- `MathLibrary.DLL`: Soubor knihovny obsahující metody, které mají být volány v době běhu. V tomto příkladu knihovna DLL obsahuje dvě metody `Add` a. `Multiply`  
  
- `Add`: Zdrojový soubor, který obsahuje metodu `Add`. Vrátí součet svých parametrů. Třída `AddClass` , která obsahuje metodu `Add` je členem oboru názvů `UtilityMethods`.  
  
- `Mult`: Zdrojový kód, který obsahuje metodu `Multiply`. Vrátí součin jeho parametrů. Třída `MultiplyClass` , která obsahuje metodu `Multiply` , je také členem oboru názvů `UtilityMethods`.  
  
- `TestCode`: Soubor, který obsahuje `Main` metodu. Používá metody v souboru DLL k výpočtu součtu a součinu argumentů běhu.  
  
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
  
 Tento soubor obsahuje algoritmus, který používá metody knihovny DLL, `Add` a `Multiply`. Začíná analýzou argumentů zadaných z příkazového řádku `num1` a. `num2` Poté vypočítá součet `Add` pomocí metody `AddClass` ve třídě a produktu `MultiplyClass` pomocí `Multiply` metody třídy na třídu.  
  
 Všimněte si, `using` že direktiva na začátku souboru umožňuje použít nekvalifikované názvy tříd k odkazování na metody DLL v době kompilace, a to takto:  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 V opačném případě je nutné použít plně kvalifikované názvy, a to následujícím způsobem:  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a>Spuštění  
 Chcete-li spustit program, zadejte název souboru EXE následovaný dvěma čísly, a to následujícím způsobem:  
  
 `TestCode 1234 5678`  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../index.md)
- [Sestavení v .NET](../../../../standard/assembly/index.md)
- [Vytvoření třídy k umístění funkcí DLL](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
