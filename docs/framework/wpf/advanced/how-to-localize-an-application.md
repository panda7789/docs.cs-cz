---
title: Lokalizace aplikace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: dc7d8f4f56b26fffbd883e1e1d6e420026e1f94f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209679"
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="28eac-102">Postupy: lokalizace aplikace</span><span class="sxs-lookup"><span data-stu-id="28eac-102">How to: Localize an application</span></span>

<span data-ttu-id="28eac-103">V tomto kurzu se dozvíte, jak vytvořit lokalizovanou aplikaci pomocí nástroje LocBaml.</span><span class="sxs-lookup"><span data-stu-id="28eac-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28eac-104">Nástroj LocBaml není aplikací připravenou pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="28eac-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="28eac-105">Je prezentován jako ukázka, která používá některá z rozhraní API lokalizace a ukazuje, jak můžete napsat nástroj pro lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="28eac-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="28eac-106">Přehled</span><span class="sxs-lookup"><span data-stu-id="28eac-106">Overview</span></span>

<span data-ttu-id="28eac-107">Tento článek poskytuje podrobný přístup k lokalizaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="28eac-107">This article gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="28eac-108">Nejprve připravujete aplikaci tak, aby bylo možné extrahovat text, který bude přeložen.</span><span class="sxs-lookup"><span data-stu-id="28eac-108">First, you prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="28eac-109">Po překladu textu se přeložený text sloučí do nové kopie původní aplikace.</span><span class="sxs-lookup"><span data-stu-id="28eac-109">After the text is translated, you merge the translated text into a new copy of the original application.</span></span>
  
## <a name="create-a-sample-application"></a><span data-ttu-id="28eac-110">Vytvoření ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="28eac-110">Create a sample application</span></span>

<span data-ttu-id="28eac-111">V tomto kroku připravíte aplikaci k lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="28eac-111">In this step, you prepare your app for localization.</span></span> <span data-ttu-id="28eac-112">V ukázkách Windows Presentation Foundation (WPF) je dodána ukázka HelloApp, která bude použita pro příklady kódu v této diskuzi.</span><span class="sxs-lookup"><span data-stu-id="28eac-112">In the Windows Presentation Foundation (WPF) samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="28eac-113">Chcete-li použít tuto ukázku, Stáhněte soubory jazyk Extensible Application Markup Language (XAML) (XAML) z [ukázky nástroje LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span><span class="sxs-lookup"><span data-stu-id="28eac-113">If you would like to use this sample, download the Extensible Application Markup Language (XAML) files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
1. <span data-ttu-id="28eac-114">Vyvine aplikaci do bodu, kde chcete spustit lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="28eac-114">Develop your application to the point where you want to start localization.</span></span>  
  
2. <span data-ttu-id="28eac-115">Určete vývojový jazyk v souboru projektu tak, aby nástroj MSBuild vygeneroval hlavní sestavení a satelitní sestavení (soubor s příponou. Resources. dll), aby obsahoval prostředky neutrálního jazyka.</span><span class="sxs-lookup"><span data-stu-id="28eac-115">Specify the development language in the project file so that MSBuild generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="28eac-116">Soubor projektu v ukázce HelloApp je HelloApp. csproj.</span><span class="sxs-lookup"><span data-stu-id="28eac-116">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="28eac-117">V tomto souboru najdete jazyk vývoje identifikovaný následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="28eac-117">In that file, you will find the development language identified as follows:</span></span>  
  
   `<UICulture>en-US</UICulture>`  
  
3. <span data-ttu-id="28eac-118">Přidejte identifikátory UID do souborů XAML.</span><span class="sxs-lookup"><span data-stu-id="28eac-118">Add Uids to your XAML files.</span></span> <span data-ttu-id="28eac-119">Identifikátory UID se používají ke sledování změn souborů a identifikaci položek, které je nutné přeložit.</span><span class="sxs-lookup"><span data-stu-id="28eac-119">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="28eac-120">Chcete-li do souborů přidat UID, spusťte `updateuid` soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="28eac-120">To add Uids to your files, run `updateuid` on your project file:</span></span>  

   `msbuild -t:updateuid helloapp.csproj`

   <span data-ttu-id="28eac-121">Chcete-li ověřit, zda nemáte žádné nebo duplicitní identifikátory UID, spusťte příkaz `checkuid` :</span><span class="sxs-lookup"><span data-stu-id="28eac-121">To verify that you have no missing or duplicate Uids, run `checkuid`:</span></span>  

   `msbuild -t:checkuid helloapp.csproj`

   <span data-ttu-id="28eac-122">Po spuštění `updateuid` by vaše soubory měly obsahovat identifikátory UID.</span><span class="sxs-lookup"><span data-stu-id="28eac-122">After running `updateuid`, your files should contain Uids.</span></span> <span data-ttu-id="28eac-123">Například v souboru *Pane1. XAML* HelloApp byste měli najít následující:</span><span class="sxs-lookup"><span data-stu-id="28eac-123">For example, in the *Pane1.xaml* file of HelloApp, you should find the following:</span></span>  

   ```xaml
   <StackPanel x:Uid="StackPanel_1">
     <TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>
     <TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>
   </StackPanel>
   ```

## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="28eac-124">Vytvoření satelitního sestavení prostředků neutrálního jazyka</span><span class="sxs-lookup"><span data-stu-id="28eac-124">Create the neutral-language resources satellite assembly</span></span>

<span data-ttu-id="28eac-125">Jakmile je aplikace nakonfigurována tak, aby vygenerovala satelitní sestavení prostředků neutrálního jazyka, sestavíte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="28eac-125">After the application is configured to generate a neutral-language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="28eac-126">Tím se vygeneruje hlavní sestavení aplikace, stejně jako prostředky v neutrálním jazyce, které jsou požadovány LocBaml pro lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="28eac-126">This generates the main application assembly as well as the neutral-language resources satellite assembly that's required by LocBaml for localization.</span></span>

<span data-ttu-id="28eac-127">Sestavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="28eac-127">To build the application:</span></span>  
  
1. <span data-ttu-id="28eac-128">Zkompiluje HelloApp a vytvoří dynamickou knihovnu (DLL):</span><span class="sxs-lookup"><span data-stu-id="28eac-128">Compile HelloApp to create a dynamic-link library (DLL):</span></span>  
  
   `msbuild helloapp.csproj`
  
2. <span data-ttu-id="28eac-129">Nově vytvořené sestavení hlavní aplikace, HelloApp. exe, je vytvořeno v následující složce: *C:\HelloApp\Bin\Debug*</span><span class="sxs-lookup"><span data-stu-id="28eac-129">The newly created main application assembly, HelloApp.exe, is created in the following folder: *C:\HelloApp\Bin\Debug*</span></span>
  
3. <span data-ttu-id="28eac-130">Nově vytvořené prostředky neutrálního cloudového sestavení HelloApp. Resources. dll se vytvoří v následující složce: *C:\HelloApp\Bin\Debug\en-US*</span><span class="sxs-lookup"><span data-stu-id="28eac-130">The newly created neutral-language resources satellite assembly, HelloApp.resources.dll, is created in the following folder: *C:\HelloApp\Bin\Debug\en-US*</span></span>
  
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="28eac-131">Sestavení nástroje LocBaml</span><span class="sxs-lookup"><span data-stu-id="28eac-131">Build the LocBaml tool</span></span>  
  
1. <span data-ttu-id="28eac-132">Všechny soubory, které jsou nezbytné pro sestavení LocBaml, jsou umístěny v ukázkách WPF.</span><span class="sxs-lookup"><span data-stu-id="28eac-132">All the files necessary to build LocBaml are located in the WPF samples.</span></span> <span data-ttu-id="28eac-133">Stažení souborů C# z [ukázky nástroje LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)</span><span class="sxs-lookup"><span data-stu-id="28eac-133">Download the C# files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
2. <span data-ttu-id="28eac-134">Z příkazového řádku spusťte soubor projektu (LocBaml. csproj) pro sestavení nástroje:</span><span class="sxs-lookup"><span data-stu-id="28eac-134">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  

   `msbuild locbaml.csproj`
  
3. <span data-ttu-id="28eac-135">Pokud chcete najít nově vytvořený spustitelný soubor (LocBaml. exe), otevřete adresář *bin\Release* .</span><span class="sxs-lookup"><span data-stu-id="28eac-135">Go to the *Bin\Release* directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="28eac-136">Příklad: *C:\LocBaml\Bin\Release\locbaml.exe*</span><span class="sxs-lookup"><span data-stu-id="28eac-136">Example: *C:\LocBaml\Bin\Release\locbaml.exe*</span></span>
  
4. <span data-ttu-id="28eac-137">Možnosti, které můžete zadat při spuštění LocBaml, jsou následující.</span><span class="sxs-lookup"><span data-stu-id="28eac-137">The options that you can specify when you run LocBaml are as follows.</span></span>

   | <span data-ttu-id="28eac-138">Možnost</span><span class="sxs-lookup"><span data-stu-id="28eac-138">Option</span></span> | <span data-ttu-id="28eac-139">Popis</span><span class="sxs-lookup"><span data-stu-id="28eac-139">Description</span></span>|
   | - | - |
   | <span data-ttu-id="28eac-140">`parse` nebo `-p`</span><span class="sxs-lookup"><span data-stu-id="28eac-140">`parse` or `-p`</span></span> | <span data-ttu-id="28eac-141">Analyzuje soubory BAML, prostředků nebo DLL pro vygenerování souboru. csv nebo. txt.</span><span class="sxs-lookup"><span data-stu-id="28eac-141">Parses Baml, resources, or DLL files to generate a .csv or .txt file.</span></span> |
   | <span data-ttu-id="28eac-142">`generate` nebo `-g`</span><span class="sxs-lookup"><span data-stu-id="28eac-142">`generate` or `-g`</span></span> | <span data-ttu-id="28eac-143">Generuje lokalizovaný binární soubor pomocí přeloženého souboru.</span><span class="sxs-lookup"><span data-stu-id="28eac-143">Generates a localized binary file by using a translated file.</span></span> |
   | <span data-ttu-id="28eac-144">`out`nebo `-o` {*adresář*]</span><span class="sxs-lookup"><span data-stu-id="28eac-144">`out` or `-o` {*filedirectory*]</span></span> | <span data-ttu-id="28eac-145">Název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="28eac-145">Output file name.</span></span> |
   | <span data-ttu-id="28eac-146">`culture`nebo `-cul` {*culture*]</span><span class="sxs-lookup"><span data-stu-id="28eac-146">`culture` or `-cul` {*culture*]</span></span> | <span data-ttu-id="28eac-147">Národní prostředí výstupních sestavení.</span><span class="sxs-lookup"><span data-stu-id="28eac-147">Locale of output assemblies.</span></span> |
   | <span data-ttu-id="28eac-148">`translation`nebo `-trans` {*Translation. csv*]</span><span class="sxs-lookup"><span data-stu-id="28eac-148">`translation` or `-trans` {*translation.csv*]</span></span> | <span data-ttu-id="28eac-149">Přeložený nebo lokalizovaný soubor.</span><span class="sxs-lookup"><span data-stu-id="28eac-149">Translated or localized file.</span></span> |
   | <span data-ttu-id="28eac-150">`asmpath`nebo `-asmpath` {*adresář*]</span><span class="sxs-lookup"><span data-stu-id="28eac-150">`asmpath` or `-asmpath` {*filedirectory*]</span></span> | <span data-ttu-id="28eac-151">Pokud váš kód jazyka XAML obsahuje vlastní ovládací prvky, je nutné dodat `asmpath` sestavení vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="28eac-151">If your XAML code contains custom controls, you must supply the `asmpath` to the custom control assembly.</span></span> |
   | `nologo` | <span data-ttu-id="28eac-152">Nezobrazí žádné logo ani informace o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="28eac-152">Displays no logo or copyright information.</span></span> |
   | `verbose` | <span data-ttu-id="28eac-153">Zobrazí podrobné informace o režimu.</span><span class="sxs-lookup"><span data-stu-id="28eac-153">Displays verbose mode information.</span></span> |
  
   > [!NOTE]
   > <span data-ttu-id="28eac-154">Pokud při spuštění nástroje potřebujete seznam možností, zadejte `LocBaml.exe` a stiskněte klávesu **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="28eac-154">If you need a list of the options when you are running the tool, enter `LocBaml.exe` and then press **Enter**.</span></span>
  
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="28eac-155">Použití LocBaml k analýze souboru</span><span class="sxs-lookup"><span data-stu-id="28eac-155">Use LocBaml to parse a file</span></span>

<span data-ttu-id="28eac-156">Nyní, když jste vytvořili nástroj LocBaml, jste připraveni ho použít k analýze souboru HelloApp. Resources. dll pro extrakci textového obsahu, který bude lokalizován.</span><span class="sxs-lookup"><span data-stu-id="28eac-156">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1. <span data-ttu-id="28eac-157">Zkopírujte LocBaml. exe do složky bin\Debug vaší aplikace, kde bylo vytvořeno hlavní sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="28eac-157">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2. <span data-ttu-id="28eac-158">Chcete-li analyzovat soubor satelitního sestavení a uložit výstup do souboru. csv, použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="28eac-158">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
   `LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv`
  
   > [!NOTE]
   > <span data-ttu-id="28eac-159">Pokud vstupní soubor HelloApp. Resources. dll není ve stejném adresáři jako LocBaml. exe, přesuňte jeden ze souborů tak, aby oba soubory byly ve stejném adresáři.</span><span class="sxs-lookup"><span data-stu-id="28eac-159">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3. <span data-ttu-id="28eac-160">Když spustíte LocBaml k analýze souborů, výstup se skládá ze sedmi polí oddělených čárkami (soubory. csv) nebo karet (soubory. txt).</span><span class="sxs-lookup"><span data-stu-id="28eac-160">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="28eac-161">Následující příklad ukazuje analyzovaný soubor. CSV pro HelloApp. Resources. dll:</span><span class="sxs-lookup"><span data-stu-id="28eac-161">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="28eac-162">HelloApp. g. en-US. Resources: Window1. BAML, Stack1: System. Windows. Controls. StackPanel. $Content, ignore, FALSE, FALSE, #Text1; #Text2;</span><span class="sxs-lookup"><span data-stu-id="28eac-162">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="28eac-163">HelloApp. g. en-US. Resources: Window1. BAML, Text1: System. Windows. Controls. TextBlock. $Content, None, TRUE, TRUE, Hello World</span><span class="sxs-lookup"><span data-stu-id="28eac-163">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="28eac-164">HelloApp. g. en-US. Resources: Window1. BAML, Text2: System. Windows. Controls. TextBlock. $Content, None, true, true, World</span><span class="sxs-lookup"><span data-stu-id="28eac-164">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="28eac-165">Sedm polí:</span><span class="sxs-lookup"><span data-stu-id="28eac-165">The seven fields are:</span></span>  
  
   - <span data-ttu-id="28eac-166">**Název BAML**</span><span class="sxs-lookup"><span data-stu-id="28eac-166">**BAML Name**.</span></span> <span data-ttu-id="28eac-167">Název prostředku BAML s ohledem na satelitní sestavení zdrojového jazyka.</span><span class="sxs-lookup"><span data-stu-id="28eac-167">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   - <span data-ttu-id="28eac-168">**Klíč prostředku**.</span><span class="sxs-lookup"><span data-stu-id="28eac-168">**Resource Key**.</span></span> <span data-ttu-id="28eac-169">Lokalizovaný identifikátor prostředku.</span><span class="sxs-lookup"><span data-stu-id="28eac-169">The localized resource identifier.</span></span>  
  
   - <span data-ttu-id="28eac-170">**Kategorie**.</span><span class="sxs-lookup"><span data-stu-id="28eac-170">**Category**.</span></span> <span data-ttu-id="28eac-171">Typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="28eac-171">The value type.</span></span> <span data-ttu-id="28eac-172">Viz [lokalizace atributů a komentářů](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="28eac-172">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="28eac-173">**Čitelnost**.</span><span class="sxs-lookup"><span data-stu-id="28eac-173">**Readability**.</span></span> <span data-ttu-id="28eac-174">Určuje, zda je možné hodnotu číst pomocí lokalizátora.</span><span class="sxs-lookup"><span data-stu-id="28eac-174">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="28eac-175">Viz [lokalizace atributů a komentářů](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="28eac-175">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="28eac-176">**Upravitelnost**.</span><span class="sxs-lookup"><span data-stu-id="28eac-176">**Modifiability**.</span></span> <span data-ttu-id="28eac-177">Určuje, zda lze hodnotu upravit pomocí lokalizátora.</span><span class="sxs-lookup"><span data-stu-id="28eac-177">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="28eac-178">Viz [lokalizace atributů a komentářů](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="28eac-178">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="28eac-179">**Komentáře**.</span><span class="sxs-lookup"><span data-stu-id="28eac-179">**Comments**.</span></span> <span data-ttu-id="28eac-180">Další popis hodnoty, která vám pomůže určit, jak je hodnota lokalizována.</span><span class="sxs-lookup"><span data-stu-id="28eac-180">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="28eac-181">Viz [lokalizace atributů a komentářů](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="28eac-181">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="28eac-182">**Hodnota**.</span><span class="sxs-lookup"><span data-stu-id="28eac-182">**Value**.</span></span> <span data-ttu-id="28eac-183">Textová hodnota, která se má přeložit na požadovanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="28eac-183">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="28eac-184">Následující tabulka ukazuje, jak se tato pole mapují na hodnoty oddělené v souboru. CSV:</span><span class="sxs-lookup"><span data-stu-id="28eac-184">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="28eac-185">Název BAML</span><span class="sxs-lookup"><span data-stu-id="28eac-185">BAML name</span></span>|<span data-ttu-id="28eac-186">Klíč prostředku</span><span class="sxs-lookup"><span data-stu-id="28eac-186">Resource key</span></span>|<span data-ttu-id="28eac-187">Kategorie</span><span class="sxs-lookup"><span data-stu-id="28eac-187">Category</span></span>|<span data-ttu-id="28eac-188">Čitelnost</span><span class="sxs-lookup"><span data-stu-id="28eac-188">Readability</span></span>|<span data-ttu-id="28eac-189">Upravitelnost</span><span class="sxs-lookup"><span data-stu-id="28eac-189">Modifiability</span></span>|<span data-ttu-id="28eac-190">Komentáře</span><span class="sxs-lookup"><span data-stu-id="28eac-190">Comments</span></span>|<span data-ttu-id="28eac-191">Hodnota</span><span class="sxs-lookup"><span data-stu-id="28eac-191">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="28eac-192">HelloApp. g. en-US. Resources: Window1. BAML</span><span class="sxs-lookup"><span data-stu-id="28eac-192">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="28eac-193">Stack1: System. Windows. Controls. StackPanel. $Content</span><span class="sxs-lookup"><span data-stu-id="28eac-193">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="28eac-194">Ignorovat</span><span class="sxs-lookup"><span data-stu-id="28eac-194">Ignore</span></span>|<span data-ttu-id="28eac-195">FALSE</span><span class="sxs-lookup"><span data-stu-id="28eac-195">FALSE</span></span>|<span data-ttu-id="28eac-196">FALSE</span><span class="sxs-lookup"><span data-stu-id="28eac-196">FALSE</span></span>||<span data-ttu-id="28eac-197">#Text1; #Text2</span><span class="sxs-lookup"><span data-stu-id="28eac-197">#Text1;#Text2</span></span>|
   |<span data-ttu-id="28eac-198">HelloApp. g. en-US. Resources: Window1. BAML</span><span class="sxs-lookup"><span data-stu-id="28eac-198">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="28eac-199">Text1: System. Windows. Controls. TextBlock. $Content</span><span class="sxs-lookup"><span data-stu-id="28eac-199">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="28eac-200">Žádné</span><span class="sxs-lookup"><span data-stu-id="28eac-200">None</span></span>|<span data-ttu-id="28eac-201">TRUE</span><span class="sxs-lookup"><span data-stu-id="28eac-201">TRUE</span></span>|<span data-ttu-id="28eac-202">TRUE</span><span class="sxs-lookup"><span data-stu-id="28eac-202">TRUE</span></span>||<span data-ttu-id="28eac-203">Hello World</span><span class="sxs-lookup"><span data-stu-id="28eac-203">Hello World</span></span>|
   |<span data-ttu-id="28eac-204">HelloApp. g. en-US. Resources: Window1. BAML</span><span class="sxs-lookup"><span data-stu-id="28eac-204">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="28eac-205">Text2: System. Windows. Controls. TextBlock. $Content</span><span class="sxs-lookup"><span data-stu-id="28eac-205">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="28eac-206">Žádné</span><span class="sxs-lookup"><span data-stu-id="28eac-206">None</span></span>|<span data-ttu-id="28eac-207">TRUE</span><span class="sxs-lookup"><span data-stu-id="28eac-207">TRUE</span></span>|<span data-ttu-id="28eac-208">TRUE</span><span class="sxs-lookup"><span data-stu-id="28eac-208">TRUE</span></span>||<span data-ttu-id="28eac-209">Vylučte ze světa</span><span class="sxs-lookup"><span data-stu-id="28eac-209">Goodbye World</span></span>|
  
   <span data-ttu-id="28eac-210">Všimněte si, že všechny hodnoty pole **Komentáře** neobsahují žádné hodnoty; Pokud pole nemá hodnotu, je prázdné.</span><span class="sxs-lookup"><span data-stu-id="28eac-210">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="28eac-211">Všimněte si také, že položka v prvním řádku není čitelná ani upravitelná a má "Ignore" jako hodnotu **kategorie** , všechny, které označují, že hodnotu nelze lokalizovat.</span><span class="sxs-lookup"><span data-stu-id="28eac-211">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4. <span data-ttu-id="28eac-212">Chcete-li usnadnit zjišťování lokalizovatelných položek v analyzovaných souborech, zejména ve velkých souborech, můžete položky řadit nebo filtrovat podle **kategorie**, **čitelnosti**a **volby.**</span><span class="sxs-lookup"><span data-stu-id="28eac-212">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="28eac-213">Můžete například vyfiltrovat nečitelný a neupravitelné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="28eac-213">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
## <a name="translate-the-localizable-content"></a><span data-ttu-id="28eac-214">Přeložit Lokalizovatelný obsah</span><span class="sxs-lookup"><span data-stu-id="28eac-214">Translate the localizable content</span></span>

<span data-ttu-id="28eac-215">Použijte libovolný nástroj, který máte k dispozici pro překlad extrahovaný obsah.</span><span class="sxs-lookup"><span data-stu-id="28eac-215">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="28eac-216">Dobrým způsobem, jak to provést, je zapsání prostředků do souboru. csv a jejich zobrazení v aplikaci Microsoft Excel a provádění změn v překladu na poslední sloupec (hodnota).</span><span class="sxs-lookup"><span data-stu-id="28eac-216">A good way to do this is to write the resources to a .csv file and view them in Microsoft Excel, making translation changes to the last column (value).</span></span>  
  
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="28eac-217">Použití LocBaml k vygenerování nového souboru. Resources. dll</span><span class="sxs-lookup"><span data-stu-id="28eac-217">Use LocBaml to generate a new .resources.dll file</span></span>

<span data-ttu-id="28eac-218">Obsah, který byl identifikován analýzou HelloApp. Resources. dll s LocBaml, byl přeložen a musí být sloučen zpět do původní aplikace.</span><span class="sxs-lookup"><span data-stu-id="28eac-218">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="28eac-219">Pomocí `generate` Možnosti nebo `-g` Vygenerujte nový soubor. Resources. dll.</span><span class="sxs-lookup"><span data-stu-id="28eac-219">Use the `generate` or `-g` option to generate a new .resources.dll file.</span></span>  
  
1. <span data-ttu-id="28eac-220">Pomocí následující syntaxe Vygenerujte nový soubor HelloApp. Resources. dll.</span><span class="sxs-lookup"><span data-stu-id="28eac-220">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="28eac-221">Označte jazykovou verzi jako en-US (/CUL: en-US).</span><span class="sxs-lookup"><span data-stu-id="28eac-221">Mark the culture as en-US (/cul:en-US).</span></span>  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US`  

   > [!NOTE]
   > <span data-ttu-id="28eac-222">Pokud vstupní soubor Hello. csv není ve stejném adresáři jako spustitelný soubor LocBaml. exe, přesuňte jeden ze souborů tak, aby oba soubory byly ve stejném adresáři.</span><span class="sxs-lookup"><span data-stu-id="28eac-222">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2. <span data-ttu-id="28eac-223">Nahraďte starý soubor *HelloApp. Resources. dll* v adresáři *C:\HelloApp\Bin\Debug\en-US\HelloApp.Resources.dll* nově vytvořeným souborem *HelloApp. Resources. dll* .</span><span class="sxs-lookup"><span data-stu-id="28eac-223">Replace the old *HelloApp.resources.dll* file in the *C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll* directory with your newly created *HelloApp.resources.dll* file.</span></span>  
  
3. <span data-ttu-id="28eac-224">V aplikaci by se teď měly přeložit "Hello World" a "rozvažovat World".</span><span class="sxs-lookup"><span data-stu-id="28eac-224">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4. <span data-ttu-id="28eac-225">Chcete-li přeložit na jinou jazykovou verzi, použijte jazykovou verzi jazyka, na který překládáte.</span><span class="sxs-lookup"><span data-stu-id="28eac-225">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="28eac-226">Následující příklad ukazuje, jak převést na francouzština – kanadská:</span><span class="sxs-lookup"><span data-stu-id="28eac-226">The following example shows how to translate to French-Canadian:</span></span>  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA`  
  
5. <span data-ttu-id="28eac-227">Ve stejném sestavení jako hlavní sestavení aplikace vytvořte novou složku specifickou pro jazykovou verzi, která bude zaustájena nové satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="28eac-227">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="28eac-228">V případě francouzštiny (kanadská) by tato složka byla fr-CA.</span><span class="sxs-lookup"><span data-stu-id="28eac-228">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6. <span data-ttu-id="28eac-229">Zkopírujte vygenerované satelitní sestavení do nové složky.</span><span class="sxs-lookup"><span data-stu-id="28eac-229">Copy the generated satellite assembly to the new folder.</span></span>  
  
7. <span data-ttu-id="28eac-230">Chcete-li otestovat nové satelitní sestavení, je nutné změnit jazykovou verzi, ve které bude aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="28eac-230">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="28eac-231">Toto lze provést jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="28eac-231">You can do this in one of two ways:</span></span>  
  
   - <span data-ttu-id="28eac-232">Změnit místní nastavení operačního systému.</span><span class="sxs-lookup"><span data-stu-id="28eac-232">Change your operating system's regional settings.</span></span>
  
   - <span data-ttu-id="28eac-233">Do App.xaml.cs přidejte do aplikace následující kód:</span><span class="sxs-lookup"><span data-stu-id="28eac-233">In your application, add the following code to App.xaml.cs:</span></span>  
  
     [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
     [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
     [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
## <a name="tips-for-using-locbaml"></a><span data-ttu-id="28eac-234">Tipy pro použití LocBaml</span><span class="sxs-lookup"><span data-stu-id="28eac-234">Tips for Using LocBaml</span></span>  
  
- <span data-ttu-id="28eac-235">Všechna závislá sestavení, která definují vlastní ovládací prvky, musí být zkopírována do místního adresáře LocBaml nebo nainstalována do mezipaměti GAC.</span><span class="sxs-lookup"><span data-stu-id="28eac-235">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="28eac-236">To je nezbytné, protože rozhraní API pro lokalizaci musí mít přístup k závislým sestavením při čtení binárního XAML (BAML).</span><span class="sxs-lookup"><span data-stu-id="28eac-236">This is necessary because the localization API must have access to the dependent assemblies when it reads the binary XAML (BAML).</span></span>  
  
- <span data-ttu-id="28eac-237">Pokud je hlavní sestavení podepsáno, vygenerované DLL prostředku musí být také podepsáno, aby bylo možné ho načíst.</span><span class="sxs-lookup"><span data-stu-id="28eac-237">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
- <span data-ttu-id="28eac-238">Verze lokalizované knihovny DLL prostředku musí být synchronizována s hlavním sestavením.</span><span class="sxs-lookup"><span data-stu-id="28eac-238">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="28eac-239">Viz také</span><span class="sxs-lookup"><span data-stu-id="28eac-239">See also</span></span>

- [<span data-ttu-id="28eac-240">Globalizace pro WPF</span><span class="sxs-lookup"><span data-stu-id="28eac-240">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="28eac-241">Přehled automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="28eac-241">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
