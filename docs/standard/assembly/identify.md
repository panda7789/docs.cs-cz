---
title: 'Postupy: určení, zda je soubor sestavením'
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1d66c0c166724f195a3cafd9bcbe3c7414c08ebb
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159504"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="e3159-102">Postupy: určení, zda je soubor sestavením</span><span class="sxs-lookup"><span data-stu-id="e3159-102">How to: Determine if a file is an assembly</span></span>

<span data-ttu-id="e3159-103">Soubor je sestavení, pokud je a pouze v případě, že je spravován a obsahuje položku sestavení v metadatech.</span><span class="sxs-lookup"><span data-stu-id="e3159-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="e3159-104">Další informace o sestaveních a metadatech naleznete v tématu [Assembly manifest](manifest.md).</span><span class="sxs-lookup"><span data-stu-id="e3159-104">For more information on assemblies and metadata, see [Assembly manifest](manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="e3159-105">Ruční určení, zda je soubor sestavení</span><span class="sxs-lookup"><span data-stu-id="e3159-105">How to manually determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="e3159-106">Spusťte nástroj [Ildasm. exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="e3159-106">Start the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2. <span data-ttu-id="e3159-107">Načtěte soubor, který chcete testovat.</span><span class="sxs-lookup"><span data-stu-id="e3159-107">Load the file you want to test.</span></span>  
  
3. <span data-ttu-id="e3159-108">Pokud **Ildasm** hlásí, že soubor není soubor přenositelného spustitelného souboru (PE), nejedná se o sestavení.</span><span class="sxs-lookup"><span data-stu-id="e3159-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="e3159-109">Další informace naleznete v tématu [Postupy: zobrazení obsahu sestavení](view-contents.md).</span><span class="sxs-lookup"><span data-stu-id="e3159-109">For more information, see the topic [How to: View assembly contents](view-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="e3159-110">Jak programově určit, jestli je soubor sestavení</span><span class="sxs-lookup"><span data-stu-id="e3159-110">How to programmatically determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="e3159-111">Zavolejte metodu <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType>, předejte úplnou cestu k souboru a název testovaného souboru.</span><span class="sxs-lookup"><span data-stu-id="e3159-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method, passing the full file path and name of the file you are testing.</span></span>  
  
2. <span data-ttu-id="e3159-112">Pokud je vyvolána výjimka <xref:System.BadImageFormatException>, soubor není sestavení.</span><span class="sxs-lookup"><span data-stu-id="e3159-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3159-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3159-113">Example</span></span>  
<span data-ttu-id="e3159-114">Tento příklad testuje knihovnu DLL, aby bylo možné zjistit, zda se jedná o sestavení.</span><span class="sxs-lookup"><span data-stu-id="e3159-114">This example tests a DLL to see if it is an assembly.</span></span>  

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

<span data-ttu-id="e3159-115">Metoda <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> načte testovací soubor a pak ho uvolní, jakmile jsou informace čteny.</span><span class="sxs-lookup"><span data-stu-id="e3159-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3159-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3159-116">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="e3159-117">C#Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="e3159-117">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e3159-118">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3159-118">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="e3159-119">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="e3159-119">Assemblies in .NET</span></span>](index.md)
