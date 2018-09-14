---
title: 'Postupy: určení, zda je soubor sestavení (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
ms.openlocfilehash: ced41279e7e192d6d5bed53dbce7378395b32e6d
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527548"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a><span data-ttu-id="0a2e4-102">Postupy: určení, zda je soubor sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a2e4-102">How to: Determine If a File Is an Assembly (Visual Basic)</span></span>
<span data-ttu-id="0a2e4-103">Pouze v případě ho spravuje a obsahuje neplatnou položku sestavení ve svých metadatech, je soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a2e4-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="0a2e4-104">Další informace o sestavení a metadata, naleznete v tématu [Manifest sestavení](../../../../framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="0a2e4-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](../../../../framework/app-domains/assembly-manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="0a2e4-105">Jak ručně určit, zda je soubor sestavení</span><span class="sxs-lookup"><span data-stu-id="0a2e4-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="0a2e4-106">Spustit [Ildasm.exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="0a2e4-106">Start the [Ildasm.exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2.  <span data-ttu-id="0a2e4-107">Načtěte soubor, který chcete testovat.</span><span class="sxs-lookup"><span data-stu-id="0a2e4-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="0a2e4-108">Pokud **ILDASM** sestavy, že soubor není soubor (PE portable executable) a pak se nejedná o sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a2e4-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="0a2e4-109">Další informace naleznete v tématu [postupy: zobrazení obsahu sestavení](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span><span class="sxs-lookup"><span data-stu-id="0a2e4-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="0a2e4-110">Jak prostřednictvím kódu programu určit, zda je soubor sestavení</span><span class="sxs-lookup"><span data-stu-id="0a2e4-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="0a2e4-111">Volání <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> předejte úplnou cestu k souboru a název souboru, které testujete.</span><span class="sxs-lookup"><span data-stu-id="0a2e4-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="0a2e4-112">Pokud <xref:System.BadImageFormatException> je vyvolána výjimka, soubor se nejedná o sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a2e4-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a2e4-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a2e4-113">Example</span></span>  
 <span data-ttu-id="0a2e4-114">V tomto příkladu ověřuje knihovnu DLL zjistěte, zda je sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a2e4-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
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
  
 <span data-ttu-id="0a2e4-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Metoda načte soubor testu a pak ho uvolní po se načtou informace.</span><span class="sxs-lookup"><span data-stu-id="0a2e4-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a2e4-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a2e4-116">See also</span></span>

- <xref:System.Reflection.AssemblyName>  
- [<span data-ttu-id="0a2e4-117">Koncepty programování</span><span class="sxs-lookup"><span data-stu-id="0a2e4-117">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
- [<span data-ttu-id="0a2e4-118">Sestavení a globální mezipaměti sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a2e4-118">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](index.md)
