---
title: 'Postupy: Lokalizace aplikace'
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83ed8ee8b8bfd9c3d6dadfedad8889af10a86466
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="344c4-102">Postupy: Lokalizace aplikace</span><span class="sxs-lookup"><span data-stu-id="344c4-102">How to: Localize an Application</span></span>
<span data-ttu-id="344c4-103">Tento kurz vysvětluje vytvoření lokalizované aplikace pomocí nástroje LocBaml.</span><span class="sxs-lookup"><span data-stu-id="344c4-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="344c4-104">Nástroj LocBaml není aplikace produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="344c4-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="344c4-105">Zobrazí se jako ukázku, která se využívá část lokalizace rozhraní API a ukazuje, jak může nástroj lokalizace zapsat.</span><span class="sxs-lookup"><span data-stu-id="344c4-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
<a name="Introduction"></a>   
## <a name="overview"></a><span data-ttu-id="344c4-106">Přehled</span><span class="sxs-lookup"><span data-stu-id="344c4-106">Overview</span></span>  
 <span data-ttu-id="344c4-107">Tato diskuse poskytuje podrobný postup k lokalizace aplikace.</span><span class="sxs-lookup"><span data-stu-id="344c4-107">This discussion gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="344c4-108">Nejprve připravte aplikaci tak, aby lze extrahovat text, který bude převeden.</span><span class="sxs-lookup"><span data-stu-id="344c4-108">First, you will prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="344c4-109">Po text přeloženy, bude sloučit přeložený text do novou kopii původní aplikace.</span><span class="sxs-lookup"><span data-stu-id="344c4-109">After the text is translated, you will merge the translated text into a new copy of the original application.</span></span>  
  
<a name="Requirements"></a>   
## <a name="requirements"></a><span data-ttu-id="344c4-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="344c4-110">Requirements</span></span>  
 <span data-ttu-id="344c4-111">V průběhu toto pojednání bude používat [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], což je kompilátoru, která se spouští z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="344c4-111">Over the course of this discussion, you will use [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], which is a compiler that runs from the command line.</span></span>  
  
 <span data-ttu-id="344c4-112">Také budete vyzváni k použít soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="344c4-112">Also, you will be instructed to use a project file.</span></span> <span data-ttu-id="344c4-113">Pokyny, jak používat [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] a soubory projektu, najdete v části [sestavení a nasazení](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md).</span><span class="sxs-lookup"><span data-stu-id="344c4-113">For instructions on how to use [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] and project files, see [Build and Deploy](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md).</span></span>  
  
 <span data-ttu-id="344c4-114">V příkladech v toto pojednání použít en US (angličtina-US) jako jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="344c4-114">All the examples in this discussion use en-US (English-US) as the culture.</span></span> <span data-ttu-id="344c4-115">To umožňuje pracovat provede příklady bez instalace v jiném jazyce.</span><span class="sxs-lookup"><span data-stu-id="344c4-115">This enables you to work through the steps of the examples without installing a different language.</span></span>  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a><span data-ttu-id="344c4-116">Vytvoření ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="344c4-116">Create a Sample Application</span></span>  
 <span data-ttu-id="344c4-117">V tomto kroku se připravíte aplikace pro lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="344c4-117">In this step, you will prepare your application for localization.</span></span> <span data-ttu-id="344c4-118">V [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ukázky HelloApp poskytnut vzorek, který se použije pro příklady kódu v toto pojednání.</span><span class="sxs-lookup"><span data-stu-id="344c4-118">In the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="344c4-119">Pokud chcete použít tuto ukázku, stáhněte si [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souborů z [ukázkový nástroj LocBaml](http://go.microsoft.com/fwlink/?LinkID=160016).</span><span class="sxs-lookup"><span data-stu-id="344c4-119">If you would like to use this sample, download the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] files from the [LocBaml Tool Sample](http://go.microsoft.com/fwlink/?LinkID=160016).</span></span>  
  
1.  <span data-ttu-id="344c4-120">Vývoj aplikace do bodu, kde chcete spustit lokalizace.</span><span class="sxs-lookup"><span data-stu-id="344c4-120">Develop your application to the point where you want to start localization.</span></span>  
  
2.  <span data-ttu-id="344c4-121">Zadejte jazyk vývoj v souboru projektu tak, aby [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] vygeneruje hlavní sestavení a satelitní sestavení (soubor s. rozšíření resources.dll) tak, aby obsahovala neutrální jazykové prostředky.</span><span class="sxs-lookup"><span data-stu-id="344c4-121">Specify the development language in the project file so that [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="344c4-122">Soubor projektu v ukázce HelloApp je HelloApp.csproj.</span><span class="sxs-lookup"><span data-stu-id="344c4-122">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="344c4-123">V tomto souboru zjistíte, vývoj jazyk identifikovat následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="344c4-123">In that file, you will find the development language identified as follows:</span></span>  
  
     `<UICulture>en-US</UICulture>`  
  
3.  <span data-ttu-id="344c4-124">Přidat UID k vaší [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory.</span><span class="sxs-lookup"><span data-stu-id="344c4-124">Add Uids to your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files.</span></span> <span data-ttu-id="344c4-125">UID se používají ke sledování změn souborů a k identifikaci položek, které se musí přeložit.</span><span class="sxs-lookup"><span data-stu-id="344c4-125">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="344c4-126">Chcete-li přidat UID vaše soubory, spusťte **updateuid** v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="344c4-126">To add Uids to your files, run **updateuid** on your project file:</span></span>  
  
     <span data-ttu-id="344c4-127">**helloapp.csproj /t:updateuid nástroje MSBuild**</span><span class="sxs-lookup"><span data-stu-id="344c4-127">**msbuild /t:updateuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="344c4-128">Pokud chcete ověřit, zda máte žádné chybějící nebo duplicitní UID, spusťte **checkuid**:</span><span class="sxs-lookup"><span data-stu-id="344c4-128">To verify that you have no missing or duplicate Uids, run **checkuid**:</span></span>  
  
     <span data-ttu-id="344c4-129">**helloapp.csproj /t:checkuid nástroje MSBuild**</span><span class="sxs-lookup"><span data-stu-id="344c4-129">**msbuild /t:checkuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="344c4-130">Po spuštění **updateuid**, vaše soubory by měly obsahovat UID.</span><span class="sxs-lookup"><span data-stu-id="344c4-130">After running **updateuid**, your files should contain Uids.</span></span> <span data-ttu-id="344c4-131">Například v souboru Pane1.xaml HelloApp, byste měli najít následující:</span><span class="sxs-lookup"><span data-stu-id="344c4-131">For example, in the Pane1.xaml file of HelloApp, you should find the following:</span></span>  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="344c4-132">Vytvořit neutrální jazyk prostředky satelitní sestavení</span><span class="sxs-lookup"><span data-stu-id="344c4-132">Create the Neutral Language Resources Satellite Assembly</span></span>  
 <span data-ttu-id="344c4-133">Po dokončení konfigurace aplikace k vygenerování satelitní sestavení prostředky neutrální jazyk, je sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="344c4-133">After the application is configured to generate a neutral language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="344c4-134">Tím se vytvoří sestavení hlavní aplikace, stejně jako neutrální jazyk prostředky satelitní sestavení, které vyžadují LocBaml pro lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="344c4-134">This generates the main application assembly, as well as the neutral language resources satellite assembly that is required by LocBaml for localization.</span></span> <span data-ttu-id="344c4-135">K vytvoření aplikace:</span><span class="sxs-lookup"><span data-stu-id="344c4-135">To build the application:</span></span>  
  
1.  <span data-ttu-id="344c4-136">Kompilace HelloApp k vytvoření [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="344c4-136">Compile HelloApp to create a [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:</span></span>  
  
     <span data-ttu-id="344c4-137">**helloapp.csproj nástroje MSBuild**</span><span class="sxs-lookup"><span data-stu-id="344c4-137">**msbuild helloapp.csproj**</span></span>  
  
2.  <span data-ttu-id="344c4-138">Nově vytvořená hlavní aplikace sestavení, HelloApp.exe, je vytvořen v následující složce:</span><span class="sxs-lookup"><span data-stu-id="344c4-138">The newly created main application assembly, HelloApp.exe, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\`  
  
3.  <span data-ttu-id="344c4-139">Vytváření satelitních sestavení prostředky nově vytvořený neutrální jazyk, HelloApp.resources.dll, v následující složce:</span><span class="sxs-lookup"><span data-stu-id="344c4-139">The newly created neutral language resources satellite assembly, HelloApp.resources.dll, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="344c4-140">Nástroj LocBaml sestavení</span><span class="sxs-lookup"><span data-stu-id="344c4-140">Build the LocBaml Tool</span></span>  
  
1.  <span data-ttu-id="344c4-141">Všechny soubory potřebné k vytvoření LocBaml jsou umístěny v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="344c4-141">All the files necessary to build LocBaml are located in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] samples.</span></span> <span data-ttu-id="344c4-142">Stažení [!INCLUDE[TLA#tla_lhcshrp](../../../../includes/tlasharptla-lhcshrp-md.md)] souborů z [ukázkový nástroj LocBaml](http://go.microsoft.com/fwlink/?LinkID=160016).</span><span class="sxs-lookup"><span data-stu-id="344c4-142">Download the [!INCLUDE[TLA#tla_lhcshrp](../../../../includes/tlasharptla-lhcshrp-md.md)] files from the [LocBaml Tool Sample](http://go.microsoft.com/fwlink/?LinkID=160016).</span></span>  
  
2.  <span data-ttu-id="344c4-143">Z příkazového řádku spusťte soubor projektu (locbaml.csproj) k vytvoření nástroje:</span><span class="sxs-lookup"><span data-stu-id="344c4-143">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  
  
     <span data-ttu-id="344c4-144">**locbaml.csproj nástroje MSBuild**</span><span class="sxs-lookup"><span data-stu-id="344c4-144">**msbuild locbaml.csproj**</span></span>  
  
3.  <span data-ttu-id="344c4-145">Přejděte do adresáře Bin\Release nově vytvořený spustitelný soubor (locbaml.exe).</span><span class="sxs-lookup"><span data-stu-id="344c4-145">Go to the Bin\Release directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="344c4-146">Example:C:\LocBaml\Bin\Release\locbaml.exe.</span><span class="sxs-lookup"><span data-stu-id="344c4-146">Example:C:\LocBaml\Bin\Release\locbaml.exe.</span></span>  
  
4.  <span data-ttu-id="344c4-147">Možnosti, které můžete zadat, když spustíte LocBaml jsou následující:</span><span class="sxs-lookup"><span data-stu-id="344c4-147">The options that you can specify when you run LocBaml are as follows:</span></span>  
  
    -   <span data-ttu-id="344c4-148">**analyzovat** nebo **-p:** analyzuje Baml prostředky, nebo [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] soubory můžete vytvořit soubor .csv nebo .txt.</span><span class="sxs-lookup"><span data-stu-id="344c4-148">**parse** or **-p:** Parses Baml, resources, or [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] files to generate a .csv or .txt file.</span></span>  
  
    -   <span data-ttu-id="344c4-149">**Generovat** nebo **-g:** generuje lokalizované binárního souboru pomocí přeložený souboru.</span><span class="sxs-lookup"><span data-stu-id="344c4-149">**generate** or **-g:** Generates a localized binary file by using a translated file.</span></span>  
  
    -   <span data-ttu-id="344c4-150">**out** nebo **-o** {*filedirectory*] **:** názvu výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="344c4-150">**out** or **-o** {*filedirectory*] **:** Output file name.</span></span>  
  
    -   <span data-ttu-id="344c4-151">**jazyková verze** nebo **- cul** {*jazykovou verzi*] **:** národního prostředí výstupu sestavení.</span><span class="sxs-lookup"><span data-stu-id="344c4-151">**culture** or **-cul** {*culture*] **:** Locale of output assemblies.</span></span>  
  
    -   <span data-ttu-id="344c4-152">**překlad** nebo **- napříč** {*translation.csv*] **:** překládané nebo lokalizované souboru.</span><span class="sxs-lookup"><span data-stu-id="344c4-152">**translation** or **-trans** {*translation.csv*] **:** Translated or localized file.</span></span>  
  
    -   <span data-ttu-id="344c4-153">**asmpath** nebo **- asmpath:** {*filedirectory*] **:** Pokud vaše [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kód obsahuje vlastní ovládací prvky, je nutné zadat  **asmpath** sestavení vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="344c4-153">**asmpath** or **-asmpath:** {*filedirectory*] **:** If your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code contains custom controls, you must supply the **asmpath** to the custom control assembly.</span></span>  
  
    -   <span data-ttu-id="344c4-154">**nologo:** zobrazí žádné logo nebo copyright informace.</span><span class="sxs-lookup"><span data-stu-id="344c4-154">**nologo:** Displays no logo or copyright information.</span></span>  
  
    -   <span data-ttu-id="344c4-155">**verbose:** zobrazí informace o podrobné režimu.</span><span class="sxs-lookup"><span data-stu-id="344c4-155">**verbose:** Displays verbose mode information.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="344c4-156">Pokud potřebujete seznam možností, pokud používáte nástroj, zadejte **LocBaml.exe** a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="344c4-156">If you need a list of the options when you are running the tool, type     **LocBaml.exe** and press ENTER.</span></span>  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="344c4-157">Použití LocBaml analyzovat soubor</span><span class="sxs-lookup"><span data-stu-id="344c4-157">Use LocBaml to Parse a File</span></span>  
 <span data-ttu-id="344c4-158">Teď, když jste vytvořili nástroj LocBaml, budete chtít použít k analýze HelloApp.resources.dll k extrahování obsahu text, který bude možné lokalizovat.</span><span class="sxs-lookup"><span data-stu-id="344c4-158">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1.  <span data-ttu-id="344c4-159">Zkopírujte LocBaml.exe do složky bin\debug vaší aplikace, které bylo vytvořeno sestavení hlavní aplikace.</span><span class="sxs-lookup"><span data-stu-id="344c4-159">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2.  <span data-ttu-id="344c4-160">Pokud chcete analyzovat soubor satelitní sestavení a uložit jako soubor CSV, použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="344c4-160">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
     <span data-ttu-id="344c4-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span><span class="sxs-lookup"><span data-stu-id="344c4-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="344c4-162">Pokud vstupní soubor HelloApp.resources.dll, není v přesunout do stejného adresáře jako LocBaml.exe jeden ze souborů tak, aby byly oba soubory ve stejném adresáři.</span><span class="sxs-lookup"><span data-stu-id="344c4-162">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3.  <span data-ttu-id="344c4-163">Při spuštění LocBaml analyzovat soubory výstup se skládá z sedm pole oddělený čárkami (.csv soubory) nebo karty (soubory s příponou .txt).</span><span class="sxs-lookup"><span data-stu-id="344c4-163">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="344c4-164">Na obrázku je soubor .csv Analyzovaná pro HelloApp.resources.dll:</span><span class="sxs-lookup"><span data-stu-id="344c4-164">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="344c4-165">HelloApp.g.en US.resources:window1.baml, Stack1:System.Windows.Controls.StackPanel. $Content, FALSE, FALSE,, ignorovat #Text1; #Text2;</span><span class="sxs-lookup"><span data-stu-id="344c4-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="344c4-166">HelloApp.g.en US.resources:window1.baml, Text1:System.Windows.Controls.TextBlock. $Content, None, nastavena hodnota TRUE, TRUE,, Hello World</span><span class="sxs-lookup"><span data-stu-id="344c4-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="344c4-167">HelloApp.g.en US.resources:window1.baml, Text2:System.Windows.Controls.TextBlock. $Content, None, TRUE, TRUE,, dát sbohem všem World</span><span class="sxs-lookup"><span data-stu-id="344c4-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="344c4-168">Pole sedm jsou:</span><span class="sxs-lookup"><span data-stu-id="344c4-168">The seven fields are:</span></span>  
  
   1.  <span data-ttu-id="344c4-169">**Název BAML**.</span><span class="sxs-lookup"><span data-stu-id="344c4-169">**BAML Name**.</span></span> <span data-ttu-id="344c4-170">Název prostředku BAML s ohledem na satelitní sestavení jazyka zdroje.</span><span class="sxs-lookup"><span data-stu-id="344c4-170">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   2.  <span data-ttu-id="344c4-171">**Klíč prostředku**.</span><span class="sxs-lookup"><span data-stu-id="344c4-171">**Resource Key**.</span></span> <span data-ttu-id="344c4-172">Identifikátor lokalizovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="344c4-172">The localized resource identifier.</span></span>  
  
   3.  <span data-ttu-id="344c4-173">**Kategorie**.</span><span class="sxs-lookup"><span data-stu-id="344c4-173">**Category**.</span></span> <span data-ttu-id="344c4-174">Typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="344c4-174">The value type.</span></span> <span data-ttu-id="344c4-175">V tématu [atributů lokalizace a komentáře](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="344c4-175">See [Localization Attributes and Comments](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span></span>  
  
   4.  <span data-ttu-id="344c4-176">**Čitelnost**.</span><span class="sxs-lookup"><span data-stu-id="344c4-176">**Readability**.</span></span> <span data-ttu-id="344c4-177">Hodnota zda mohou být přečteny lokalizátora.</span><span class="sxs-lookup"><span data-stu-id="344c4-177">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="344c4-178">V tématu [atributů lokalizace a komentáře](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="344c4-178">See [Localization Attributes and Comments](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span></span>  
  
   5.  <span data-ttu-id="344c4-179">**Modifiability**.</span><span class="sxs-lookup"><span data-stu-id="344c4-179">**Modifiability**.</span></span> <span data-ttu-id="344c4-180">Jestli může být hodnota upravit lokalizátora.</span><span class="sxs-lookup"><span data-stu-id="344c4-180">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="344c4-181">V tématu [atributů lokalizace a komentáře](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="344c4-181">See [Localization Attributes and Comments](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span></span>  
  
   6.  <span data-ttu-id="344c4-182">**Komentáře**.</span><span class="sxs-lookup"><span data-stu-id="344c4-182">**Comments**.</span></span> <span data-ttu-id="344c4-183">Další popis hodnoty, které vám pomohou určit, jak je lokalizované hodnotu.</span><span class="sxs-lookup"><span data-stu-id="344c4-183">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="344c4-184">V tématu [atributů lokalizace a komentáře](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="344c4-184">See [Localization Attributes and Comments](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span></span>  
  
   7.  <span data-ttu-id="344c4-185">**Hodnota**.</span><span class="sxs-lookup"><span data-stu-id="344c4-185">**Value**.</span></span> <span data-ttu-id="344c4-186">Textové hodnoty nepřeloží na požadovanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="344c4-186">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="344c4-187">Následující tabulka ukazuje, jak mapování těchto polí na hodnoty s oddělovači souboru CSV:</span><span class="sxs-lookup"><span data-stu-id="344c4-187">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="344c4-188">Název BAML</span><span class="sxs-lookup"><span data-stu-id="344c4-188">BAML name</span></span>|<span data-ttu-id="344c4-189">Klíč prostředku</span><span class="sxs-lookup"><span data-stu-id="344c4-189">Resource key</span></span>|<span data-ttu-id="344c4-190">Kategorie</span><span class="sxs-lookup"><span data-stu-id="344c4-190">Category</span></span>|<span data-ttu-id="344c4-191">Čitelnost</span><span class="sxs-lookup"><span data-stu-id="344c4-191">Readability</span></span>|<span data-ttu-id="344c4-192">Modifiability</span><span class="sxs-lookup"><span data-stu-id="344c4-192">Modifiability</span></span>|<span data-ttu-id="344c4-193">Komentáře</span><span class="sxs-lookup"><span data-stu-id="344c4-193">Comments</span></span>|<span data-ttu-id="344c4-194">Hodnota</span><span class="sxs-lookup"><span data-stu-id="344c4-194">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="344c4-195">HelloApp.g.en US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="344c4-195">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="344c4-196">Stack1:System.Windows.Controls.StackPanel.$Content</span><span class="sxs-lookup"><span data-stu-id="344c4-196">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="344c4-197">Ignorovat</span><span class="sxs-lookup"><span data-stu-id="344c4-197">Ignore</span></span>|<span data-ttu-id="344c4-198">FALSE</span><span class="sxs-lookup"><span data-stu-id="344c4-198">FALSE</span></span>|<span data-ttu-id="344c4-199">FALSE</span><span class="sxs-lookup"><span data-stu-id="344c4-199">FALSE</span></span>||<span data-ttu-id="344c4-200">#Text1; #Text2</span><span class="sxs-lookup"><span data-stu-id="344c4-200">#Text1;#Text2</span></span>|
   |<span data-ttu-id="344c4-201">HelloApp.g.en US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="344c4-201">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="344c4-202">Text1:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="344c4-202">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="344c4-203">Žádné</span><span class="sxs-lookup"><span data-stu-id="344c4-203">None</span></span>|<span data-ttu-id="344c4-204">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="344c4-204">TRUE</span></span>|<span data-ttu-id="344c4-205">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="344c4-205">TRUE</span></span>||<span data-ttu-id="344c4-206">Hello World</span><span class="sxs-lookup"><span data-stu-id="344c4-206">Hello World</span></span>|
   |<span data-ttu-id="344c4-207">HelloApp.g.en US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="344c4-207">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="344c4-208">Text2:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="344c4-208">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="344c4-209">Žádné</span><span class="sxs-lookup"><span data-stu-id="344c4-209">None</span></span>|<span data-ttu-id="344c4-210">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="344c4-210">TRUE</span></span>|<span data-ttu-id="344c4-211">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="344c4-211">TRUE</span></span>||<span data-ttu-id="344c4-212">Dát sbohem všem World</span><span class="sxs-lookup"><span data-stu-id="344c4-212">Goodbye World</span></span>|
  
   <span data-ttu-id="344c4-213">Všimněte si, že všechny hodnoty **komentáře** pole neobsahují žádné hodnoty; Pokud pole nemá hodnotu, je prázdný.</span><span class="sxs-lookup"><span data-stu-id="344c4-213">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="344c4-214">Všimněte si také že položky v prvním řádku není čitelný ani upravitelnými a že má "Ignorovat" jako jeho **kategorie** hodnotu, což znamená, že hodnota není lokalizovatelný.</span><span class="sxs-lookup"><span data-stu-id="344c4-214">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4.  <span data-ttu-id="344c4-215">K usnadnění zjišťování lokalizovatelný položek v analyzované soubory, zejména ve velkých souborech, můžete řazení nebo filtrovat položky dle **kategorie**, **čitelnost**, a **Modifiability**.</span><span class="sxs-lookup"><span data-stu-id="344c4-215">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="344c4-216">Například můžete odfiltrovat nečitelná a unmodifiable hodnoty.</span><span class="sxs-lookup"><span data-stu-id="344c4-216">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a><span data-ttu-id="344c4-217">Převede lokalizovatelný obsahu</span><span class="sxs-lookup"><span data-stu-id="344c4-217">Translate the Localizable Content</span></span>  
 <span data-ttu-id="344c4-218">Pomocí libovolného nástroje, která je k dispozici přeložit extrahovaného obsahu.</span><span class="sxs-lookup"><span data-stu-id="344c4-218">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="344c4-219">Dobrým způsobem, jak to udělat je napsat prostředky do CSV souborů a jejich zobrazením v [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], což překlad změní na poslední sloupec (hodnota).</span><span class="sxs-lookup"><span data-stu-id="344c4-219">A good way to do this is to write the resources to a .csv file and view them in [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], making translation changes to the last column (value).</span></span>  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="344c4-220">Můžete vygenerovat nový pomocí LocBaml. resources.dll souboru</span><span class="sxs-lookup"><span data-stu-id="344c4-220">Use LocBaml to Generate a New .resources.dll File</span></span>  
 <span data-ttu-id="344c4-221">Obsah, kterou identifikovalo analýza HelloApp.resources.dll s LocBaml byl přeložen a je potřeba sloučit zpět do původní aplikace.</span><span class="sxs-lookup"><span data-stu-id="344c4-221">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="344c4-222">Použití **generovat** nebo **-g** možnost k vygenerování nového. resources.dll souboru.</span><span class="sxs-lookup"><span data-stu-id="344c4-222">Use the **generate** or **-g** option to generate a new .resources.dll file.</span></span>  
  
1.  <span data-ttu-id="344c4-223">Pomocí následující syntaxe vygenerujte nový soubor HelloApp.resources.dll.</span><span class="sxs-lookup"><span data-stu-id="344c4-223">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="344c4-224">Označit jako en US jazykovou verzi (nebo cul:en-USA).</span><span class="sxs-lookup"><span data-stu-id="344c4-224">Mark the culture as en-US (/cul:en-US).</span></span>  
  
     <span data-ttu-id="344c4-225">**LocBaml.exe / generovat HelloApp.resources.dll /trans:Hello.csv /out:c: \ /cul:en-USA**</span><span class="sxs-lookup"><span data-stu-id="344c4-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="344c4-226">Pokud vstupní soubor Hello.csv, není ve stejném adresáři jako spustitelný soubor, LocBaml.exe, přesuňte jeden ze souborů tak, aby byly oba soubory ve stejném adresáři.</span><span class="sxs-lookup"><span data-stu-id="344c4-226">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2.  <span data-ttu-id="344c4-227">Nahraďte starý HelloApp.resources.dll soubor v adresáři C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll vaše nově vytvořený soubor HelloApp.resources.dll.</span><span class="sxs-lookup"><span data-stu-id="344c4-227">Replace the old HelloApp.resources.dll file in the C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll directory with your newly created HelloApp.resources.dll file.</span></span>  
  
3.  <span data-ttu-id="344c4-228">"Hello, World" a "Goodbye World" by měl nyní přeložený do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="344c4-228">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4.  <span data-ttu-id="344c4-229">Chcete-li převede na jinou jazykovou verzi, použijte jazyka, který se překladu pro jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="344c4-229">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="344c4-230">Následující příklad ukazuje, jak nepřeloží na French-Canadian:</span><span class="sxs-lookup"><span data-stu-id="344c4-230">The following example shows how to translate to French-Canadian:</span></span>  
  
     <span data-ttu-id="344c4-231">**LocBaml.exe / generovat HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c: \ /cul:fr-certifikační Autority**</span><span class="sxs-lookup"><span data-stu-id="344c4-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span></span>  
  
5.  <span data-ttu-id="344c4-232">Ve stejném sestavení jako sestavení hlavní aplikace vytvořte novou složku specifické pro jazykovou verzi pro uložení nové satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="344c4-232">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="344c4-233">Pro French-Canadian bude složka fr-CA.</span><span class="sxs-lookup"><span data-stu-id="344c4-233">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6.  <span data-ttu-id="344c4-234">Zkopírujte vygenerovaný satelitní sestavení do nové složky.</span><span class="sxs-lookup"><span data-stu-id="344c4-234">Copy the generated satellite assembly to the new folder.</span></span>  
  
7.  <span data-ttu-id="344c4-235">Pokud chcete vyzkoušet nové satelitní sestavení, potřebujete změnit jazykové verze, ve kterém aplikace poběží.</span><span class="sxs-lookup"><span data-stu-id="344c4-235">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="344c4-236">Toto lze provést jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="344c4-236">You can do this in one of two ways:</span></span>  
  
    -   <span data-ttu-id="344c4-237">Změnit místní nastavení operačního systému (**spustit** &#124; **Ovládací panely** &#124; **Místní a jazykové nastavení**).</span><span class="sxs-lookup"><span data-stu-id="344c4-237">Change your operating system's regional settings (**Start** &#124; **Control Panel** &#124; **Regional and Language Options**).</span></span>  
  
    -   <span data-ttu-id="344c4-238">V aplikaci přidejte následující kód do souboru App.xaml.cs:</span><span class="sxs-lookup"><span data-stu-id="344c4-238">In your application, add the following code to App.xaml.cs:</span></span>  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a><span data-ttu-id="344c4-239">Tipy pro používání LocBaml</span><span class="sxs-lookup"><span data-stu-id="344c4-239">Some Tips for Using LocBaml</span></span>  
  
-   <span data-ttu-id="344c4-240">Všechny závislé sestavení, které definují vlastní ovládací prvky, musí být zkopírován do místního adresáře LocBaml nebo nainstalovat do mezipaměti GAC.</span><span class="sxs-lookup"><span data-stu-id="344c4-240">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="344c4-241">To je nezbytné proto lokalizace rozhraní API musí mít přístup k závislá sestavení, při čtení [!INCLUDE[TLA#tla_baml](../../../../includes/tlasharptla-baml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="344c4-241">This is necessary because the localization API must have access to the dependent assemblies when it reads the [!INCLUDE[TLA#tla_baml](../../../../includes/tlasharptla-baml-md.md)].</span></span>  
  
-   <span data-ttu-id="344c4-242">Pokud hlavní sestavení je podepsaný, musí v pořadí pro něj má být načten podepsané generovaného DLL prostředků.</span><span class="sxs-lookup"><span data-stu-id="344c4-242">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
-   <span data-ttu-id="344c4-243">Verze lokalizovaný prostředek DLL musí být synchronizovány s hlavní sestavení.</span><span class="sxs-lookup"><span data-stu-id="344c4-243">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a><span data-ttu-id="344c4-244">Co je další</span><span class="sxs-lookup"><span data-stu-id="344c4-244">What's Next</span></span>  
 <span data-ttu-id="344c4-245">Teď byste měli mít základní znalosti o tom, jak používat nástroj LocBaml.</span><span class="sxs-lookup"><span data-stu-id="344c4-245">You should now have a basic understanding of how to use the LocBaml tool.</span></span>  <span data-ttu-id="344c4-246">Byste měli mít zkontrolujte soubor, který obsahuje UID.</span><span class="sxs-lookup"><span data-stu-id="344c4-246">You should be able to make a file that contains Uids.</span></span> <span data-ttu-id="344c4-247">Pomocí nástroje LocBaml by měl být schopen analyzovat soubor k extrahování obsahu lokalizovatelný a po obsah přeloženy, byste měli dokáže generovat. resources.dll soubor, který sloučí přeložený obsah.</span><span class="sxs-lookup"><span data-stu-id="344c4-247">By using the LocBaml tool, you should be able to parse a file to extract the localizable content, and after the content is translated, you should be able to generate a .resources.dll file that merges the translated content.</span></span> <span data-ttu-id="344c4-248">Toto téma neobsahuje všechny možné podrobností, ale Teď máte znalosti nezbytných k používání LocBaml pro lokalizace aplikací.</span><span class="sxs-lookup"><span data-stu-id="344c4-248">This topic does not include every possible detail, but you now have the knowledge necessary to use LocBaml for localizing your applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="344c4-249">Viz také</span><span class="sxs-lookup"><span data-stu-id="344c4-249">See Also</span></span>  
 [<span data-ttu-id="344c4-250">Globalizace pro WPF</span><span class="sxs-lookup"><span data-stu-id="344c4-250">Globalization for WPF</span></span>](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [<span data-ttu-id="344c4-251">Přehled automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="344c4-251">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)
