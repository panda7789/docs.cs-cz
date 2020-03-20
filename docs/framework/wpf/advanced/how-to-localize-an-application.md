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
ms.openlocfilehash: f2e7e5e8879e89806cfd457a1af80f51b91871cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174209"
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="021ce-102">Postupy: Lokalizace aplikace</span><span class="sxs-lookup"><span data-stu-id="021ce-102">How to: Localize an Application</span></span>
<span data-ttu-id="021ce-103">Tento kurz vysvětluje, jak vytvořit lokalizovanou aplikaci pomocí nástroje LocBaml.</span><span class="sxs-lookup"><span data-stu-id="021ce-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="021ce-104">Nástroj LocBaml není aplikace připravená k výrobě.</span><span class="sxs-lookup"><span data-stu-id="021ce-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="021ce-105">Je prezentována jako ukázka, která používá některá lokalizační api a ukazuje, jak můžete napsat nástroj lokalizace.</span><span class="sxs-lookup"><span data-stu-id="021ce-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
<a name="Introduction"></a>
## <a name="overview"></a><span data-ttu-id="021ce-106">Přehled</span><span class="sxs-lookup"><span data-stu-id="021ce-106">Overview</span></span>  
 <span data-ttu-id="021ce-107">Tato diskuse poskytuje podrobný přístup k lokalizaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="021ce-107">This discussion gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="021ce-108">Nejprve připravíte aplikaci tak, aby text, který bude přeložen, mohl být extrahován.</span><span class="sxs-lookup"><span data-stu-id="021ce-108">First, you will prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="021ce-109">Po překladu textu sloučíte přeložený text do nové kopie původní aplikace.</span><span class="sxs-lookup"><span data-stu-id="021ce-109">After the text is translated, you will merge the translated text into a new copy of the original application.</span></span>  
  
<a name="Requirements"></a>
## <a name="requirements"></a><span data-ttu-id="021ce-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="021ce-110">Requirements</span></span>  
 <span data-ttu-id="021ce-111">V průběhu této diskuse budete používat modul sestavení Společnosti Microsoft (MSBuild), což je kompilátor, který běží z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="021ce-111">Over the course of this discussion, you will use Microsoft build engine (MSBuild), which is a compiler that runs from the command line.</span></span>  
  
 <span data-ttu-id="021ce-112">Také budete vyzváni k použití souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="021ce-112">Also, you will be instructed to use a project file.</span></span> <span data-ttu-id="021ce-113">Pokyny k použití souborů MSBuild a project naleznete v tématu [Sestavení a nasazení](../app-development/building-and-deploying-wpf-applications.md).</span><span class="sxs-lookup"><span data-stu-id="021ce-113">For instructions on how to use MSBuild and project files, see [Build and Deploy](../app-development/building-and-deploying-wpf-applications.md).</span></span>  
  
 <span data-ttu-id="021ce-114">Všechny příklady v této diskusi použít en US (anglicky-US) jako jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="021ce-114">All the examples in this discussion use en-US (English-US) as the culture.</span></span> <span data-ttu-id="021ce-115">To umožňuje pracovat prostřednictvím kroků příkladů bez instalace jiného jazyka.</span><span class="sxs-lookup"><span data-stu-id="021ce-115">This enables you to work through the steps of the examples without installing a different language.</span></span>  
  
<a name="create_sample_app"></a>
## <a name="create-a-sample-application"></a><span data-ttu-id="021ce-116">Vytvoření ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="021ce-116">Create a Sample Application</span></span>  
 <span data-ttu-id="021ce-117">V tomto kroku připravíte aplikaci pro lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="021ce-117">In this step, you will prepare your application for localization.</span></span> <span data-ttu-id="021ce-118">Ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vzorcích helloapp ukázka je zadána, která bude použita pro příklady kódu v této diskusi.</span><span class="sxs-lookup"><span data-stu-id="021ce-118">In the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="021ce-119">Pokud chcete použít tuto ukázku, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stáhněte soubory z [ukázky nástroje LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span><span class="sxs-lookup"><span data-stu-id="021ce-119">If you would like to use this sample, download the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
1. <span data-ttu-id="021ce-120">Vývoj aplikace do bodu, kde chcete spustit lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="021ce-120">Develop your application to the point where you want to start localization.</span></span>  
  
2. <span data-ttu-id="021ce-121">Zadejte vývojový jazyk v souboru projektu tak, aby MSBuild generuje hlavní sestavení a satelitní sestavení (soubor s příponou .resources.dll) obsahující neutrální jazykové prostředky.</span><span class="sxs-lookup"><span data-stu-id="021ce-121">Specify the development language in the project file so that MSBuild generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="021ce-122">Soubor projektu v helloapp vzorku je HelloApp.csproj.</span><span class="sxs-lookup"><span data-stu-id="021ce-122">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="021ce-123">V tomto souboru najdete vývojový jazyk identifikovaný takto:</span><span class="sxs-lookup"><span data-stu-id="021ce-123">In that file, you will find the development language identified as follows:</span></span>  
  
     `<UICulture>en-US</UICulture>`  
  
3. <span data-ttu-id="021ce-124">Přidejte do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souborů uidy.</span><span class="sxs-lookup"><span data-stu-id="021ce-124">Add Uids to your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files.</span></span> <span data-ttu-id="021ce-125">Uids se používají ke sledování změn v souborech a k identifikaci položek, které musí být přeloženy.</span><span class="sxs-lookup"><span data-stu-id="021ce-125">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="021ce-126">Chcete-li do souborů přidat uidy, spusťte **updateuid** v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="021ce-126">To add Uids to your files, run **updateuid** on your project file:</span></span>  
  
     <span data-ttu-id="021ce-127">**msbuild -t:updateuid helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="021ce-127">**msbuild -t:updateuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="021ce-128">Chcete-li ověřit, zda nechybí žádné duplicitní identifikátory UID, spusťte **příkaz checkuid**:</span><span class="sxs-lookup"><span data-stu-id="021ce-128">To verify that you have no missing or duplicate Uids, run **checkuid**:</span></span>  
  
     <span data-ttu-id="021ce-129">**msbuild -t:checkuid helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="021ce-129">**msbuild -t:checkuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="021ce-130">Po spuštění **updateuid**, soubory by měly obsahovat UIDs.</span><span class="sxs-lookup"><span data-stu-id="021ce-130">After running **updateuid**, your files should contain Uids.</span></span> <span data-ttu-id="021ce-131">Například v souboru Pane1.xaml HelloApp byste měli najít následující:</span><span class="sxs-lookup"><span data-stu-id="021ce-131">For example, in the Pane1.xaml file of HelloApp, you should find the following:</span></span>  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>
## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="021ce-132">Vytvoření satelitního sestavení neutrálních jazykových prostředků</span><span class="sxs-lookup"><span data-stu-id="021ce-132">Create the Neutral Language Resources Satellite Assembly</span></span>  
 <span data-ttu-id="021ce-133">Po nakonfigurován aplikace generovat neutrální jazyk prostředky satelitní sestavení, sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="021ce-133">After the application is configured to generate a neutral language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="021ce-134">To generuje sestavení hlavní aplikace, stejně jako neutrální jazykové prostředky satelitní sestavení, které je vyžadováno LocBaml pro lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="021ce-134">This generates the main application assembly, as well as the neutral language resources satellite assembly that is required by LocBaml for localization.</span></span> <span data-ttu-id="021ce-135">Vytvoření aplikace:</span><span class="sxs-lookup"><span data-stu-id="021ce-135">To build the application:</span></span>  
  
1. <span data-ttu-id="021ce-136">Kompilace HelloApp pro vytvoření dynamické knihovny (DLL):</span><span class="sxs-lookup"><span data-stu-id="021ce-136">Compile HelloApp to create a dynamic-link library (DLL):</span></span>  
  
     <span data-ttu-id="021ce-137">**msbuild helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="021ce-137">**msbuild helloapp.csproj**</span></span>  
  
2. <span data-ttu-id="021ce-138">Nově vytvořené sestavení hlavní aplikace HelloApp.exe je vytvořeno v následující složce:</span><span class="sxs-lookup"><span data-stu-id="021ce-138">The newly created main application assembly, HelloApp.exe, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. <span data-ttu-id="021ce-139">Nově vytvořené satelitní sestavení prostředků neutrálního jazyka HelloApp.resources.dll je vytvořeno v následující složce:</span><span class="sxs-lookup"><span data-stu-id="021ce-139">The newly created neutral language resources satellite assembly, HelloApp.resources.dll, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="021ce-140">Sestavení nástroje LocBaml</span><span class="sxs-lookup"><span data-stu-id="021ce-140">Build the LocBaml Tool</span></span>  
  
1. <span data-ttu-id="021ce-141">Všechny soubory potřebné k sestavení LocBaml [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou umístěny ve vzorcích.</span><span class="sxs-lookup"><span data-stu-id="021ce-141">All the files necessary to build LocBaml are located in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] samples.</span></span> <span data-ttu-id="021ce-142">Stáhněte soubory C# z [ukázky nástroje LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span><span class="sxs-lookup"><span data-stu-id="021ce-142">Download the C# files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
2. <span data-ttu-id="021ce-143">Z příkazového řádku spusťte soubor projektu (locbaml.csproj) a vytvořte nástroj:</span><span class="sxs-lookup"><span data-stu-id="021ce-143">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  
  
     <span data-ttu-id="021ce-144">**msbuild locbaml.csproj**</span><span class="sxs-lookup"><span data-stu-id="021ce-144">**msbuild locbaml.csproj**</span></span>  
  
3. <span data-ttu-id="021ce-145">Přejděte do adresáře Bin\Release a vyhledejte nově vytvořený spustitelný soubor (locbaml.exe).</span><span class="sxs-lookup"><span data-stu-id="021ce-145">Go to the Bin\Release directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="021ce-146">Příklad:C:\LocBaml\Bin\Release\locbaml.exe.</span><span class="sxs-lookup"><span data-stu-id="021ce-146">Example:C:\LocBaml\Bin\Release\locbaml.exe.</span></span>  
  
4. <span data-ttu-id="021ce-147">Možnosti, které můžete zadat při spuštění LocBaml, jsou následující:</span><span class="sxs-lookup"><span data-stu-id="021ce-147">The options that you can specify when you run LocBaml are as follows:</span></span>  
  
    - <span data-ttu-id="021ce-148">**parse** nebo **-p:** Analyzuje soubory Baml, prostředky nebo DLL a vygeneruje soubor .csv nebo .txt.</span><span class="sxs-lookup"><span data-stu-id="021ce-148">**parse** or **-p:** Parses Baml, resources, or DLL files to generate a .csv or .txt file.</span></span>  
  
    - <span data-ttu-id="021ce-149">**generate** or **-g:** Generuje lokalizovaný binární soubor pomocí přeloženého souboru.</span><span class="sxs-lookup"><span data-stu-id="021ce-149">**generate** or **-g:** Generates a localized binary file by using a translated file.</span></span>  
  
    - <span data-ttu-id="021ce-150">**nebo** **-o** {*filedirectory*] **:** Název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="021ce-150">**out** or **-o** {*filedirectory*] **:** Output file name.</span></span>  
  
    - <span data-ttu-id="021ce-151">**culture** nebo **-cul** {*culture*] **:** Národní prostředí výstupních sestavení.</span><span class="sxs-lookup"><span data-stu-id="021ce-151">**culture** or **-cul** {*culture*] **:** Locale of output assemblies.</span></span>  
  
    - <span data-ttu-id="021ce-152">**překlad** nebo **-trans** {*translation.csv*] **:** Přeložený nebo lokalizovaný soubor.</span><span class="sxs-lookup"><span data-stu-id="021ce-152">**translation** or **-trans** {*translation.csv*] **:** Translated or localized file.</span></span>  
  
    - <span data-ttu-id="021ce-153">**asmpath** nebo **-asmpath:** {*filedirectory*] **:** Pokud váš [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kód obsahuje vlastní ovládací prvky, musíte dodat **asmpath** do sestavení vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="021ce-153">**asmpath** or **-asmpath:** {*filedirectory*] **:** If your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code contains custom controls, you must supply the **asmpath** to the custom control assembly.</span></span>  
  
    - <span data-ttu-id="021ce-154">**nologo:** Nezobrazuje žádné logo ani informace o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="021ce-154">**nologo:** Displays no logo or copyright information.</span></span>  
  
    - <span data-ttu-id="021ce-155">**podrobné:** Zobrazí podrobné informace o režimu.</span><span class="sxs-lookup"><span data-stu-id="021ce-155">**verbose:** Displays verbose mode information.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="021ce-156">Pokud potřebujete seznam možností při spuštění nástroje, zadejte **LocBaml.exe** a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="021ce-156">If you need a list of the options when you are running the tool, type     **LocBaml.exe** and press ENTER.</span></span>  
  
<a name="parse_dll"></a>
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="021ce-157">Analýza souboru pomocí LocBamlu</span><span class="sxs-lookup"><span data-stu-id="021ce-157">Use LocBaml to Parse a File</span></span>  
 <span data-ttu-id="021ce-158">Nyní, když jste vytvořili nástroj LocBaml, jste připraveni jej použít k analýzě HelloApp.resources.dll extrahovat textový obsah, který bude lokalizován.</span><span class="sxs-lookup"><span data-stu-id="021ce-158">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1. <span data-ttu-id="021ce-159">Zkopírujte soubor LocBaml.exe do složky bin\debug aplikace, kde bylo vytvořeno sestavení hlavní aplikace.</span><span class="sxs-lookup"><span data-stu-id="021ce-159">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2. <span data-ttu-id="021ce-160">Chcete-li analyzovat soubor satelitního sestavení a uložit výstup jako soubor .csv, použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="021ce-160">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
     <span data-ttu-id="021ce-161">**LocBaml.exe /analyzovat HelloApp.resources.dll /out:Hello.csv**</span><span class="sxs-lookup"><span data-stu-id="021ce-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="021ce-162">Pokud vstupní soubor HelloApp.resources.dll není ve stejném adresáři jako LocBaml.exe přesunout jeden ze souborů tak, aby oba soubory jsou ve stejném adresáři.</span><span class="sxs-lookup"><span data-stu-id="021ce-162">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3. <span data-ttu-id="021ce-163">Při spuštění LocBaml analyzovat soubory, výstup se skládá ze sedmi polí oddělených čárkami (.csv soubory) nebo karty (.txt soubory).</span><span class="sxs-lookup"><span data-stu-id="021ce-163">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="021ce-164">Následující text ukazuje analyzovaný soubor .csv pro soubor HelloApp.resources.dll:</span><span class="sxs-lookup"><span data-stu-id="021ce-164">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="021ce-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignorovat,FALSE, FALSE,,#Text1;#Text2;</span><span class="sxs-lookup"><span data-stu-id="021ce-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="021ce-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span><span class="sxs-lookup"><span data-stu-id="021ce-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="021ce-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span><span class="sxs-lookup"><span data-stu-id="021ce-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="021ce-168">Sedm polí je:</span><span class="sxs-lookup"><span data-stu-id="021ce-168">The seven fields are:</span></span>  
  
   1. <span data-ttu-id="021ce-169">**Název BAML**.</span><span class="sxs-lookup"><span data-stu-id="021ce-169">**BAML Name**.</span></span> <span data-ttu-id="021ce-170">Název prostředku BAML s ohledem na satelitní sestavení zdrojového jazyka.</span><span class="sxs-lookup"><span data-stu-id="021ce-170">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   2. <span data-ttu-id="021ce-171">**Klíč zdroje**.</span><span class="sxs-lookup"><span data-stu-id="021ce-171">**Resource Key**.</span></span> <span data-ttu-id="021ce-172">Lokalizovaný identifikátor prostředku.</span><span class="sxs-lookup"><span data-stu-id="021ce-172">The localized resource identifier.</span></span>  
  
   3. <span data-ttu-id="021ce-173">**Kategorie**.</span><span class="sxs-lookup"><span data-stu-id="021ce-173">**Category**.</span></span> <span data-ttu-id="021ce-174">Typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="021ce-174">The value type.</span></span> <span data-ttu-id="021ce-175">Viz [Atributy lokalizace a komentáře](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="021ce-175">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   4. <span data-ttu-id="021ce-176">**Čitelnost**.</span><span class="sxs-lookup"><span data-stu-id="021ce-176">**Readability**.</span></span> <span data-ttu-id="021ce-177">Zda lze hodnotu číst lokalizátorem.</span><span class="sxs-lookup"><span data-stu-id="021ce-177">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="021ce-178">Viz [Atributy lokalizace a komentáře](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="021ce-178">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   5. <span data-ttu-id="021ce-179">**Modifikovatelnost**.</span><span class="sxs-lookup"><span data-stu-id="021ce-179">**Modifiability**.</span></span> <span data-ttu-id="021ce-180">Určuje, zda lze hodnotu změnit lokalizátorem.</span><span class="sxs-lookup"><span data-stu-id="021ce-180">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="021ce-181">Viz [Atributy lokalizace a komentáře](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="021ce-181">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   6. <span data-ttu-id="021ce-182">**Komentáře**.</span><span class="sxs-lookup"><span data-stu-id="021ce-182">**Comments**.</span></span> <span data-ttu-id="021ce-183">Další popis hodnoty, která má pomoci určit, jak je hodnota lokalizována.</span><span class="sxs-lookup"><span data-stu-id="021ce-183">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="021ce-184">Viz [Atributy lokalizace a komentáře](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="021ce-184">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   7. <span data-ttu-id="021ce-185">**Hodnota**.</span><span class="sxs-lookup"><span data-stu-id="021ce-185">**Value**.</span></span> <span data-ttu-id="021ce-186">Textová hodnota přeložit do požadované jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="021ce-186">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="021ce-187">Následující tabulka ukazuje, jak se tato pole mapují na oddělené hodnoty souboru CSV:</span><span class="sxs-lookup"><span data-stu-id="021ce-187">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="021ce-188">Název BAML</span><span class="sxs-lookup"><span data-stu-id="021ce-188">BAML name</span></span>|<span data-ttu-id="021ce-189">Klíč prostředku</span><span class="sxs-lookup"><span data-stu-id="021ce-189">Resource key</span></span>|<span data-ttu-id="021ce-190">Kategorie</span><span class="sxs-lookup"><span data-stu-id="021ce-190">Category</span></span>|<span data-ttu-id="021ce-191">Čitelnost</span><span class="sxs-lookup"><span data-stu-id="021ce-191">Readability</span></span>|<span data-ttu-id="021ce-192">Modifiability</span><span class="sxs-lookup"><span data-stu-id="021ce-192">Modifiability</span></span>|<span data-ttu-id="021ce-193">Komentáře</span><span class="sxs-lookup"><span data-stu-id="021ce-193">Comments</span></span>|<span data-ttu-id="021ce-194">Hodnota</span><span class="sxs-lookup"><span data-stu-id="021ce-194">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="021ce-195">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="021ce-195">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="021ce-196">Stack1:System.Windows.Controls.StackPanel.$Content</span><span class="sxs-lookup"><span data-stu-id="021ce-196">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="021ce-197">Ignorovat</span><span class="sxs-lookup"><span data-stu-id="021ce-197">Ignore</span></span>|<span data-ttu-id="021ce-198">FALSE</span><span class="sxs-lookup"><span data-stu-id="021ce-198">FALSE</span></span>|<span data-ttu-id="021ce-199">FALSE</span><span class="sxs-lookup"><span data-stu-id="021ce-199">FALSE</span></span>||<span data-ttu-id="021ce-200">#Text1;#Text2</span><span class="sxs-lookup"><span data-stu-id="021ce-200">#Text1;#Text2</span></span>|
   |<span data-ttu-id="021ce-201">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="021ce-201">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="021ce-202">Text1:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="021ce-202">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="021ce-203">Žádný</span><span class="sxs-lookup"><span data-stu-id="021ce-203">None</span></span>|<span data-ttu-id="021ce-204">TRUE</span><span class="sxs-lookup"><span data-stu-id="021ce-204">TRUE</span></span>|<span data-ttu-id="021ce-205">TRUE</span><span class="sxs-lookup"><span data-stu-id="021ce-205">TRUE</span></span>||<span data-ttu-id="021ce-206">Hello World</span><span class="sxs-lookup"><span data-stu-id="021ce-206">Hello World</span></span>|
   |<span data-ttu-id="021ce-207">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="021ce-207">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="021ce-208">Text2:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="021ce-208">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="021ce-209">Žádný</span><span class="sxs-lookup"><span data-stu-id="021ce-209">None</span></span>|<span data-ttu-id="021ce-210">TRUE</span><span class="sxs-lookup"><span data-stu-id="021ce-210">TRUE</span></span>|<span data-ttu-id="021ce-211">TRUE</span><span class="sxs-lookup"><span data-stu-id="021ce-211">TRUE</span></span>||<span data-ttu-id="021ce-212">Sbohem svět</span><span class="sxs-lookup"><span data-stu-id="021ce-212">Goodbye World</span></span>|
  
   <span data-ttu-id="021ce-213">Všimněte si, že všechny hodnoty pro **pole Komentáře** neobsahují žádné hodnoty; Pokud pole nemá hodnotu, je prázdné.</span><span class="sxs-lookup"><span data-stu-id="021ce-213">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="021ce-214">Všimněte si také, že položka v prvním řádku není čitelná ani upravitelná a má jako hodnotu **Kategorie** hodnotu "Ignorovat", což znamená, že hodnota není lokalizovatelná.</span><span class="sxs-lookup"><span data-stu-id="021ce-214">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4. <span data-ttu-id="021ce-215">Chcete-li usnadnit zjišťování lokalizovatelných položek v analyzovaných souborech, zejména ve velkých souborech, můžete položky seřadit nebo filtrovat podle **kategorie**, **čitelnosti**a **upravitelnosti**.</span><span class="sxs-lookup"><span data-stu-id="021ce-215">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="021ce-216">Můžete například odfiltrovat nečitelné a neupravitelné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="021ce-216">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
<a name="translate_loc_content"></a>
## <a name="translate-the-localizable-content"></a><span data-ttu-id="021ce-217">Přeložit lokalizovatelný obsah</span><span class="sxs-lookup"><span data-stu-id="021ce-217">Translate the Localizable Content</span></span>  
 <span data-ttu-id="021ce-218">K překladu extrahovaného obsahu použijte libovolný nástroj, který máte k dispozici.</span><span class="sxs-lookup"><span data-stu-id="021ce-218">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="021ce-219">Dobrým způsobem, jak to provést, je zapsat prostředky do souboru .csv a zobrazit je v aplikaci Microsoft Excel, takže překlad změny posledního sloupce (hodnota).</span><span class="sxs-lookup"><span data-stu-id="021ce-219">A good way to do this is to write the resources to a .csv file and view them in Microsoft Excel, making translation changes to the last column (value).</span></span>  
  
<a name="merge_translations"></a>
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="021ce-220">Použití LocBamlu ke generování nového souboru .resources.dll</span><span class="sxs-lookup"><span data-stu-id="021ce-220">Use LocBaml to Generate a New .resources.dll File</span></span>  
 <span data-ttu-id="021ce-221">Obsah, který byl identifikován analýzou HelloApp.resources.dll s LocBaml byl přeložen a musí být sloučeny zpět do původní aplikace.</span><span class="sxs-lookup"><span data-stu-id="021ce-221">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="021ce-222">Pomocí možnosti **generate** nebo **-g** vygenerujte nový soubor .resources.dll.</span><span class="sxs-lookup"><span data-stu-id="021ce-222">Use the **generate** or **-g** option to generate a new .resources.dll file.</span></span>  
  
1. <span data-ttu-id="021ce-223">Následující syntaxe slouží ke generování nového souboru HelloApp.resources.dll.</span><span class="sxs-lookup"><span data-stu-id="021ce-223">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="021ce-224">Označte jazykovou verzi jako en US (/cul:en-US).</span><span class="sxs-lookup"><span data-stu-id="021ce-224">Mark the culture as en-US (/cul:en-US).</span></span>  
  
     <span data-ttu-id="021ce-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span><span class="sxs-lookup"><span data-stu-id="021ce-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="021ce-226">Pokud vstupní soubor Hello.csv není ve stejném adresáři jako spustitelný soubor LocBaml.exe, přesuňte jeden ze souborů tak, aby oba soubory byly ve stejném adresáři.</span><span class="sxs-lookup"><span data-stu-id="021ce-226">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2. <span data-ttu-id="021ce-227">Nahraďte starý soubor HelloApp.resources.dll v adresáři C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll nově vytvořeným souborem HelloApp.resources.dll.</span><span class="sxs-lookup"><span data-stu-id="021ce-227">Replace the old HelloApp.resources.dll file in the C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll directory with your newly created HelloApp.resources.dll file.</span></span>  
  
3. <span data-ttu-id="021ce-228">"Hello World" a "Goodbye World" by nyní měly být přeloženy do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="021ce-228">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4. <span data-ttu-id="021ce-229">Chcete-li přeložit do jiné jazykové verze, použijte jazykovou verzi jazyka, do kterého překládáte.</span><span class="sxs-lookup"><span data-stu-id="021ce-229">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="021ce-230">Následující příklad ukazuje, jak přeložit do francouzština-kanadská:</span><span class="sxs-lookup"><span data-stu-id="021ce-230">The following example shows how to translate to French-Canadian:</span></span>  
  
     <span data-ttu-id="021ce-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span><span class="sxs-lookup"><span data-stu-id="021ce-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span></span>  
  
5. <span data-ttu-id="021ce-232">Ve stejném sestavení jako sestavení hlavní aplikace vytvořte novou složku specifickou pro jazykovou verzi pro nové satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="021ce-232">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="021ce-233">Pro francouzsko-kanadské, složka by fr-CA.</span><span class="sxs-lookup"><span data-stu-id="021ce-233">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6. <span data-ttu-id="021ce-234">Zkopírujte generované satelitní sestavení do nové složky.</span><span class="sxs-lookup"><span data-stu-id="021ce-234">Copy the generated satellite assembly to the new folder.</span></span>  
  
7. <span data-ttu-id="021ce-235">Chcete-li otestovat nové satelitní sestavení, je třeba změnit jazykovou verzi, pod kterou bude aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="021ce-235">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="021ce-236">Toto lze provést jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="021ce-236">You can do this in one of two ways:</span></span>  
  
    - <span data-ttu-id="021ce-237">Změňte místní nastavení operačního systému **(Spustit** &#124; **Ovládací panely** &#124; **místní a jazykové možnosti).**</span><span class="sxs-lookup"><span data-stu-id="021ce-237">Change your operating system's regional settings (**Start** &#124; **Control Panel** &#124; **Regional and Language Options**).</span></span>  
  
    - <span data-ttu-id="021ce-238">Do aplikace přidejte do App.xaml.cs následující kód:</span><span class="sxs-lookup"><span data-stu-id="021ce-238">In your application, add the following code to App.xaml.cs:</span></span>  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>
## <a name="some-tips-for-using-locbaml"></a><span data-ttu-id="021ce-239">Několik tipů pro použití LocBaml</span><span class="sxs-lookup"><span data-stu-id="021ce-239">Some Tips for Using LocBaml</span></span>  
  
- <span data-ttu-id="021ce-240">Všechna závislá sestavení, která definují vlastní ovládací prvky, musí být zkopírována do místního adresáře LocBamlu nebo nainstalována do gac.</span><span class="sxs-lookup"><span data-stu-id="021ce-240">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="021ce-241">To je nezbytné, protože rozhraní API lokalizace musí mít přístup k závislým sestavením při čtení binárního XAML (BAML).</span><span class="sxs-lookup"><span data-stu-id="021ce-241">This is necessary because the localization API must have access to the dependent assemblies when it reads the binary XAML (BAML).</span></span>  
  
- <span data-ttu-id="021ce-242">Pokud je hlavní sestavení podepsáno, musí být také podepsána vygenerovaná dll prostředku, aby mohla být načtena.</span><span class="sxs-lookup"><span data-stu-id="021ce-242">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
- <span data-ttu-id="021ce-243">Verze lokalizované dll prostředku musí být synchronizována s hlavním sestavením.</span><span class="sxs-lookup"><span data-stu-id="021ce-243">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>  
  
<a name="Whats_Next"></a>
## <a name="whats-next"></a><span data-ttu-id="021ce-244">Co bude dál</span><span class="sxs-lookup"><span data-stu-id="021ce-244">What's Next</span></span>  
 <span data-ttu-id="021ce-245">Nyní byste měli mít základní znalosti o tom, jak používat nástroj LocBaml.</span><span class="sxs-lookup"><span data-stu-id="021ce-245">You should now have a basic understanding of how to use the LocBaml tool.</span></span>  <span data-ttu-id="021ce-246">Měli byste být schopni vytvořit soubor, který obsahuje UIDs.</span><span class="sxs-lookup"><span data-stu-id="021ce-246">You should be able to make a file that contains Uids.</span></span> <span data-ttu-id="021ce-247">Pomocí nástroje LocBaml byste měli být schopni analyzovat soubor, abyste extrahovali lokalizovatelný obsah, a po překladu obsahu byste měli být schopni vygenerovat soubor .resources.dll, který slučuje přeložený obsah.</span><span class="sxs-lookup"><span data-stu-id="021ce-247">By using the LocBaml tool, you should be able to parse a file to extract the localizable content, and after the content is translated, you should be able to generate a .resources.dll file that merges the translated content.</span></span> <span data-ttu-id="021ce-248">Toto téma neobsahuje všechny možné podrobnosti, ale nyní máte znalosti potřebné k použití LocBaml pro lokalizaci aplikací.</span><span class="sxs-lookup"><span data-stu-id="021ce-248">This topic does not include every possible detail, but you now have the knowledge necessary to use LocBaml for localizing your applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="021ce-249">Viz také</span><span class="sxs-lookup"><span data-stu-id="021ce-249">See also</span></span>

- [<span data-ttu-id="021ce-250">Globalizace pro WPF</span><span class="sxs-lookup"><span data-stu-id="021ce-250">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="021ce-251">Přehled automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="021ce-251">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
