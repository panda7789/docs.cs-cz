---
title: 'Postupy: Určení, zda je soubor sestavení'
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: f9bff86ac559e40136ed016b862eef8ba0863ce3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973220"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a>Postupy: Určení, zda je soubor sestavení

Soubor je sestavení, pokud je a pouze v případě, že je spravován a obsahuje položku sestavení v metadatech. Další informace o sestaveních a metadatech naleznete v tématu [Assembly manifest](manifest.md).  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Ruční určení, zda je soubor sestavení  
  
1. Spusťte nástroj [Ildasm. exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).  
  
2. Načtěte soubor, který chcete testovat.  
  
3. Pokud **Ildasm** hlásí, že soubor není soubor přenositelného spustitelného souboru (PE), nejedná se o sestavení. Další informace najdete v tématu [postup: Zobrazit obsah](view-contents.md)sestavení.  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Jak programově určit, jestli je soubor sestavení  
  
1. <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> Zavolejte metodu a předejte jí úplnou cestu k souboru a název testovaného souboru.  
  
2. Pokud je vyvolána výjimka, soubor není sestavení. <xref:System.BadImageFormatException>  
  
## <a name="example"></a>Příklad  
Tento příklad testuje knihovnu DLL, aby bylo možné zjistit, zda se jedná o sestavení.  

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
 
<xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Metoda načte testovací soubor a pak ho uvolní, jakmile jsou informace čteny.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.AssemblyName>
- [C#Průvodce programováním](../../csharp/programming-guide/index.md)
- [Koncepty programování (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Sestavení v .NET](index.md)
