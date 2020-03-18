---
title: 'Postup: Určení, zda je soubor sestavením'
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1d66c0c166724f195a3cafd9bcbe3c7414c08ebb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159504"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a>Postup: Určení, zda je soubor sestavením

Soubor je sestavení, pokud a pouze v případě, že je spravován a obsahuje položku sestavení v jeho metadata. Další informace o sestaveních a metadatech naleznete v [tématu Manifest sestavení](manifest.md).  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Ruční určení, zda je soubor sestavením  
  
1. Spusťte [ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).  
  
2. Načtěte soubor, který chcete otestovat.  
  
3. Pokud **ILDASM** hlásí, že soubor není přenosný spustitelný soubor (PE), pak není sestavení. Další informace naleznete v tématu [Jak: Zobrazit obsah sestavení](view-contents.md).  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Jak programově určit, zda je soubor sestavení  
  
1. Volání <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> metody, předání úplnou cestu k souboru a název souboru, který testujete.  
  
2. Pokud <xref:System.BadImageFormatException> je vyvolána výjimka, soubor není sestavení.  
  
## <a name="example"></a>Příklad  
Tento příklad testuje dll, aby zjistil, zda se jedná o sestavení.  

```csharp
class TestAssembly  
{  
    static void Main()  
    {  
  
        try  
        {  
            System.Reflection.AssemblyName testAssembly =  
                System.Reflection.AssemblyName.GetAssemblyName(@"C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll");  
  
            System.Console.WriteLine("Yes, the file is an assembly.");  
        }  
  
        catch (System.IO.FileNotFoundException)  
        {  
            System.Console.WriteLine("The file cannot be found.");  
        }  
  
        catch (System.BadImageFormatException)  
        {  
            System.Console.WriteLine("The file is not an assembly.");  
        }  
  
        catch (System.IO.FileLoadException)  
        {  
            System.Console.WriteLine("The assembly has already been loaded.");  
        }  
    }  
}  
/* Output (with .NET Framework 3.5 installed):  
    Yes, the file is an assembly.  
*/  
```  

```vb  
Module Module1  
    Sub Main()  
        Try  
            Dim testAssembly As Reflection.AssemblyName =  
                                Reflection.AssemblyName.GetAssemblyName("C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll")  
            Console.WriteLine("Yes, the file is an Assembly.")  
        Catch ex As System.IO.FileNotFoundException  
            Console.WriteLine("The file cannot be found.")  
        Catch ex As System.BadImageFormatException  
            Console.WriteLine("The file is not an Assembly.")  
        Catch ex As System.IO.FileLoadException  
            Console.WriteLine("The Assembly has already been loaded.")  
        End Try  
        Console.ReadLine()  
    End Sub  
End Module  
' Output (with .NET Framework 3.5 installed):  
'        Yes, the file is an Assembly.  
```

Metoda <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> načte testovací soubor a poté jej uvolní po přečtení informací.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Reflection.AssemblyName>
- [Průvodce programováním v C#](../../csharp/programming-guide/index.md)
- [Koncepty programování (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Sestavení v .NET](index.md)
