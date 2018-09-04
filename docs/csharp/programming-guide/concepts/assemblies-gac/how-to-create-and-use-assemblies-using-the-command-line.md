---
title: 'Postupy: vytvoření a použití sestavení s pomocí příkazového řádku (C#)'
ms.date: 07/20/2015
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
ms.openlocfilehash: 0cb964991cdbcdb3fa528ac96a0e883a37439099
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514552"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a>Postupy: vytvoření a použití sestavení s pomocí příkazového řádku (C#)
Sestavení nebo dynamické propojení knihovny (DLL), je propojen s program za běhu. Abychom si předvedli, vytvoření a použití knihovny DLL, zvažte následující scénáře:  
  
-   `MathLibrary.DLL`: Knihovna soubor, který obsahuje metody pro volaných za běhu. V tomto příkladu knihovna DLL obsahuje dvě metody, `Add` a `Multiply`.  
  
-   `Add`: Zdrojový soubor, který obsahuje metodu `Add`. Vrátí součet svých parametrů. Třída `AddClass` , který obsahuje metodu `Add` patří do oboru názvů `UtilityMethods`.  
  
-   `Mult`: Zdrojový kód, který obsahuje metodu `Multiply`. Vrátí součin její parametry. Třída `MultiplyClass` , který obsahuje metodu `Multiply` je také členem oboru názvů `UtilityMethods`.  
  
-   `TestCode`: Soubor, který obsahuje `Main` metody. Používá metody v souboru knihovny DLL pro výpočet součtu a produktu argumenty za běhu.  
  
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
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Pro sestavení souboru `MathLibrary.DLL`, zkompilujte příslušné dva soubory `Add` a `Mult` pomocí následující příkazový řádek.  
  
```csharp  
csc /target:library /out:MathLibrary.DLL Add.cs Mult.cs  
```  
  
 [/Target: library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) – možnost kompilátoru instruuje kompilátor, aby výstupní knihovnu DLL místo souboru EXE. [/Out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) – možnost kompilátoru následovaný názvem souboru se používá k určení názvu souboru knihovny DLL. V opačném případě kompilátor použije první soubor (`Add.cs`) jako název knihovny DLL.  
  
 K sestavení spustitelného souboru `TestCode.exe`, použijte následující příkazový řádek:  
  
```csharp  
csc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.cs  
```  
  
 **/Out** – možnost kompilátoru instruuje kompilátor, aby výstupní soubor EXE a určuje název výstupního souboru (`TestCode.exe`). Tato možnost kompilátoru je volitelné. [/Reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) – možnost kompilátoru Určuje soubor knihovny DLL nebo soubory, které tento program využívá. Další informace najdete v tématu [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
 Další informace o sestavování z příkazového řádku najdete v tématu [sestavení pomocí příkazového řádku csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)  
- [Sestavení a globální mezipaměti sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
- [Vytvoření třídy k umístění funkcí DLL](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
