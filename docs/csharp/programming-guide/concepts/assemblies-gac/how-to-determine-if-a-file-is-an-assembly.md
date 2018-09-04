---
title: 'Postupy: určení, zda je soubor sestavení (C#)'
ms.date: 07/20/2015
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
ms.openlocfilehash: 51dbf2c0f37b767206d206cd86513d24c7f3c6c5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43538633"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a><span data-ttu-id="cb46b-102">Postupy: určení, zda je soubor sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="cb46b-102">How to: Determine If a File Is an Assembly (C#)</span></span>
<span data-ttu-id="cb46b-103">Pouze v případě ho spravuje a obsahuje neplatnou položku sestavení ve svých metadatech, je soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="cb46b-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="cb46b-104">Další informace o sestavení a metadata, naleznete v tématu [Manifest sestavení](../../../../../docs/framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="cb46b-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](../../../../../docs/framework/app-domains/assembly-manifest.md).</span></span>  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="cb46b-105">Jak ručně určit, zda je soubor sestavení</span><span class="sxs-lookup"><span data-stu-id="cb46b-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="cb46b-106">Spustit [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).</span><span class="sxs-lookup"><span data-stu-id="cb46b-106">Start the [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).</span></span>  
  
2.  <span data-ttu-id="cb46b-107">Načtěte soubor, který chcete testovat.</span><span class="sxs-lookup"><span data-stu-id="cb46b-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="cb46b-108">Pokud **ILDASM** sestavy, že soubor není soubor (PE portable executable) a pak se nejedná o sestavení.</span><span class="sxs-lookup"><span data-stu-id="cb46b-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="cb46b-109">Další informace naleznete v tématu [postupy: zobrazení obsahu sestavení](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span><span class="sxs-lookup"><span data-stu-id="cb46b-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="cb46b-110">Jak prostřednictvím kódu programu určit, zda je soubor sestavení</span><span class="sxs-lookup"><span data-stu-id="cb46b-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="cb46b-111">Volání <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> předejte úplnou cestu k souboru a název souboru, které testujete.</span><span class="sxs-lookup"><span data-stu-id="cb46b-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="cb46b-112">Pokud <xref:System.BadImageFormatException> je vyvolána výjimka, soubor se nejedná o sestavení.</span><span class="sxs-lookup"><span data-stu-id="cb46b-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb46b-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="cb46b-113">Example</span></span>  
 <span data-ttu-id="cb46b-114">V tomto příkladu ověřuje knihovnu DLL zjistěte, zda je sestavení.</span><span class="sxs-lookup"><span data-stu-id="cb46b-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
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
  
 <span data-ttu-id="cb46b-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Metoda načte soubor testu a pak ho uvolní po se načtou informace.</span><span class="sxs-lookup"><span data-stu-id="cb46b-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb46b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb46b-116">See Also</span></span>

- <xref:System.Reflection.AssemblyName>  
- [<span data-ttu-id="cb46b-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="cb46b-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="cb46b-118">Sestavení a globální mezipaměti sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="cb46b-118">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
