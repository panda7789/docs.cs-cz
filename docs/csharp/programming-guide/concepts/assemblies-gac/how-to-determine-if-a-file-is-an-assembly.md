---
title: 'Postupy: určení, zda je soubor sestavení (C#)'
ms.date: 07/20/2015
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
ms.openlocfilehash: 0557f42d42e42606c3d1b2a2ad71bd797a159e8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317980"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a>Postupy: určení, zda je soubor sestavení (C#)
Pokud je spravovaný a obsahuje položku sestavení ve svých metadatech, je soubor sestavení. Další informace o sestavení a metadata, naleznete v tématu [Manifest sestavení](../../../../../docs/framework/app-domains/assembly-manifest.md).  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Jak ručně určit, zda je soubor sestavení  
  
1.  Spuštění [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).  
  
2.  Načtěte soubor, který chcete otestovat.  
  
3.  Pokud **ILDASM** sestavy, zda soubor není souborem přenosné spustitelný soubor (PE), a není sestavení. Další informace naleznete v tématu [postupy: zobrazení obsahu sestavení](../../../../framework/app-domains/how-to-view-assembly-contents.md).  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Jak programově určit, zda je soubor sestavení  
  
1.  Volání <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> metodu předáním úplná cesta a název souboru jsou testování.  
  
2.  Pokud <xref:System.BadImageFormatException> je vyvolána výjimka, soubor není sestavení.  
  
## <a name="example"></a>Příklad  
 Tento příklad testy, zkontrolujte, jestli je sestavení knihovnu DLL.  
  
```  
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
  
 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Metoda načte testovací soubor a pak uvolní po informace je pro čtení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection.AssemblyName>  
 [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)  
 [Sestavení a globální mezipaměti sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
