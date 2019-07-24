---
title: 'Postupy: Lokalizace aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: 68bb3b8cd080e5b454776433e65027b7d18e7c3b
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331564"
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="11fd1-102">Postupy: Lokalizace aplikace</span><span class="sxs-lookup"><span data-stu-id="11fd1-102">How to: Localize an Application</span></span>
<span data-ttu-id="11fd1-103">V tomto kurzu se dozvíte, jak vytvořit lokalizovanou aplikaci pomocí nástroje LocBaml.</span><span class="sxs-lookup"><span data-stu-id="11fd1-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11fd1-104">Nástroj LocBaml není aplikací připravenou pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="11fd1-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="11fd1-105">Je prezentován jako ukázka, která používá některá z rozhraní API lokalizace a ukazuje, jak můžete napsat nástroj pro lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="11fd1-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
<a name="Introduction"></a>   
## <a name="overview"></a><span data-ttu-id="11fd1-106">Přehled</span><span class="sxs-lookup"><span data-stu-id="11fd1-106">Overview</span></span>  
 <span data-ttu-id="11fd1-107">Tato diskuze vám poskytne podrobný přístup k lokalizaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="11fd1-107">This discussion gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="11fd1-108">Nejprve připravujete aplikaci tak, aby bylo možné extrahovat text, který bude přeložen.</span><span class="sxs-lookup"><span data-stu-id="11fd1-108">First, you will prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="11fd1-109">Po překladu textu se přeložený text sloučí do nové kopie původní aplikace.</span><span class="sxs-lookup"><span data-stu-id="11fd1-109">After the text is translated, you will merge the translated text into a new copy of the original application.</span></span>  
  
<a name="Requirements"></a>   
## <a name="requirements"></a><span data-ttu-id="11fd1-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11fd1-110">Requirements</span></span>  
 <span data-ttu-id="11fd1-111">V průběhu této diskuze použijete [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], což je kompilátor spouštěný z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="11fd1-111">Over the course of this discussion, you will use [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], which is a compiler that runs from the command line.</span></span>  
  
 <span data-ttu-id="11fd1-112">Také budete vyzváni k použití souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="11fd1-112">Also, you will be instructed to use a project file.</span></span> <span data-ttu-id="11fd1-113">Pokyny k používání [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] a projektových souborů najdete v tématu [sestavení a nasazení](../app-development/building-and-deploying-wpf-applications.md).</span><span class="sxs-lookup"><span data-stu-id="11fd1-113">For instructions on how to use [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] and project files, see [Build and Deploy](../app-development/building-and-deploying-wpf-applications.md).</span></span>  
  
 <span data-ttu-id="11fd1-114">Všechny příklady v této diskuzi používají jako jazykovou verzi en-US (Čeština-US).</span><span class="sxs-lookup"><span data-stu-id="11fd1-114">All the examples in this discussion use en-US (English-US) as the culture.</span></span> <span data-ttu-id="11fd1-115">To vám umožní pracovat s jednotlivými kroky v příkladech bez nutnosti instalovat jiný jazyk.</span><span class="sxs-lookup"><span data-stu-id="11fd1-115">This enables you to work through the steps of the examples without installing a different language.</span></span>  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a><span data-ttu-id="11fd1-116">Vytvoření ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="11fd1-116">Create a Sample Application</span></span>  
 <span data-ttu-id="11fd1-117">V tomto kroku připravíte aplikaci k lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="11fd1-117">In this step, you will prepare your application for localization.</span></span> <span data-ttu-id="11fd1-118">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] V ukázkách je dodána ukázka HelloApp, která bude použita pro příklady kódu v této diskuzi.</span><span class="sxs-lookup"><span data-stu-id="11fd1-118">In the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="11fd1-119">Chcete-li použít tuto ukázku, stáhněte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubory z [ukázky nástroje LocBaml](https://go.microsoft.com/fwlink/?LinkID=160016).</span><span class="sxs-lookup"><span data-stu-id="11fd1-119">If you would like to use this sample, download the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] files from the [LocBaml Tool Sample](https://go.microsoft.com/fwlink/?LinkID=160016).</span></span>  
  
1. <span data-ttu-id="11fd1-120">Vyvine aplikaci do bodu, kde chcete spustit lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="11fd1-120">Develop your application to the point where you want to start localization.</span></span>  
  
2. <span data-ttu-id="11fd1-121">Určete vývojový jazyk v souboru projektu tak, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] aby vygeneroval hlavní sestavení a satelitní sestavení (soubor s příponou. Resources. dll), který obsahuje prostředky neutrálního jazyka.</span><span class="sxs-lookup"><span data-stu-id="11fd1-121">Specify the development language in the project file so that [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="11fd1-122">Soubor projektu v ukázce HelloApp je HelloApp. csproj.</span><span class="sxs-lookup"><span data-stu-id="11fd1-122">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="11fd1-123">V tomto souboru najdete jazyk vývoje identifikovaný následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="11fd1-123">In that file, you will find the development language identified as follows:</span></span>  
  
     `<UICulture>en-US</UICulture>`  
  
3. <span data-ttu-id="11fd1-124">Přidejte do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souborů UID.</span><span class="sxs-lookup"><span data-stu-id="11fd1-124">Add Uids to your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files.</span></span> <span data-ttu-id="11fd1-125">Identifikátory UID se používají ke sledování změn souborů a identifikaci položek, které je nutné přeložit.</span><span class="sxs-lookup"><span data-stu-id="11fd1-125">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="11fd1-126">Chcete-li do souborů přidat identifikátor UID, spusťte v souboru projektu **updateuid** :</span><span class="sxs-lookup"><span data-stu-id="11fd1-126">To add Uids to your files, run **updateuid** on your project file:</span></span>  
  
     <span data-ttu-id="11fd1-127">**MSBuild-t:updateuid helloapp. csproj**</span><span class="sxs-lookup"><span data-stu-id="11fd1-127">**msbuild -t:updateuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="11fd1-128">Pokud chcete ověřit, že nemáte žádné nebo duplicitní identifikátory UID, spusťte **checkuid**:</span><span class="sxs-lookup"><span data-stu-id="11fd1-128">To verify that you have no missing or duplicate Uids, run **checkuid**:</span></span>  
  
     <span data-ttu-id="11fd1-129">**MSBuild-t:checkuid helloapp. csproj**</span><span class="sxs-lookup"><span data-stu-id="11fd1-129">**msbuild -t:checkuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="11fd1-130">Po spuštění **updateuid**by vaše soubory měly obsahovat identifikátory UID.</span><span class="sxs-lookup"><span data-stu-id="11fd1-130">After running **updateuid**, your files should contain Uids.</span></span> <span data-ttu-id="11fd1-131">Například v souboru Pane1. XAML HelloApp byste měli najít následující:</span><span class="sxs-lookup"><span data-stu-id="11fd1-131">For example, in the Pane1.xaml file of HelloApp, you should find the following:</span></span>  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="11fd1-132">Vytvoření satelitního sestavení pro prostředky v neutrálním jazyce</span><span class="sxs-lookup"><span data-stu-id="11fd1-132">Create the Neutral Language Resources Satellite Assembly</span></span>  
 <span data-ttu-id="11fd1-133">Po nakonfigurování aplikace pro generování satelitního sestavení prostředků v neutrálním jazyce sestavíte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="11fd1-133">After the application is configured to generate a neutral language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="11fd1-134">Tím se vygeneruje hlavní sestavení aplikace, stejně jako satelitní sestavení pro prostředky neutrálních jazyků, které je vyžadováno LocBaml pro lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="11fd1-134">This generates the main application assembly, as well as the neutral language resources satellite assembly that is required by LocBaml for localization.</span></span> <span data-ttu-id="11fd1-135">Sestavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="11fd1-135">To build the application:</span></span>  
  
1. <span data-ttu-id="11fd1-136">Zkompilujte HelloApp pro vytvoření [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="11fd1-136">Compile HelloApp to create a [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:</span></span>  
  
     <span data-ttu-id="11fd1-137">**MSBuild helloapp. csproj**</span><span class="sxs-lookup"><span data-stu-id="11fd1-137">**msbuild helloapp.csproj**</span></span>  
  
2. <span data-ttu-id="11fd1-138">Nově vytvořené sestavení hlavní aplikace, HelloApp. exe, je vytvořeno v následující složce:</span><span class="sxs-lookup"><span data-stu-id="11fd1-138">The newly created main application assembly, HelloApp.exe, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. <span data-ttu-id="11fd1-139">Nově vytvořené satelitní sestavení v neutrálních jazycích (HelloApp. Resources. dll) se vytvoří v následující složce:</span><span class="sxs-lookup"><span data-stu-id="11fd1-139">The newly created neutral language resources satellite assembly, HelloApp.resources.dll, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="11fd1-140">Sestavení nástroje LocBaml</span><span class="sxs-lookup"><span data-stu-id="11fd1-140">Build the LocBaml Tool</span></span>  
  
1. <span data-ttu-id="11fd1-141">Všechny soubory potřebné k sestavení LocBaml jsou umístěné v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ukázkách.</span><span class="sxs-lookup"><span data-stu-id="11fd1-141">All the files necessary to build LocBaml are located in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] samples.</span></span> <span data-ttu-id="11fd1-142">Stáhněte si C# soubory z [ukázky nástroje LocBaml](https://go.microsoft.com/fwlink/?LinkID=160016).</span><span class="sxs-lookup"><span data-stu-id="11fd1-142">Download the C# files from the [LocBaml Tool Sample](https://go.microsoft.com/fwlink/?LinkID=160016).</span></span>  
  
2. <span data-ttu-id="11fd1-143">Z příkazového řádku spusťte soubor projektu (LocBaml. csproj) pro sestavení nástroje:</span><span class="sxs-lookup"><span data-stu-id="11fd1-143">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  
  
     <span data-ttu-id="11fd1-144">**MSBuild LocBaml. csproj**</span><span class="sxs-lookup"><span data-stu-id="11fd1-144">**msbuild locbaml.csproj**</span></span>  
  
3. <span data-ttu-id="11fd1-145">Pokud chcete najít nově vytvořený spustitelný soubor (LocBaml. exe), otevřete adresář Bin\Release.</span><span class="sxs-lookup"><span data-stu-id="11fd1-145">Go to the Bin\Release directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="11fd1-146">Příklad: C: \LocBaml\Bin\Release\locbaml.exe.</span><span class="sxs-lookup"><span data-stu-id="11fd1-146">Example:C:\LocBaml\Bin\Release\locbaml.exe.</span></span>  
  
4. <span data-ttu-id="11fd1-147">Možnosti, které můžete zadat při spuštění LocBaml, jsou následující:</span><span class="sxs-lookup"><span data-stu-id="11fd1-147">The options that you can specify when you run LocBaml are as follows:</span></span>  
  
    - <span data-ttu-id="11fd1-148">**analyzovat** nebo **-p:** Analyzuje soubor CSV, prostředky nebo [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] soubory, aby vygeneroval soubor. csv nebo. txt.</span><span class="sxs-lookup"><span data-stu-id="11fd1-148">**parse** or **-p:** Parses Baml, resources, or [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] files to generate a .csv or .txt file.</span></span>  
  
    - <span data-ttu-id="11fd1-149">**Generovat** nebo **-g:** Generuje lokalizovaný binární soubor pomocí přeloženého souboru.</span><span class="sxs-lookup"><span data-stu-id="11fd1-149">**generate** or **-g:** Generates a localized binary file by using a translated file.</span></span>  
  
    - <span data-ttu-id="11fd1-150">**výstupní** nebo **-o** {*adresář adresáře*] **:** Název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="11fd1-150">**out** or **-o** {*filedirectory*] **:** Output file name.</span></span>  
  
    - <span data-ttu-id="11fd1-151">**jazyková verze** nebo **-CUL** {*culture*] **:** Národní prostředí výstupních sestavení.</span><span class="sxs-lookup"><span data-stu-id="11fd1-151">**culture** or **-cul** {*culture*] **:** Locale of output assemblies.</span></span>  
  
    - <span data-ttu-id="11fd1-152">**Překlad** nebo **-trans** {*Translation. csv*] **:** Přeložený nebo lokalizovaný soubor.</span><span class="sxs-lookup"><span data-stu-id="11fd1-152">**translation** or **-trans** {*translation.csv*] **:** Translated or localized file.</span></span>  
  
    - <span data-ttu-id="11fd1-153">**asmPath** nebo **-asmPath:** {*adresář*] **:** Pokud váš [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kód obsahuje vlastní ovládací prvky, je nutné dodat **asmPath** sestavení vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="11fd1-153">**asmpath** or **-asmpath:** {*filedirectory*] **:** If your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code contains custom controls, you must supply the **asmpath** to the custom control assembly.</span></span>  
  
    - <span data-ttu-id="11fd1-154">**nologo** Nezobrazí žádné logo ani informace o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="11fd1-154">**nologo:** Displays no logo or copyright information.</span></span>  
  
    - <span data-ttu-id="11fd1-155">**Podrobné** Zobrazí podrobné informace o režimu.</span><span class="sxs-lookup"><span data-stu-id="11fd1-155">**verbose:** Displays verbose mode information.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="11fd1-156">Pokud při spuštění nástroje potřebujete seznam možností, zadejte **LocBaml. exe** a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="11fd1-156">If you need a list of the options when you are running the tool, type     **LocBaml.exe** and press ENTER.</span></span>  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="11fd1-157">Použití LocBaml k analýze souboru</span><span class="sxs-lookup"><span data-stu-id="11fd1-157">Use LocBaml to Parse a File</span></span>  
 <span data-ttu-id="11fd1-158">Nyní, když jste vytvořili nástroj LocBaml, jste připraveni ho použít k analýze souboru HelloApp. Resources. dll pro extrakci textového obsahu, který bude lokalizován.</span><span class="sxs-lookup"><span data-stu-id="11fd1-158">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1. <span data-ttu-id="11fd1-159">Zkopírujte LocBaml. exe do složky bin\Debug vaší aplikace, kde bylo vytvořeno hlavní sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="11fd1-159">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2. <span data-ttu-id="11fd1-160">Chcete-li analyzovat soubor satelitního sestavení a uložit výstup do souboru. csv, použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="11fd1-160">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
     <span data-ttu-id="11fd1-161">**LocBaml. exe/Parse HelloApp. Resources. dll/out: Hello. csv**</span><span class="sxs-lookup"><span data-stu-id="11fd1-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="11fd1-162">Pokud vstupní soubor HelloApp. Resources. dll není ve stejném adresáři jako LocBaml. exe, přesuňte jeden ze souborů tak, aby oba soubory byly ve stejném adresáři.</span><span class="sxs-lookup"><span data-stu-id="11fd1-162">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3. <span data-ttu-id="11fd1-163">Když spustíte LocBaml k analýze souborů, výstup se skládá ze sedmi polí oddělených čárkami (soubory. csv) nebo karet (soubory. txt).</span><span class="sxs-lookup"><span data-stu-id="11fd1-163">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="11fd1-164">Následující příklad ukazuje analyzovaný soubor. CSV pro HelloApp. Resources. dll:</span><span class="sxs-lookup"><span data-stu-id="11fd1-164">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="11fd1-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span><span class="sxs-lookup"><span data-stu-id="11fd1-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="11fd1-166">HelloApp. g. en-US. Resources: Window1. BAML, Text1: System. Windows. Controls. TextBlock. $Content, None, TRUE, TRUE, Hello World</span><span class="sxs-lookup"><span data-stu-id="11fd1-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="11fd1-167">HelloApp. g. en-US. Resources: Window1. BAML, Text2: System. Windows. Controls. TextBlock. $Content, None, true, true, World</span><span class="sxs-lookup"><span data-stu-id="11fd1-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="11fd1-168">Sedm polí:</span><span class="sxs-lookup"><span data-stu-id="11fd1-168">The seven fields are:</span></span>  
  
   1. <span data-ttu-id="11fd1-169">**Název BAML**</span><span class="sxs-lookup"><span data-stu-id="11fd1-169">**BAML Name**.</span></span> <span data-ttu-id="11fd1-170">Název prostředku BAML s ohledem na satelitní sestavení zdrojového jazyka.</span><span class="sxs-lookup"><span data-stu-id="11fd1-170">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   2. <span data-ttu-id="11fd1-171">**Klíč prostředku**.</span><span class="sxs-lookup"><span data-stu-id="11fd1-171">**Resource Key**.</span></span> <span data-ttu-id="11fd1-172">Lokalizovaný identifikátor prostředku.</span><span class="sxs-lookup"><span data-stu-id="11fd1-172">The localized resource identifier.</span></span>  
  
   3. <span data-ttu-id="11fd1-173">**Kategorie**.</span><span class="sxs-lookup"><span data-stu-id="11fd1-173">**Category**.</span></span> <span data-ttu-id="11fd1-174">Typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="11fd1-174">The value type.</span></span> <span data-ttu-id="11fd1-175">Viz [lokalizace atributů a komentářů](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="11fd1-175">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   4. <span data-ttu-id="11fd1-176">**Čitelnost**.</span><span class="sxs-lookup"><span data-stu-id="11fd1-176">**Readability**.</span></span> <span data-ttu-id="11fd1-177">Určuje, zda je možné hodnotu číst pomocí lokalizátora.</span><span class="sxs-lookup"><span data-stu-id="11fd1-177">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="11fd1-178">Viz [lokalizace atributů a komentářů](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="11fd1-178">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   5. <span data-ttu-id="11fd1-179">**Upravitelnost**.</span><span class="sxs-lookup"><span data-stu-id="11fd1-179">**Modifiability**.</span></span> <span data-ttu-id="11fd1-180">Určuje, zda lze hodnotu upravit pomocí lokalizátora.</span><span class="sxs-lookup"><span data-stu-id="11fd1-180">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="11fd1-181">Viz [lokalizace atributů a komentářů](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="11fd1-181">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   6. <span data-ttu-id="11fd1-182">**Komentáře**.</span><span class="sxs-lookup"><span data-stu-id="11fd1-182">**Comments**.</span></span> <span data-ttu-id="11fd1-183">Další popis hodnoty, která vám pomůže určit, jak je hodnota lokalizována.</span><span class="sxs-lookup"><span data-stu-id="11fd1-183">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="11fd1-184">Viz [lokalizace atributů a komentářů](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="11fd1-184">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   7. <span data-ttu-id="11fd1-185">**Hodnota**.</span><span class="sxs-lookup"><span data-stu-id="11fd1-185">**Value**.</span></span> <span data-ttu-id="11fd1-186">Textová hodnota, která se má přeložit na požadovanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="11fd1-186">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="11fd1-187">Následující tabulka ukazuje, jak se tato pole mapují na hodnoty oddělené v souboru. CSV:</span><span class="sxs-lookup"><span data-stu-id="11fd1-187">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="11fd1-188">Název BAML</span><span class="sxs-lookup"><span data-stu-id="11fd1-188">BAML name</span></span>|<span data-ttu-id="11fd1-189">Klíč prostředku</span><span class="sxs-lookup"><span data-stu-id="11fd1-189">Resource key</span></span>|<span data-ttu-id="11fd1-190">Kategorie</span><span class="sxs-lookup"><span data-stu-id="11fd1-190">Category</span></span>|<span data-ttu-id="11fd1-191">Čitelnost</span><span class="sxs-lookup"><span data-stu-id="11fd1-191">Readability</span></span>|<span data-ttu-id="11fd1-192">Upravitelnost</span><span class="sxs-lookup"><span data-stu-id="11fd1-192">Modifiability</span></span>|<span data-ttu-id="11fd1-193">Komentáře</span><span class="sxs-lookup"><span data-stu-id="11fd1-193">Comments</span></span>|<span data-ttu-id="11fd1-194">Value</span><span class="sxs-lookup"><span data-stu-id="11fd1-194">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="11fd1-195">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="11fd1-195">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="11fd1-196">Stack1:System.Windows.Controls.StackPanel.$Content</span><span class="sxs-lookup"><span data-stu-id="11fd1-196">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="11fd1-197">Ignorovat</span><span class="sxs-lookup"><span data-stu-id="11fd1-197">Ignore</span></span>|<span data-ttu-id="11fd1-198">CHYBNÉ</span><span class="sxs-lookup"><span data-stu-id="11fd1-198">FALSE</span></span>|<span data-ttu-id="11fd1-199">CHYBNÉ</span><span class="sxs-lookup"><span data-stu-id="11fd1-199">FALSE</span></span>||<span data-ttu-id="11fd1-200">#Text1;#Text2</span><span class="sxs-lookup"><span data-stu-id="11fd1-200">#Text1;#Text2</span></span>|
   |<span data-ttu-id="11fd1-201">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="11fd1-201">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="11fd1-202">Text1:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="11fd1-202">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="11fd1-203">Žádný</span><span class="sxs-lookup"><span data-stu-id="11fd1-203">None</span></span>|<span data-ttu-id="11fd1-204">PODMÍNKA</span><span class="sxs-lookup"><span data-stu-id="11fd1-204">TRUE</span></span>|<span data-ttu-id="11fd1-205">PODMÍNKA</span><span class="sxs-lookup"><span data-stu-id="11fd1-205">TRUE</span></span>||<span data-ttu-id="11fd1-206">Hello World</span><span class="sxs-lookup"><span data-stu-id="11fd1-206">Hello World</span></span>|
   |<span data-ttu-id="11fd1-207">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="11fd1-207">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="11fd1-208">Text2:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="11fd1-208">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="11fd1-209">Žádné</span><span class="sxs-lookup"><span data-stu-id="11fd1-209">None</span></span>|<span data-ttu-id="11fd1-210">PODMÍNKA</span><span class="sxs-lookup"><span data-stu-id="11fd1-210">TRUE</span></span>|<span data-ttu-id="11fd1-211">PODMÍNKA</span><span class="sxs-lookup"><span data-stu-id="11fd1-211">TRUE</span></span>||<span data-ttu-id="11fd1-212">Vylučte ze světa</span><span class="sxs-lookup"><span data-stu-id="11fd1-212">Goodbye World</span></span>|
  
   <span data-ttu-id="11fd1-213">Všimněte si, že všechny hodnoty pole **Komentáře** neobsahují žádné hodnoty; Pokud pole nemá hodnotu, je prázdné.</span><span class="sxs-lookup"><span data-stu-id="11fd1-213">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="11fd1-214">Všimněte si také, že položka v prvním řádku není čitelná ani upravitelná a má "Ignore" jako hodnotu **kategorie** , všechny, které označují, že hodnotu nelze lokalizovat.</span><span class="sxs-lookup"><span data-stu-id="11fd1-214">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4. <span data-ttu-id="11fd1-215">Chcete-li usnadnit zjišťování lokalizovatelných položek v analyzovaných souborech, zejména ve velkých souborech, můžete položky řadit nebo filtrovat podle **kategorie**, čitelnosti a **volby.**</span><span class="sxs-lookup"><span data-stu-id="11fd1-215">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="11fd1-216">Můžete například vyfiltrovat nečitelný a neupravitelné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="11fd1-216">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a><span data-ttu-id="11fd1-217">Přeložit Lokalizovatelný obsah</span><span class="sxs-lookup"><span data-stu-id="11fd1-217">Translate the Localizable Content</span></span>  
 <span data-ttu-id="11fd1-218">Použijte libovolný nástroj, který máte k dispozici pro překlad extrahovaný obsah.</span><span class="sxs-lookup"><span data-stu-id="11fd1-218">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="11fd1-219">Dobrým způsobem, jak to provést, je zapsání prostředků do souboru. csv a jejich zobrazení [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)]v nástroji, provádění změn v překladu na poslední sloupec (hodnota).</span><span class="sxs-lookup"><span data-stu-id="11fd1-219">A good way to do this is to write the resources to a .csv file and view them in [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], making translation changes to the last column (value).</span></span>  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="11fd1-220">Použití LocBaml k vygenerování nového souboru. Resources. dll</span><span class="sxs-lookup"><span data-stu-id="11fd1-220">Use LocBaml to Generate a New .resources.dll File</span></span>  
 <span data-ttu-id="11fd1-221">Obsah, který byl identifikován analýzou HelloApp. Resources. dll s LocBaml, byl přeložen a musí být sloučen zpět do původní aplikace.</span><span class="sxs-lookup"><span data-stu-id="11fd1-221">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="11fd1-222">K vygenerování nového souboru. Resources. dll použijte možnost **Generate** nebo **-g** .</span><span class="sxs-lookup"><span data-stu-id="11fd1-222">Use the **generate** or **-g** option to generate a new .resources.dll file.</span></span>  
  
1. <span data-ttu-id="11fd1-223">Pomocí následující syntaxe Vygenerujte nový soubor HelloApp. Resources. dll.</span><span class="sxs-lookup"><span data-stu-id="11fd1-223">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="11fd1-224">Označte jazykovou verzi jako en-US (/CUL: en-US).</span><span class="sxs-lookup"><span data-stu-id="11fd1-224">Mark the culture as en-US (/cul:en-US).</span></span>  
  
     <span data-ttu-id="11fd1-225">**LocBaml. exe/Generate HelloApp. Resources. dll/trans: Hello. csv/out: c:\/CUL: en-US**</span><span class="sxs-lookup"><span data-stu-id="11fd1-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="11fd1-226">Pokud vstupní soubor Hello. csv není ve stejném adresáři jako spustitelný soubor LocBaml. exe, přesuňte jeden ze souborů tak, aby oba soubory byly ve stejném adresáři.</span><span class="sxs-lookup"><span data-stu-id="11fd1-226">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2. <span data-ttu-id="11fd1-227">Nahraďte starý soubor HelloApp. Resources. dll v adresáři C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll nově vytvořeným souborem HelloApp. Resources. dll.</span><span class="sxs-lookup"><span data-stu-id="11fd1-227">Replace the old HelloApp.resources.dll file in the C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll directory with your newly created HelloApp.resources.dll file.</span></span>  
  
3. <span data-ttu-id="11fd1-228">V aplikaci by se teď měly přeložit "Hello World" a "rozvažovat World".</span><span class="sxs-lookup"><span data-stu-id="11fd1-228">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4. <span data-ttu-id="11fd1-229">Chcete-li přeložit na jinou jazykovou verzi, použijte jazykovou verzi jazyka, na který překládáte.</span><span class="sxs-lookup"><span data-stu-id="11fd1-229">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="11fd1-230">Následující příklad ukazuje, jak převést na francouzština – kanadská:</span><span class="sxs-lookup"><span data-stu-id="11fd1-230">The following example shows how to translate to French-Canadian:</span></span>  
  
     <span data-ttu-id="11fd1-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span><span class="sxs-lookup"><span data-stu-id="11fd1-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span></span>  
  
5. <span data-ttu-id="11fd1-232">Ve stejném sestavení jako hlavní sestavení aplikace vytvořte novou složku specifickou pro jazykovou verzi, která bude zaustájena nové satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="11fd1-232">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="11fd1-233">V případě francouzštiny (kanadská) by tato složka byla fr-CA.</span><span class="sxs-lookup"><span data-stu-id="11fd1-233">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6. <span data-ttu-id="11fd1-234">Zkopírujte vygenerované satelitní sestavení do nové složky.</span><span class="sxs-lookup"><span data-stu-id="11fd1-234">Copy the generated satellite assembly to the new folder.</span></span>  
  
7. <span data-ttu-id="11fd1-235">Chcete-li otestovat nové satelitní sestavení, je nutné změnit jazykovou verzi, ve které bude aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="11fd1-235">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="11fd1-236">Toto lze provést jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="11fd1-236">You can do this in one of two ways:</span></span>  
  
    - <span data-ttu-id="11fd1-237">Změňte místní nastavení operačního systému (možnost**Spustit** &#124; **Ovládací panely** &#124; v nabídce **místní a jazyk**).</span><span class="sxs-lookup"><span data-stu-id="11fd1-237">Change your operating system's regional settings (**Start** &#124; **Control Panel** &#124; **Regional and Language Options**).</span></span>  
  
    - <span data-ttu-id="11fd1-238">Do App.xaml.cs přidejte do aplikace následující kód:</span><span class="sxs-lookup"><span data-stu-id="11fd1-238">In your application, add the following code to App.xaml.cs:</span></span>  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a><span data-ttu-id="11fd1-239">Několik tipů pro použití LocBaml</span><span class="sxs-lookup"><span data-stu-id="11fd1-239">Some Tips for Using LocBaml</span></span>  
  
- <span data-ttu-id="11fd1-240">Všechna závislá sestavení, která definují vlastní ovládací prvky, musí být zkopírována do místního adresáře LocBaml nebo nainstalována do mezipaměti GAC.</span><span class="sxs-lookup"><span data-stu-id="11fd1-240">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="11fd1-241">To je nezbytné, protože rozhraní API pro lokalizaci musí mít přístup k závislým sestavením při čtení binárního XAML (BAML).</span><span class="sxs-lookup"><span data-stu-id="11fd1-241">This is necessary because the localization API must have access to the dependent assemblies when it reads the binary XAML (BAML).</span></span>  
  
- <span data-ttu-id="11fd1-242">Pokud je hlavní sestavení podepsáno, vygenerované DLL prostředku musí být také podepsáno, aby bylo možné ho načíst.</span><span class="sxs-lookup"><span data-stu-id="11fd1-242">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
- <span data-ttu-id="11fd1-243">Verze lokalizované knihovny DLL prostředku musí být synchronizována s hlavním sestavením.</span><span class="sxs-lookup"><span data-stu-id="11fd1-243">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a><span data-ttu-id="11fd1-244">Co dál</span><span class="sxs-lookup"><span data-stu-id="11fd1-244">What's Next</span></span>  
 <span data-ttu-id="11fd1-245">Nyní byste měli mít základní informace o tom, jak používat nástroj LocBaml.</span><span class="sxs-lookup"><span data-stu-id="11fd1-245">You should now have a basic understanding of how to use the LocBaml tool.</span></span>  <span data-ttu-id="11fd1-246">Měli byste být schopni vytvořit soubor, který obsahuje identifikátory UID.</span><span class="sxs-lookup"><span data-stu-id="11fd1-246">You should be able to make a file that contains Uids.</span></span> <span data-ttu-id="11fd1-247">Pomocí nástroje LocBaml byste měli být schopni analyzovat soubor pro extrakci lokalizovatelné obsahu a po překladu obsahu byste měli být schopni vygenerovat soubor. Resources. dll, který slučuje přeložený obsah.</span><span class="sxs-lookup"><span data-stu-id="11fd1-247">By using the LocBaml tool, you should be able to parse a file to extract the localizable content, and after the content is translated, you should be able to generate a .resources.dll file that merges the translated content.</span></span> <span data-ttu-id="11fd1-248">Toto téma neobsahuje všechny možné podrobnosti, ale nyní máte znalosti potřebné k použití LocBaml pro lokalizaci vašich aplikací.</span><span class="sxs-lookup"><span data-stu-id="11fd1-248">This topic does not include every possible detail, but you now have the knowledge necessary to use LocBaml for localizing your applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11fd1-249">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11fd1-249">See also</span></span>

- [<span data-ttu-id="11fd1-250">Globalizace pro WPF</span><span class="sxs-lookup"><span data-stu-id="11fd1-250">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="11fd1-251">Přehled automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="11fd1-251">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
