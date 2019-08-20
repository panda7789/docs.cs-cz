---
title: 'Postupy: Určení, zda je soubor sestavením (C#)'
ms.date: 07/20/2015
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
ms.openlocfilehash: 803159eed25a7785b1a2b4433e6950fa65e0a734
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595860"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a>Postupy: Určení, zda je soubor sestavením (C#)
Soubor je sestavení, pokud je a pouze v případě, že je spravován a obsahuje položku sestavení v metadatech. Další informace o sestaveních a metadatech naleznete v tématu [manifest sestavení](../../../../framework/app-domains/assembly-manifest.md)tématu.  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Ruční určení, zda je soubor sestavení  
  
1. Spusťte nástroj [Ildasm. exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).  
  
2. Načtěte soubor, který chcete testovat.  
  
3. Pokud **Ildasm** hlásí, že soubor není soubor přenositelného spustitelného souboru (PE), nejedná se o sestavení. Další informace najdete v tématu [postup: Zobrazit obsah](../../../../framework/app-domains/how-to-view-assembly-contents.md)sestavení.  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Jak programově určit, jestli je soubor sestavení  
  
1. <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Zavolejte metodu a předejte jí úplnou cestu k souboru a název testovaného souboru.  
  
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
  
 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Metoda načte testovací soubor a pak ho uvolní, jakmile jsou informace čteny.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.AssemblyName>
- [Průvodce programováním v jazyce C#](../../index.md)
- [Sestavení v .NET](../../../../standard/assembly/index.md)
