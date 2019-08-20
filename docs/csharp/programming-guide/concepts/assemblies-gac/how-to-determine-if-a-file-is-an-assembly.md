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
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a><span data-ttu-id="20062-102">Postupy: Určení, zda je soubor sestavením (C#)</span><span class="sxs-lookup"><span data-stu-id="20062-102">How to: Determine If a File Is an Assembly (C#)</span></span>
<span data-ttu-id="20062-103">Soubor je sestavení, pokud je a pouze v případě, že je spravován a obsahuje položku sestavení v metadatech.</span><span class="sxs-lookup"><span data-stu-id="20062-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="20062-104">Další informace o sestaveních a metadatech naleznete v tématu [manifest sestavení](../../../../framework/app-domains/assembly-manifest.md)tématu.</span><span class="sxs-lookup"><span data-stu-id="20062-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](../../../../framework/app-domains/assembly-manifest.md).</span></span>  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="20062-105">Ruční určení, zda je soubor sestavení</span><span class="sxs-lookup"><span data-stu-id="20062-105">How to manually determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="20062-106">Spusťte nástroj [Ildasm. exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="20062-106">Start the [Ildasm.exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2. <span data-ttu-id="20062-107">Načtěte soubor, který chcete testovat.</span><span class="sxs-lookup"><span data-stu-id="20062-107">Load the file you wish to test.</span></span>  
  
3. <span data-ttu-id="20062-108">Pokud **Ildasm** hlásí, že soubor není soubor přenositelného spustitelného souboru (PE), nejedná se o sestavení.</span><span class="sxs-lookup"><span data-stu-id="20062-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="20062-109">Další informace najdete v tématu [postup: Zobrazit obsah](../../../../framework/app-domains/how-to-view-assembly-contents.md)sestavení.</span><span class="sxs-lookup"><span data-stu-id="20062-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="20062-110">Jak programově určit, jestli je soubor sestavení</span><span class="sxs-lookup"><span data-stu-id="20062-110">How to programmatically determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="20062-111"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Zavolejte metodu a předejte jí úplnou cestu k souboru a název testovaného souboru.</span><span class="sxs-lookup"><span data-stu-id="20062-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2. <span data-ttu-id="20062-112">Pokud je vyvolána výjimka, soubor není sestavení. <xref:System.BadImageFormatException></span><span class="sxs-lookup"><span data-stu-id="20062-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20062-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="20062-113">Example</span></span>  
 <span data-ttu-id="20062-114">Tento příklad testuje knihovnu DLL, aby bylo možné zjistit, zda se jedná o sestavení.</span><span class="sxs-lookup"><span data-stu-id="20062-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
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
  
 <span data-ttu-id="20062-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Metoda načte testovací soubor a pak ho uvolní, jakmile jsou informace čteny.</span><span class="sxs-lookup"><span data-stu-id="20062-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20062-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20062-116">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="20062-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="20062-117">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="20062-118">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="20062-118">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
