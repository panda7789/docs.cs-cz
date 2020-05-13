---
title: 'Postupy: určení, zda je soubor sestavením'
description: V tomto článku se dozvíte, jak určit, zda je soubor sestavením .NET, ručně i programově.
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: fb1bcfa50ec380f10ab67cc47331f91dc3e4b32d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380150"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="d3443-103">Postupy: určení, zda je soubor sestavením</span><span class="sxs-lookup"><span data-stu-id="d3443-103">How to: Determine if a file is an assembly</span></span>

<span data-ttu-id="d3443-104">Soubor je sestavení, pokud je a pouze v případě, že je spravován a obsahuje položku sestavení v metadatech.</span><span class="sxs-lookup"><span data-stu-id="d3443-104">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="d3443-105">Další informace o sestaveních a metadatech naleznete v tématu [Assembly manifest](manifest.md).</span><span class="sxs-lookup"><span data-stu-id="d3443-105">For more information on assemblies and metadata, see [Assembly manifest](manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="d3443-106">Ruční určení, zda je soubor sestavení</span><span class="sxs-lookup"><span data-stu-id="d3443-106">How to manually determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="d3443-107">Spusťte nástroj [Ildasm. exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="d3443-107">Start the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2. <span data-ttu-id="d3443-108">Načtěte soubor, který chcete testovat.</span><span class="sxs-lookup"><span data-stu-id="d3443-108">Load the file you want to test.</span></span>  
  
3. <span data-ttu-id="d3443-109">Pokud **Ildasm** hlásí, že soubor není soubor přenositelného spustitelného souboru (PE), nejedná se o sestavení.</span><span class="sxs-lookup"><span data-stu-id="d3443-109">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="d3443-110">Další informace naleznete v tématu [Postupy: zobrazení obsahu sestavení](view-contents.md).</span><span class="sxs-lookup"><span data-stu-id="d3443-110">For more information, see the topic [How to: View assembly contents](view-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="d3443-111">Jak programově určit, jestli je soubor sestavení</span><span class="sxs-lookup"><span data-stu-id="d3443-111">How to programmatically determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="d3443-112">Zavolejte <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> metodu a předejte jí úplnou cestu k souboru a název testovaného souboru.</span><span class="sxs-lookup"><span data-stu-id="d3443-112">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method, passing the full file path and name of the file you are testing.</span></span>  
  
2. <span data-ttu-id="d3443-113">Pokud <xref:System.BadImageFormatException> je vyvolána výjimka, soubor není sestavení.</span><span class="sxs-lookup"><span data-stu-id="d3443-113">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3443-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3443-114">Example</span></span>  
<span data-ttu-id="d3443-115">Tento příklad testuje knihovnu DLL, aby bylo možné zjistit, zda se jedná o sestavení.</span><span class="sxs-lookup"><span data-stu-id="d3443-115">This example tests a DLL to see if it is an assembly.</span></span>  

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

<span data-ttu-id="d3443-116"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A>Metoda načte testovací soubor a pak ho uvolní, jakmile jsou informace čteny.</span><span class="sxs-lookup"><span data-stu-id="d3443-116">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3443-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3443-117">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="d3443-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="d3443-118">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d3443-119">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3443-119">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="d3443-120">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="d3443-120">Assemblies in .NET</span></span>](index.md)
