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
ms.openlocfilehash: 17ab7317ff1147dc79fae4ef3068cd9bc2143907
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774208"
---
# <a name="lcexe-license-compiler"></a><span data-ttu-id="a9c4d-102">Lc.exe (kompilátor licencí)</span><span class="sxs-lookup"><span data-stu-id="a9c4d-102">Lc.exe (License Compiler)</span></span>
<span data-ttu-id="a9c4d-103">License Compiler čte textové soubory, které obsahují licenční informace a vytváří binární soubor, který může být integrován jako prostředek do spustitelného souboru modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="a9c4d-103">The License Compiler reads text files that contain licensing information and produces a binary file that can be embedded in a common language runtime executable as a resource.</span></span>  
  
 <span data-ttu-id="a9c4d-104">Textový soubor .licx se automaticky vygeneruje nebo aktualizuje prostřednictvím Návrháře formulářů Windows pokaždé, když je do formuláře přidán licencovaný ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-104">A .licx text file is automatically generated or updated by the Windows Forms Designer whenever a licensed control is added to the form.</span></span> <span data-ttu-id="a9c4d-105">Jako část kompilace bude systém projektu transformovat textový soubor .licx na binární prostředek .licenses, který podporuje licencování ovládacích prvků .NET.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-105">As part of compilation, the project system will transform the .licx text file into a .licenses binary resource that provides support for .NET control licensing.</span></span> <span data-ttu-id="a9c4d-106">Binární prostředek bude poté vložen do výstupu projektu.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-106">The binary resource will then be embedded in the project output.</span></span>  
  
 <span data-ttu-id="a9c4d-107">Křížová kompilace mezi 32 bity a 64 bity není podporována, jestliže při sestavování projektu použijete License Compiler.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-107">Cross compilation between 32-bit and 64-bit is not supported when you use the License Compiler when building your project.</span></span> <span data-ttu-id="a9c4d-108">Důvodem je, že License Compiler musí načíst sestavení, přičemž načítání 64bitových sestavení z 32bitové aplikace není povoleno a naopak.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-108">This is because the License Compiler has to load assemblies, and loading 64-bit assemblies from a 32-bit application is not allowed, and vice versa.</span></span> <span data-ttu-id="a9c4d-109">V tomto případě použijte License Compiler z příkazového řádku k ruční kompilaci licence a zadejte odpovídající architekturu.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-109">In this case, use the License Compiler from the command line to compile the license manually, and specify the corresponding architecture.</span></span>  
  
 <span data-ttu-id="a9c4d-110">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="a9c4d-111">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="a9c4d-111">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="a9c4d-112">Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="a9c4d-112">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="a9c4d-113">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="a9c4d-113">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9c4d-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9c4d-114">Syntax</span></span>  
  
```console
      lc /target:  
targetPE /complist:filename [-outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|<span data-ttu-id="a9c4d-115">Možnost</span><span class="sxs-lookup"><span data-stu-id="a9c4d-115">Option</span></span>|<span data-ttu-id="a9c4d-116">Popis</span><span class="sxs-lookup"><span data-stu-id="a9c4d-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a9c4d-117">**/complist:** *název souboru*</span><span class="sxs-lookup"><span data-stu-id="a9c4d-117">**/complist:** *filename*</span></span>|<span data-ttu-id="a9c4d-118">Určuje název souboru, který obsahuje seznam licencovaných součástí, jež chcete zahrnout do souboru .licenses.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-118">Specifies the name of a file that contains the list of licensed components to include in the .licenses file.</span></span> <span data-ttu-id="a9c4d-119">Jednotlivé komponenty se odkazují pomocí úplného názvu, vždy pouze jedna komponenta na řádek.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-119">Each component is referenced using its full name with only one component per line.</span></span><br /><br /> <span data-ttu-id="a9c4d-120">Uživatelé příkazového řádku mohou určit samostatný soubor pro každý formulář v projektu.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-120">Command-line users can specify a separate file for each form in the project.</span></span> <span data-ttu-id="a9c4d-121">Lc.exe akceptuje více vstupních souborů a vytváří jeden soubor .licenses.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-121">Lc.exe accepts multiple input files and produces a single .licenses file.</span></span>|  
|<span data-ttu-id="a9c4d-122">**/h**[**ELP**]</span><span class="sxs-lookup"><span data-stu-id="a9c4d-122">**/h**[**elp**]</span></span>|<span data-ttu-id="a9c4d-123">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-123">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="a9c4d-124">**/i:** *modul*</span><span class="sxs-lookup"><span data-stu-id="a9c4d-124">**/i:** *module*</span></span>|<span data-ttu-id="a9c4d-125">Určuje moduly, které obsahují součásti uvedené v souboru **/complist** .</span><span class="sxs-lookup"><span data-stu-id="a9c4d-125">Specifies the modules that contain the components listed in the **/complist** file.</span></span> <span data-ttu-id="a9c4d-126">Pokud chcete zadat víc než jeden modul, použijte několik příznaků **/i** .</span><span class="sxs-lookup"><span data-stu-id="a9c4d-126">To specify more than one module, use multiple **/i** flags.</span></span>|  
|<span data-ttu-id="a9c4d-127">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="a9c4d-127">**/nologo**</span></span>|<span data-ttu-id="a9c4d-128">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-128">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="a9c4d-129">**/OutDir:** *cesta*</span><span class="sxs-lookup"><span data-stu-id="a9c4d-129">**/outdir:** *path*</span></span>|<span data-ttu-id="a9c4d-130">Určuje adresář, do kterého má být umístěn výstupní soubor .licenses.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-130">Specifies the directory in which to place the output .licenses file.</span></span>|  
|<span data-ttu-id="a9c4d-131">**/target:** *targetPE*</span><span class="sxs-lookup"><span data-stu-id="a9c4d-131">**/target:** *targetPE*</span></span>|<span data-ttu-id="a9c4d-132">Určuje spustitelný soubor, pro který je generován soubor .licenses.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-132">Specifies the executable for which the .licenses file is being generated.</span></span>|  
|<span data-ttu-id="a9c4d-133">**/v**</span><span class="sxs-lookup"><span data-stu-id="a9c4d-133">**/v**</span></span>|<span data-ttu-id="a9c4d-134">Určuje režim podrobného vypisování; zobrazuje informace o průběhu kompilace.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-134">Specifies verbose mode; displays compilation progress information.</span></span>|  
|<span data-ttu-id="a9c4d-135">*soubor* @</span><span class="sxs-lookup"><span data-stu-id="a9c4d-135">**@** *file*</span></span>|<span data-ttu-id="a9c4d-136">Určuje soubor odpovědi (. rsp).</span><span class="sxs-lookup"><span data-stu-id="a9c4d-136">Specifies the response (.rsp) file.</span></span>|  
|<span data-ttu-id="a9c4d-137">**/?**</span><span class="sxs-lookup"><span data-stu-id="a9c4d-137">**/?**</span></span>|<span data-ttu-id="a9c4d-138">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-138">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a9c4d-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9c4d-139">Example</span></span>  
  
1. <span data-ttu-id="a9c4d-140">Pokud používáte licencovaný ovládací prvek `MyCompany.Samples.LicControl1` obsažený v `Samples.DLL` v aplikaci s názvem `HostApp.exe` *,* můžete vytvořit `HostAppLic.txt`, který obsahuje následující.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-140">If you are using a licensed control `MyCompany.Samples.LicControl1` contained in `Samples.DLL` in an application called `HostApp.exe`*,* you can create `HostAppLic.txt` that contains the following.</span></span>  
  
    ```text
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2. <span data-ttu-id="a9c4d-141">Pomocí následujícího příkazu vytvořte soubor. licenses s názvem `HostApp.exe.licenses`.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-141">Create the .licenses file called `HostApp.exe.licenses` using the following command.</span></span>  
  
    ```console  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3. <span data-ttu-id="a9c4d-142">Sestavte `HostApp.exe` včetně souboru. licenses jako prostředku.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-142">Build `HostApp.exe` including the .licenses file as a resource.</span></span> <span data-ttu-id="a9c4d-143">Pokud vytváříte aplikace C#, měli byste k sestavení aplikace použít následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-143">If you were building a C# application you would use the following command to build your application.</span></span>  
  
    ```console
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 <span data-ttu-id="a9c4d-144">Následující příkaz zkompiluje `myApp.licenses` ze seznamu licencovaných komponent určených `hostapplic.txt`, `hostapplic2.txt` a `hostapplic3.txt`.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-144">The following command compiles `myApp.licenses` from the lists of licensed components specified by `hostapplic.txt`, `hostapplic2.txt` and `hostapplic3.txt`.</span></span> <span data-ttu-id="a9c4d-145">Argument `modulesList` Určuje moduly, které obsahují licencované součásti.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-145">The `modulesList` argument specifies the modules that contain the licensed components.</span></span>  
  
```console  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a><span data-ttu-id="a9c4d-146">Příklad souboru odezvy</span><span class="sxs-lookup"><span data-stu-id="a9c4d-146">Response File Example</span></span>  
 <span data-ttu-id="a9c4d-147">Následující výpis ukazuje příklad souboru odpovědi `response.rsp`.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-147">The following listing shows an example of a response file, `response.rsp`.</span></span> <span data-ttu-id="a9c4d-148">Další informace o souborech odpovědí naleznete v tématu [soubory odpovědí](/visualstudio/msbuild/msbuild-response-files).</span><span class="sxs-lookup"><span data-stu-id="a9c4d-148">For more information on response files, see [Response Files](/visualstudio/msbuild/msbuild-response-files).</span></span>  
  
```text  
/target:hostapp.exe  
/complist:hostapplic.txt   
/i:WFCPrj.dll   
/outdir:"C:\My Folder"  
```  
  
 <span data-ttu-id="a9c4d-149">Následující příkazový řádek používá soubor `response.rsp`.</span><span class="sxs-lookup"><span data-stu-id="a9c4d-149">The following command line uses the `response.rsp` file.</span></span>  
  
```console  
lc @response.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="a9c4d-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9c4d-150">See also</span></span>

- [<span data-ttu-id="a9c4d-151">Nástroje</span><span class="sxs-lookup"><span data-stu-id="a9c4d-151">Tools</span></span>](index.md)
- [<span data-ttu-id="a9c4d-152">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="a9c4d-152">Al.exe (Assembly Linker)</span></span>](al-exe-assembly-linker.md)
- [<span data-ttu-id="a9c4d-153">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="a9c4d-153">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
