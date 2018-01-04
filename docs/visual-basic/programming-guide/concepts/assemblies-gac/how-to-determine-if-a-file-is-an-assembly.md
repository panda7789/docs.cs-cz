---
title: "Postupy: určení, zda je soubor sestavení (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0930b6504306efd7dfaf019e090a6d1212c65657
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a>Postupy: určení, zda je soubor sestavení (Visual Basic)
Pokud je spravovaný a obsahuje položku sestavení ve svých metadatech, je soubor sestavení. Další informace o sestavení a metadata, naleznete v tématu [Manifest sestavení](../../../../framework/app-domains/assembly-manifest.md).  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Jak ručně určit, zda je soubor sestavení  
  
1.  Spuštění [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).  
  
2.  Načtěte soubor, který chcete otestovat.  
  
3.  Pokud **ILDASM** sestavy, zda soubor není souborem přenosné spustitelný soubor (PE), a není sestavení. Další informace naleznete v tématu [postupy: zobrazení obsahu sestavení](../../../../framework/app-domains/how-to-view-assembly-contents.md).  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Jak programově určit, zda je soubor sestavení  
  
1.  Volání <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> metodu předáním úplná cesta a název souboru jsou testování.  
  
2.  Pokud <xref:System.BadImageFormatException> je vyvolána výjimka, soubor není sestavení.  
  
## <a name="example"></a>Příklad  
 Tento příklad testy, zkontrolujte, jestli je sestavení knihovnu DLL.  
  
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
  
 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Metoda načte testovací soubor a pak uvolní po informace je pro čtení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection.AssemblyName>  
 [Koncepty programování](../../../../visual-basic/programming-guide/concepts/index.md)  
 [Sestavení a globální mezipaměti sestavení (Visual Basic)](index.md)
