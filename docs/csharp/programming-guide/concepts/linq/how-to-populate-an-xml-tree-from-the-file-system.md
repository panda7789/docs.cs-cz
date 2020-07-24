---
title: Postup naplnění stromu XML ze systému souborů (C#)
description: Naučte se naplnit strom XML ze systému souborů v jazyce C#. Tento příklad naplní XML a pak dotazuje strom, aby vypočítal celkovou velikost všech souborů.
ms.date: 07/20/2015
ms.assetid: 2aa2ccac-4a22-47ae-9107-3bb8df232576
ms.openlocfilehash: 676261656be7d306294c9912b75edcb51a31cccc
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104756"
---
# <a name="how-to-populate-an-xml-tree-from-the-file-system-c"></a><span data-ttu-id="ac637-104">Postup naplnění stromu XML ze systému souborů (C#)</span><span class="sxs-lookup"><span data-stu-id="ac637-104">How to populate an XML tree from the file system (C#)</span></span>
<span data-ttu-id="ac637-105">Společnou a užitečnou aplikací stromů XML je úložiště dat hierarchického názvu nebo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ac637-105">A common and useful application of XML trees is as a hierarchical name/value data store.</span></span> <span data-ttu-id="ac637-106">Můžete naplnit strom XML hierarchickými daty a pak je dotazovat, transformovat a v případě potřeby ho serializovat.</span><span class="sxs-lookup"><span data-stu-id="ac637-106">You can populate an XML tree with hierarchical data, and then query it, transform it, and if necessary, serialize it.</span></span> <span data-ttu-id="ac637-107">V tomto scénáři použití nejsou důležité mnohé z sémantiky specifické pro XML, jako jsou například obory názvů a prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="ac637-107">In this usage scenario, many of the XML specific semantics, such as namespaces and white space behavior, are not important.</span></span> <span data-ttu-id="ac637-108">Místo toho můžete strom XML používat jako malou databázi, hierarchickou databázi s jedním uživatelem.</span><span class="sxs-lookup"><span data-stu-id="ac637-108">Instead, you are using the XML tree as a small, in memory, single user hierarchical database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac637-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ac637-109">Example</span></span>  
 <span data-ttu-id="ac637-110">Následující příklad naplní strom XML z místního systému souborů pomocí rekurze.</span><span class="sxs-lookup"><span data-stu-id="ac637-110">The following example populates an XML tree from the local file system using recursion.</span></span> <span data-ttu-id="ac637-111">Pak se dotazuje na strom a vypočítá celkový počet velikostí všech souborů ve stromu.</span><span class="sxs-lookup"><span data-stu-id="ac637-111">It then queries the tree, calculating the total of the sizes of all files in the tree.</span></span>  
  
```csharp  
class Program  
{  
    static XElement CreateFileSystemXmlTree(string source)  
    {  
        DirectoryInfo di = new DirectoryInfo(source);  
        return new XElement("Dir",  
            new XAttribute("Name", di.Name),  
            from d in Directory.GetDirectories(source)  
            select CreateFileSystemXmlTree(d),  
            from fi in di.GetFiles()  
            select new XElement("File",  
                new XElement("Name", fi.Name),  
                new XElement("Length", fi.Length)  
            )  
        );  
    }  
  
    static void Main(string[] args)  
    {  
        XElement fileSystemTree = CreateFileSystemXmlTree("C:/Tmp");  
        Console.WriteLine(fileSystemTree);  
        Console.WriteLine("------");  
        long totalFileSize =  
            (from f in fileSystemTree.Descendants("File")  
             select (long)f.Element("Length")).Sum();  
        Console.WriteLine("Total File Size:{0}", totalFileSize);  
    }  
}  
```  
  
 <span data-ttu-id="ac637-112">Tento příklad vytvoří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="ac637-112">This example produces output similar to the following:</span></span>  
  
```xml  
<Dir Name="Tmp">  
  <Dir Name="ConsoleApplication1">  
    <Dir Name="bin">  
      <Dir Name="Debug">  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe</Name>  
          <Length>9568</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe.manifest</Name>  
          <Length>473</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="obj">  
      <Dir Name="Debug">  
        <Dir Name="TempPE" />  
        <File>  
          <Name>ConsoleApplication1.csproj.FileListAbsolute.txt</Name>  
          <Length>322</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="Properties">  
      <File>  
        <Name>AssemblyInfo.cs</Name>  
        <Length>1454</Length>  
      </File>  
    </Dir>  
    <File>  
      <Name>ConsoleApplication1.csproj</Name>  
      <Length>2546</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.sln</Name>  
      <Length>937</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.suo</Name>  
      <Length>10752</Length>  
    </File>  
    <File>  
      <Name>Program.cs</Name>  
      <Length>269</Length>  
    </File>  
  </Dir>  
</Dir>  
------  
Total File Size:59089  
```  
