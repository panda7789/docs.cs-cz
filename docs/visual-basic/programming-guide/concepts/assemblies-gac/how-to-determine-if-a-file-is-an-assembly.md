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
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a><span data-ttu-id="92b48-102">Postupy: určení, zda je soubor sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92b48-102">How to: Determine If a File Is an Assembly (Visual Basic)</span></span>
<span data-ttu-id="92b48-103">Pokud je spravovaný a obsahuje položku sestavení ve svých metadatech, je soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="92b48-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="92b48-104">Další informace o sestavení a metadata, naleznete v tématu [Manifest sestavení](../../../../framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="92b48-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](../../../../framework/app-domains/assembly-manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="92b48-105">Jak ručně určit, zda je soubor sestavení</span><span class="sxs-lookup"><span data-stu-id="92b48-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="92b48-106">Spuštění [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).</span><span class="sxs-lookup"><span data-stu-id="92b48-106">Start the [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).</span></span>  
  
2.  <span data-ttu-id="92b48-107">Načtěte soubor, který chcete otestovat.</span><span class="sxs-lookup"><span data-stu-id="92b48-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="92b48-108">Pokud **ILDASM** sestavy, zda soubor není souborem přenosné spustitelný soubor (PE), a není sestavení.</span><span class="sxs-lookup"><span data-stu-id="92b48-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="92b48-109">Další informace naleznete v tématu [postupy: zobrazení obsahu sestavení](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span><span class="sxs-lookup"><span data-stu-id="92b48-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="92b48-110">Jak programově určit, zda je soubor sestavení</span><span class="sxs-lookup"><span data-stu-id="92b48-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="92b48-111">Volání <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> metodu předáním úplná cesta a název souboru jsou testování.</span><span class="sxs-lookup"><span data-stu-id="92b48-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="92b48-112">Pokud <xref:System.BadImageFormatException> je vyvolána výjimka, soubor není sestavení.</span><span class="sxs-lookup"><span data-stu-id="92b48-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92b48-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="92b48-113">Example</span></span>  
 <span data-ttu-id="92b48-114">Tento příklad testy, zkontrolujte, jestli je sestavení knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="92b48-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
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
  
 <span data-ttu-id="92b48-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Metoda načte testovací soubor a pak uvolní po informace je pro čtení.</span><span class="sxs-lookup"><span data-stu-id="92b48-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b48-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="92b48-116">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 [<span data-ttu-id="92b48-117">Koncepty programování</span><span class="sxs-lookup"><span data-stu-id="92b48-117">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="92b48-118">Sestavení a globální mezipaměti sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92b48-118">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](index.md)
