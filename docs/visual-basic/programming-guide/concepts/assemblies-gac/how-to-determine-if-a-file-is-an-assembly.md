---
title: 'Postupy: Určení, zda je soubor sestavení (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
ms.openlocfilehash: 47ac7f29509af86819006a4394ca661140b95ab0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316060"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a>Postupy: Určení, zda je soubor sestavení (Visual Basic)
Pouze v případě ho spravuje a obsahuje neplatnou položku sestavení ve svých metadatech, je soubor sestavení. Další informace o sestavení a metadata, naleznete v tématu [Manifest sestavení](../../../../framework/app-domains/assembly-manifest.md).  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Jak ručně určit, zda je soubor sestavení  
  
1. Spustit [Ildasm.exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).  
  
2. Načtěte soubor, který chcete testovat.  
  
3. Pokud **ILDASM** sestavy, že soubor není soubor (PE portable executable) a pak se nejedná o sestavení. Další informace naleznete v tématu [jak: Zobrazení obsahu sestavení](../../../../framework/app-domains/how-to-view-assembly-contents.md).  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Jak prostřednictvím kódu programu určit, zda je soubor sestavení  
  
1. Volání <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> předejte úplnou cestu k souboru a název souboru, které testujete.  
  
2. Pokud <xref:System.BadImageFormatException> je vyvolána výjimka, soubor se nejedná o sestavení.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu ověřuje knihovnu DLL zjistěte, zda je sestavení.  
  
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
  
 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Metoda načte soubor testu a pak ho uvolní po se načtou informace.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.AssemblyName>
- [Koncepty programování](../../../../visual-basic/programming-guide/concepts/index.md)
- [Sestavení a globální mezipaměti sestavení (Visual Basic)](index.md)
