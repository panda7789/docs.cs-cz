---
title: Lc.exe (kompilátor licencí)
ms.date: 03/30/2017
helpviewer_keywords:
- Lc.exe
- .licx file
- License Compiler
- control licenses [Windows Forms]
- compiling licenses file
- license file
- .licenses file
- Windows Forms, control licenses
- licensed controls [Windows Forms]
ms.assetid: 2de803b8-495e-4982-b209-19a72aba0460
ms.openlocfilehash: 464514a241cc35fc821049ba0c29bec108d88253
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180400"
---
# <a name="lcexe-license-compiler"></a><span data-ttu-id="6bae9-102">Lc.exe (kompilátor licencí)</span><span class="sxs-lookup"><span data-stu-id="6bae9-102">Lc.exe (License Compiler)</span></span>
<span data-ttu-id="6bae9-103">License Compiler čte textové soubory, které obsahují licenční informace a vytváří binární soubor, který může být integrován jako prostředek do spustitelného souboru modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="6bae9-103">The License Compiler reads text files that contain licensing information and produces a binary file that can be embedded in a common language runtime executable as a resource.</span></span>  
  
 <span data-ttu-id="6bae9-104">Textový soubor .licx se automaticky vygeneruje nebo aktualizuje prostřednictvím Návrháře formulářů Windows pokaždé, když je do formuláře přidán licencovaný ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="6bae9-104">A .licx text file is automatically generated or updated by the Windows Forms Designer whenever a licensed control is added to the form.</span></span> <span data-ttu-id="6bae9-105">Jako část kompilace bude systém projektu transformovat textový soubor .licx na binární prostředek .licenses, který podporuje licencování ovládacích prvků .NET.</span><span class="sxs-lookup"><span data-stu-id="6bae9-105">As part of compilation, the project system will transform the .licx text file into a .licenses binary resource that provides support for .NET control licensing.</span></span> <span data-ttu-id="6bae9-106">Binární prostředek bude poté vložen do výstupu projektu.</span><span class="sxs-lookup"><span data-stu-id="6bae9-106">The binary resource will then be embedded in the project output.</span></span>  
  
 <span data-ttu-id="6bae9-107">Křížová kompilace mezi 32 bity a 64 bity není podporována, jestliže při sestavování projektu použijete License Compiler.</span><span class="sxs-lookup"><span data-stu-id="6bae9-107">Cross compilation between 32-bit and 64-bit is not supported when you use the License Compiler when building your project.</span></span> <span data-ttu-id="6bae9-108">Důvodem je, že License Compiler musí načíst sestavení, přičemž načítání 64bitových sestavení z 32bitové aplikace není povoleno a naopak.</span><span class="sxs-lookup"><span data-stu-id="6bae9-108">This is because the License Compiler has to load assemblies, and loading 64-bit assemblies from a 32-bit application is not allowed, and vice versa.</span></span> <span data-ttu-id="6bae9-109">V tomto případě použijte License Compiler z příkazového řádku k ruční kompilaci licence a zadejte odpovídající architekturu.</span><span class="sxs-lookup"><span data-stu-id="6bae9-109">In this case, use the License Compiler from the command line to compile the license manually, and specify the corresponding architecture.</span></span>  
  
 <span data-ttu-id="6bae9-110">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6bae9-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="6bae9-111">Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="6bae9-111">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="6bae9-112">Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="6bae9-112">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="6bae9-113">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="6bae9-113">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bae9-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bae9-114">Syntax</span></span>  
  
```console
      lc /target:  
targetPE /complist:filename [-outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|<span data-ttu-id="6bae9-115">Možnost</span><span class="sxs-lookup"><span data-stu-id="6bae9-115">Option</span></span>|<span data-ttu-id="6bae9-116">Popis</span><span class="sxs-lookup"><span data-stu-id="6bae9-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6bae9-117">**/complist:** *název souboru*</span><span class="sxs-lookup"><span data-stu-id="6bae9-117">**/complist:** *filename*</span></span>|<span data-ttu-id="6bae9-118">Určuje název souboru, který obsahuje seznam licencovaných součástí, jež chcete zahrnout do souboru .licenses.</span><span class="sxs-lookup"><span data-stu-id="6bae9-118">Specifies the name of a file that contains the list of licensed components to include in the .licenses file.</span></span> <span data-ttu-id="6bae9-119">Jednotlivé komponenty se odkazují pomocí úplného názvu, vždy pouze jedna komponenta na řádek.</span><span class="sxs-lookup"><span data-stu-id="6bae9-119">Each component is referenced using its full name with only one component per line.</span></span><br /><br /> <span data-ttu-id="6bae9-120">Uživatelé příkazového řádku mohou určit samostatný soubor pro každý formulář v projektu.</span><span class="sxs-lookup"><span data-stu-id="6bae9-120">Command-line users can specify a separate file for each form in the project.</span></span> <span data-ttu-id="6bae9-121">Lc.exe akceptuje více vstupních souborů a vytváří jeden soubor .licenses.</span><span class="sxs-lookup"><span data-stu-id="6bae9-121">Lc.exe accepts multiple input files and produces a single .licenses file.</span></span>|  
|<span data-ttu-id="6bae9-122">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="6bae9-122">**/h**[**elp**]</span></span>|<span data-ttu-id="6bae9-123">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="6bae9-123">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="6bae9-124">**/i:** *modul*</span><span class="sxs-lookup"><span data-stu-id="6bae9-124">**/i:** *module*</span></span>|<span data-ttu-id="6bae9-125">Určuje moduly, které obsahují součásti uvedené v souboru **/complist.**</span><span class="sxs-lookup"><span data-stu-id="6bae9-125">Specifies the modules that contain the components listed in the **/complist** file.</span></span> <span data-ttu-id="6bae9-126">Chcete-li zadat více než jeden modul, použijte více příznaků **/i.**</span><span class="sxs-lookup"><span data-stu-id="6bae9-126">To specify more than one module, use multiple **/i** flags.</span></span>|  
|<span data-ttu-id="6bae9-127">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="6bae9-127">**/nologo**</span></span>|<span data-ttu-id="6bae9-128">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6bae9-128">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="6bae9-129">**/outdir:** *cesta*</span><span class="sxs-lookup"><span data-stu-id="6bae9-129">**/outdir:** *path*</span></span>|<span data-ttu-id="6bae9-130">Určuje adresář, do kterého má být umístěn výstupní soubor .licenses.</span><span class="sxs-lookup"><span data-stu-id="6bae9-130">Specifies the directory in which to place the output .licenses file.</span></span>|  
|<span data-ttu-id="6bae9-131">**/cíl:** *targetPE*</span><span class="sxs-lookup"><span data-stu-id="6bae9-131">**/target:** *targetPE*</span></span>|<span data-ttu-id="6bae9-132">Určuje spustitelný soubor, pro který je generován soubor .licenses.</span><span class="sxs-lookup"><span data-stu-id="6bae9-132">Specifies the executable for which the .licenses file is being generated.</span></span>|  
|<span data-ttu-id="6bae9-133">**/v**</span><span class="sxs-lookup"><span data-stu-id="6bae9-133">**/v**</span></span>|<span data-ttu-id="6bae9-134">Určuje režim podrobného vypisování; zobrazuje informace o průběhu kompilace.</span><span class="sxs-lookup"><span data-stu-id="6bae9-134">Specifies verbose mode; displays compilation progress information.</span></span>|  
|<span data-ttu-id="6bae9-135">\**@\*\*\*soubor*</span><span class="sxs-lookup"><span data-stu-id="6bae9-135">**@** *file*</span></span>|<span data-ttu-id="6bae9-136">Určuje soubor odpovědi (.rsp).</span><span class="sxs-lookup"><span data-stu-id="6bae9-136">Specifies the response (.rsp) file.</span></span>|  
|<span data-ttu-id="6bae9-137">**/?**</span><span class="sxs-lookup"><span data-stu-id="6bae9-137">**/?**</span></span>|<span data-ttu-id="6bae9-138">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="6bae9-138">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6bae9-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="6bae9-139">Example</span></span>  
  
1. <span data-ttu-id="6bae9-140">Pokud používáte licencovaný `MyCompany.Samples.LicControl1` ovládací prvek `Samples.DLL` obsažený v `HostApp.exe`aplikaci `HostAppLic.txt` s názvem *,* můžete vytvořit následující.</span><span class="sxs-lookup"><span data-stu-id="6bae9-140">If you are using a licensed control `MyCompany.Samples.LicControl1` contained in `Samples.DLL` in an application called `HostApp.exe`*,* you can create `HostAppLic.txt` that contains the following.</span></span>  
  
    ```text
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2. <span data-ttu-id="6bae9-141">Vytvořte soubor .licenses s názvem `HostApp.exe.licenses` pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="6bae9-141">Create the .licenses file called `HostApp.exe.licenses` using the following command.</span></span>  
  
    ```console  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3. <span data-ttu-id="6bae9-142">Sestavení `HostApp.exe` včetně souboru .licenses jako prostředku.</span><span class="sxs-lookup"><span data-stu-id="6bae9-142">Build `HostApp.exe` including the .licenses file as a resource.</span></span> <span data-ttu-id="6bae9-143">Pokud vytváříte aplikace C#, měli byste k sestavení aplikace použít následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="6bae9-143">If you were building a C# application you would use the following command to build your application.</span></span>  
  
    ```console
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 <span data-ttu-id="6bae9-144">Následující příkaz se `myApp.licenses` zkompiluje ze `hostapplic.txt`seznamů licencovaných součástí určených v položkách , `hostapplic2.txt` a `hostapplic3.txt`.</span><span class="sxs-lookup"><span data-stu-id="6bae9-144">The following command compiles `myApp.licenses` from the lists of licensed components specified by `hostapplic.txt`, `hostapplic2.txt` and `hostapplic3.txt`.</span></span> <span data-ttu-id="6bae9-145">Argument `modulesList` určuje moduly, které obsahují licencované součásti.</span><span class="sxs-lookup"><span data-stu-id="6bae9-145">The `modulesList` argument specifies the modules that contain the licensed components.</span></span>  
  
```console  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a><span data-ttu-id="6bae9-146">Příklad souboru odpovědi</span><span class="sxs-lookup"><span data-stu-id="6bae9-146">Response File Example</span></span>  
 <span data-ttu-id="6bae9-147">Následující výpis ukazuje příklad souboru `response.rsp`odpovědí .</span><span class="sxs-lookup"><span data-stu-id="6bae9-147">The following listing shows an example of a response file, `response.rsp`.</span></span> <span data-ttu-id="6bae9-148">Další informace o souborech odpovědí naleznete v [tématu Response Files](/visualstudio/msbuild/msbuild-response-files).</span><span class="sxs-lookup"><span data-stu-id="6bae9-148">For more information on response files, see [Response Files](/visualstudio/msbuild/msbuild-response-files).</span></span>  
  
```text  
/target:hostapp.exe  
/complist:hostapplic.txt
/i:WFCPrj.dll
/outdir:"C:\My Folder"  
```  
  
 <span data-ttu-id="6bae9-149">Soubor používá následující `response.rsp` příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="6bae9-149">The following command line uses the `response.rsp` file.</span></span>  
  
```console  
lc @response.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="6bae9-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bae9-150">See also</span></span>

- [<span data-ttu-id="6bae9-151">Nástroje</span><span class="sxs-lookup"><span data-stu-id="6bae9-151">Tools</span></span>](index.md)
- [<span data-ttu-id="6bae9-152">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="6bae9-152">Al.exe (Assembly Linker)</span></span>](al-exe-assembly-linker.md)
- [<span data-ttu-id="6bae9-153">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="6bae9-153">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
