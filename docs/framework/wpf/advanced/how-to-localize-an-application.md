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
ms.openlocfilehash: d08f991204b2d74899cbd1aee82c0cc23e175dd4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59298315"
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="87f4f-102">Postupy: Lokalizace aplikace</span><span class="sxs-lookup"><span data-stu-id="87f4f-102">How to: Localize an Application</span></span>
<span data-ttu-id="87f4f-103">Tento kurz vysvětluje vytvoření lokalizované aplikace s použitím locbaml – nástroj.</span><span class="sxs-lookup"><span data-stu-id="87f4f-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87f4f-104">Locbaml – nástroj není aplikace připravené pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="87f4f-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="87f4f-105">Zobrazí se jako ukázka, která používá některé lokalizace rozhraní API a ukazuje, jak můžete například napsat lokalizační nástroj.</span><span class="sxs-lookup"><span data-stu-id="87f4f-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
<a name="Introduction"></a>   
## <a name="overview"></a><span data-ttu-id="87f4f-106">Přehled</span><span class="sxs-lookup"><span data-stu-id="87f4f-106">Overview</span></span>  
 <span data-ttu-id="87f4f-107">Tato diskuse poskytuje podrobný postup k lokalizace aplikace.</span><span class="sxs-lookup"><span data-stu-id="87f4f-107">This discussion gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="87f4f-108">Nejprve se připravte aplikaci tak, aby může být extrahována text, který bude fungovat.</span><span class="sxs-lookup"><span data-stu-id="87f4f-108">First, you will prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="87f4f-109">Poté, co je přeložen text, sloučí přeložený text do novou kopii původní aplikace.</span><span class="sxs-lookup"><span data-stu-id="87f4f-109">After the text is translated, you will merge the translated text into a new copy of the original application.</span></span>  
  
<a name="Requirements"></a>   
## <a name="requirements"></a><span data-ttu-id="87f4f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87f4f-110">Requirements</span></span>  
 <span data-ttu-id="87f4f-111">V průběhu této diskuse, budete používat [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], což je kompilátor, který se spustí z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="87f4f-111">Over the course of this discussion, you will use [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], which is a compiler that runs from the command line.</span></span>  
  
 <span data-ttu-id="87f4f-112">Navíc vám bude nastaven na použití souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="87f4f-112">Also, you will be instructed to use a project file.</span></span> <span data-ttu-id="87f4f-113">Pokyny k používání [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] a soubory projektu, přečtěte si [sestavovat a nasazovat](../app-development/building-and-deploying-wpf-applications.md).</span><span class="sxs-lookup"><span data-stu-id="87f4f-113">For instructions on how to use [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] and project files, see [Build and Deploy](../app-development/building-and-deploying-wpf-applications.md).</span></span>  
  
 <span data-ttu-id="87f4f-114">Všechny příklady v této diskuzi použít jako jazykové verze en US (angličtina-USA).</span><span class="sxs-lookup"><span data-stu-id="87f4f-114">All the examples in this discussion use en-US (English-US) as the culture.</span></span> <span data-ttu-id="87f4f-115">To umožňuje seznámení se základními kroky příklady bez instalace jiný jazyk.</span><span class="sxs-lookup"><span data-stu-id="87f4f-115">This enables you to work through the steps of the examples without installing a different language.</span></span>  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a><span data-ttu-id="87f4f-116">Vytvoření ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="87f4f-116">Create a Sample Application</span></span>  
 <span data-ttu-id="87f4f-117">V tomto kroku se připravíte aplikace pro lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="87f4f-117">In this step, you will prepare your application for localization.</span></span> <span data-ttu-id="87f4f-118">V [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ukázky HelloApp ukázky pochází, který se použije pro příklady v této diskuzi.</span><span class="sxs-lookup"><span data-stu-id="87f4f-118">In the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="87f4f-119">Pokud chcete tuto ukázku použít, stáhněte si [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souborů z doručené pošty [locbaml – nástroj ukázka](https://go.microsoft.com/fwlink/?LinkID=160016).</span><span class="sxs-lookup"><span data-stu-id="87f4f-119">If you would like to use this sample, download the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] files from the [LocBaml Tool Sample](https://go.microsoft.com/fwlink/?LinkID=160016).</span></span>  
  
1. <span data-ttu-id="87f4f-120">Vývoj vaší aplikace do bodu, ve kterém chcete spustit lokalizace.</span><span class="sxs-lookup"><span data-stu-id="87f4f-120">Develop your application to the point where you want to start localization.</span></span>  
  
2. <span data-ttu-id="87f4f-121">Zadejte jazyk pro vývoj v souboru projektu tak, aby [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] generuje do hlavního sestavení a satelitní sestavení (soubor s. resources.dll rozšíření) tak, aby obsahovala neutrální jazyk prostředků.</span><span class="sxs-lookup"><span data-stu-id="87f4f-121">Specify the development language in the project file so that [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="87f4f-122">Soubor projektu v ukázce HelloApp je HelloApp.csproj.</span><span class="sxs-lookup"><span data-stu-id="87f4f-122">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="87f4f-123">V tomto souboru najdete vývojový jazyk identifikována takto:</span><span class="sxs-lookup"><span data-stu-id="87f4f-123">In that file, you will find the development language identified as follows:</span></span>  
  
     `<UICulture>en-US</UICulture>`  
  
3. <span data-ttu-id="87f4f-124">Přidat identifikátory UID byly pro vaši [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory.</span><span class="sxs-lookup"><span data-stu-id="87f4f-124">Add Uids to your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files.</span></span> <span data-ttu-id="87f4f-125">Identifikátory UID byly se používají ke sledování změn souborů a k identifikaci položky, které se musí přeložit.</span><span class="sxs-lookup"><span data-stu-id="87f4f-125">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="87f4f-126">Chcete-li přidat identifikátory UID byly k souborům, spusťte **updateuid** v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="87f4f-126">To add Uids to your files, run **updateuid** on your project file:</span></span>  
  
     <span data-ttu-id="87f4f-127">**MSBuild – t: updateuid helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="87f4f-127">**msbuild -t:updateuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="87f4f-128">Chcete-li ověřit, zda máte žádné chybějící nebo duplicitní identifikátory UID, spusťte **checkuid**:</span><span class="sxs-lookup"><span data-stu-id="87f4f-128">To verify that you have no missing or duplicate Uids, run **checkuid**:</span></span>  
  
     <span data-ttu-id="87f4f-129">**MSBuild – t: checkuid helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="87f4f-129">**msbuild -t:checkuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="87f4f-130">Po spuštění **updateuid**, vaše soubory by měly obsahovat identifikátory UID.</span><span class="sxs-lookup"><span data-stu-id="87f4f-130">After running **updateuid**, your files should contain Uids.</span></span> <span data-ttu-id="87f4f-131">Například v souboru Pane1.xaml HelloApp byste měli najít následující:</span><span class="sxs-lookup"><span data-stu-id="87f4f-131">For example, in the Pane1.xaml file of HelloApp, you should find the following:</span></span>  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="87f4f-132">Vytvořit satelitní sestavení prostředků neutrální jazyk</span><span class="sxs-lookup"><span data-stu-id="87f4f-132">Create the Neutral Language Resources Satellite Assembly</span></span>  
 <span data-ttu-id="87f4f-133">Po aplikaci bylo nakonfigurováno pro generování satelitního sestavení neutrální jazyk prostředků, sestavte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="87f4f-133">After the application is configured to generate a neutral language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="87f4f-134">Tím se vytvoří sestavení hlavní aplikace, stejně jako neutrální jazyk prostředků satelitní sestavení, který vyžaduje locbaml – pro lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="87f4f-134">This generates the main application assembly, as well as the neutral language resources satellite assembly that is required by LocBaml for localization.</span></span> <span data-ttu-id="87f4f-135">K sestavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="87f4f-135">To build the application:</span></span>  
  
1. <span data-ttu-id="87f4f-136">Kompilace HelloApp k vytvoření [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="87f4f-136">Compile HelloApp to create a [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:</span></span>  
  
     <span data-ttu-id="87f4f-137">**MSBuild helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="87f4f-137">**msbuild helloapp.csproj**</span></span>  
  
2. <span data-ttu-id="87f4f-138">Sestavení nově vytvořeného hlavní aplikace HelloApp.exe, se vytvoří v následující složce:</span><span class="sxs-lookup"><span data-stu-id="87f4f-138">The newly created main application assembly, HelloApp.exe, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. <span data-ttu-id="87f4f-139">Satelitní sestavení nově vytvořeného neutrální jazyk prostředků, HelloApp.resources.dll, se vytvoří v následující složce:</span><span class="sxs-lookup"><span data-stu-id="87f4f-139">The newly created neutral language resources satellite assembly, HelloApp.resources.dll, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="87f4f-140">Sestavení locbaml – nástroj</span><span class="sxs-lookup"><span data-stu-id="87f4f-140">Build the LocBaml Tool</span></span>  
  
1. <span data-ttu-id="87f4f-141">Všechny soubory potřebné k vývoji locbaml – jsou umístěny v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="87f4f-141">All the files necessary to build LocBaml are located in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] samples.</span></span> <span data-ttu-id="87f4f-142">Stáhnout soubory jazyka C# z [locbaml – nástroj ukázka](https://go.microsoft.com/fwlink/?LinkID=160016).</span><span class="sxs-lookup"><span data-stu-id="87f4f-142">Download the C# files from the [LocBaml Tool Sample](https://go.microsoft.com/fwlink/?LinkID=160016).</span></span>  
  
2. <span data-ttu-id="87f4f-143">Z příkazového řádku spusťte soubor projektu (locbaml.csproj) pro sestavení nástroje:</span><span class="sxs-lookup"><span data-stu-id="87f4f-143">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  
  
     <span data-ttu-id="87f4f-144">**MSBuild locbaml.csproj**</span><span class="sxs-lookup"><span data-stu-id="87f4f-144">**msbuild locbaml.csproj**</span></span>  
  
3. <span data-ttu-id="87f4f-145">Přejděte do adresáře Bin\Release nově vytvořený spustitelný soubor (locbaml.exe) se nenašel.</span><span class="sxs-lookup"><span data-stu-id="87f4f-145">Go to the Bin\Release directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="87f4f-146">Example:C:\LocBaml\Bin\Release\locbaml.exe.</span><span class="sxs-lookup"><span data-stu-id="87f4f-146">Example:C:\LocBaml\Bin\Release\locbaml.exe.</span></span>  
  
4. <span data-ttu-id="87f4f-147">Možnosti, které můžete zadat při spuštění locbaml – jsou následující:</span><span class="sxs-lookup"><span data-stu-id="87f4f-147">The options that you can specify when you run LocBaml are as follows:</span></span>  
  
    -   <span data-ttu-id="87f4f-148">**analyzovat** nebo **-p:** Analyzuje Baml, prostředky, nebo [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] soubory vygenerovat soubor CSV nebo .txt.</span><span class="sxs-lookup"><span data-stu-id="87f4f-148">**parse** or **-p:** Parses Baml, resources, or [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] files to generate a .csv or .txt file.</span></span>  
  
    -   <span data-ttu-id="87f4f-149">**Generovat** nebo **-k:** Generuje lokalizované binární soubor s použitím přeložený soubor.</span><span class="sxs-lookup"><span data-stu-id="87f4f-149">**generate** or **-g:** Generates a localized binary file by using a translated file.</span></span>  
  
    -   <span data-ttu-id="87f4f-150">**navýšení kapacity** nebo **-o** {*filedirectory*] **:** Název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="87f4f-150">**out** or **-o** {*filedirectory*] **:** Output file name.</span></span>  
  
    -   <span data-ttu-id="87f4f-151">**jazyková verze** nebo **- cul** {*jazykovou verzi*] **:** Národní prostředí z výstupu sestavení.</span><span class="sxs-lookup"><span data-stu-id="87f4f-151">**culture** or **-cul** {*culture*] **:** Locale of output assemblies.</span></span>  
  
    -   <span data-ttu-id="87f4f-152">**překlad** nebo **- trans** {*translation.csv*] **:** Přeložené nebo lokalizovaný soubor.</span><span class="sxs-lookup"><span data-stu-id="87f4f-152">**translation** or **-trans** {*translation.csv*] **:** Translated or localized file.</span></span>  
  
    -   <span data-ttu-id="87f4f-153">**asmpath** nebo **- asmpath:** {*filedirectory*] **:** Pokud vaše [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kód obsahuje vlastní ovládací prvky, je nutné zadat **asmpath** sestavení vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="87f4f-153">**asmpath** or **-asmpath:** {*filedirectory*] **:** If your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code contains custom controls, you must supply the **asmpath** to the custom control assembly.</span></span>  
  
    -   <span data-ttu-id="87f4f-154">**nologo:** Zobrazuje informace bez logo nebo autorských práv.</span><span class="sxs-lookup"><span data-stu-id="87f4f-154">**nologo:** Displays no logo or copyright information.</span></span>  
  
    -   <span data-ttu-id="87f4f-155">**verbose:** Zobrazí informace o režimu s komentářem.</span><span class="sxs-lookup"><span data-stu-id="87f4f-155">**verbose:** Displays verbose mode information.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="87f4f-156">Pokud potřebujete seznam možností, pokud spouštíte nástroj, zadejte **LocBaml.exe** a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="87f4f-156">If you need a list of the options when you are running the tool, type     **LocBaml.exe** and press ENTER.</span></span>  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="87f4f-157">Locbaml – použít k analýze souboru</span><span class="sxs-lookup"><span data-stu-id="87f4f-157">Use LocBaml to Parse a File</span></span>  
 <span data-ttu-id="87f4f-158">Teď, když jste vytvořili locbaml – nástroj, budete chtít použít k analýze HelloApp.resources.dll extrahování textového obsahu, který bude lokalizovaný.</span><span class="sxs-lookup"><span data-stu-id="87f4f-158">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1. <span data-ttu-id="87f4f-159">Zkopírujte LocBaml.exe bin\debug složky vaší aplikace, kde byl vytvořen sestavení hlavní aplikace.</span><span class="sxs-lookup"><span data-stu-id="87f4f-159">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2. <span data-ttu-id="87f4f-160">K analýze souboru satelitní sestavení a výstup uložit jako soubor .csv, použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="87f4f-160">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
     <span data-ttu-id="87f4f-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span><span class="sxs-lookup"><span data-stu-id="87f4f-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="87f4f-162">Pokud vstupní soubor HelloApp.resources.dll, není v přesunout do stejného adresáře jako LocBaml.exe jeden ze souborů tak, že oba soubory jsou ve stejném adresáři.</span><span class="sxs-lookup"><span data-stu-id="87f4f-162">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3. <span data-ttu-id="87f4f-163">Když spustíte locbaml – analyzovat soubory, výstup se skládá z sedm polí oddělených čárkami (CSV soubory) nebo karty (soubory s příponou .txt).</span><span class="sxs-lookup"><span data-stu-id="87f4f-163">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="87f4f-164">Následuje ukázka soubor .csv analyzovanou klauzuli pro HelloApp.resources.dll:</span><span class="sxs-lookup"><span data-stu-id="87f4f-164">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="87f4f-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span><span class="sxs-lookup"><span data-stu-id="87f4f-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="87f4f-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span><span class="sxs-lookup"><span data-stu-id="87f4f-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="87f4f-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span><span class="sxs-lookup"><span data-stu-id="87f4f-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="87f4f-168">Sedm pole jsou:</span><span class="sxs-lookup"><span data-stu-id="87f4f-168">The seven fields are:</span></span>  
  
   1.  <span data-ttu-id="87f4f-169">**Název BAML**.</span><span class="sxs-lookup"><span data-stu-id="87f4f-169">**BAML Name**.</span></span> <span data-ttu-id="87f4f-170">Název prostředku BAML s ohledem na zdrojový jazyk satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="87f4f-170">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   2.  <span data-ttu-id="87f4f-171">**Klíč prostředku**.</span><span class="sxs-lookup"><span data-stu-id="87f4f-171">**Resource Key**.</span></span> <span data-ttu-id="87f4f-172">Identifikátor lokalizovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="87f4f-172">The localized resource identifier.</span></span>  
  
   3.  <span data-ttu-id="87f4f-173">**Kategorie**.</span><span class="sxs-lookup"><span data-stu-id="87f4f-173">**Category**.</span></span> <span data-ttu-id="87f4f-174">Typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="87f4f-174">The value type.</span></span> <span data-ttu-id="87f4f-175">Zobrazit [atributy a komentáře lokalizace](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="87f4f-175">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   4.  <span data-ttu-id="87f4f-176">**Lepší čitelnost**.</span><span class="sxs-lookup"><span data-stu-id="87f4f-176">**Readability**.</span></span> <span data-ttu-id="87f4f-177">Hodnota určuje, zda mohou být přečteny lokalizátora.</span><span class="sxs-lookup"><span data-stu-id="87f4f-177">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="87f4f-178">Zobrazit [atributy a komentáře lokalizace](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="87f4f-178">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   5.  <span data-ttu-id="87f4f-179">**Modifiability**.</span><span class="sxs-lookup"><span data-stu-id="87f4f-179">**Modifiability**.</span></span> <span data-ttu-id="87f4f-180">Určuje, zda můžete změnit hodnotu lokalizátora.</span><span class="sxs-lookup"><span data-stu-id="87f4f-180">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="87f4f-181">Zobrazit [atributy a komentáře lokalizace](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="87f4f-181">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   6.  <span data-ttu-id="87f4f-182">**Komentáře**.</span><span class="sxs-lookup"><span data-stu-id="87f4f-182">**Comments**.</span></span> <span data-ttu-id="87f4f-183">Další popis hodnotu sloužící k určení, jak je lokalizován hodnotu.</span><span class="sxs-lookup"><span data-stu-id="87f4f-183">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="87f4f-184">Zobrazit [atributy a komentáře lokalizace](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="87f4f-184">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   7.  <span data-ttu-id="87f4f-185">**Hodnota**.</span><span class="sxs-lookup"><span data-stu-id="87f4f-185">**Value**.</span></span> <span data-ttu-id="87f4f-186">Textová hodnota pro převod na požadovanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="87f4f-186">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="87f4f-187">Následující tabulka ukazuje, jak tato pole se mapují na hodnoty s oddělovači souboru CSV:</span><span class="sxs-lookup"><span data-stu-id="87f4f-187">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="87f4f-188">Název BAML</span><span class="sxs-lookup"><span data-stu-id="87f4f-188">BAML name</span></span>|<span data-ttu-id="87f4f-189">Klíč prostředku</span><span class="sxs-lookup"><span data-stu-id="87f4f-189">Resource key</span></span>|<span data-ttu-id="87f4f-190">Kategorie</span><span class="sxs-lookup"><span data-stu-id="87f4f-190">Category</span></span>|<span data-ttu-id="87f4f-191">Lepší čitelnost</span><span class="sxs-lookup"><span data-stu-id="87f4f-191">Readability</span></span>|<span data-ttu-id="87f4f-192">Modifiability</span><span class="sxs-lookup"><span data-stu-id="87f4f-192">Modifiability</span></span>|<span data-ttu-id="87f4f-193">Komentáře</span><span class="sxs-lookup"><span data-stu-id="87f4f-193">Comments</span></span>|<span data-ttu-id="87f4f-194">Value</span><span class="sxs-lookup"><span data-stu-id="87f4f-194">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="87f4f-195">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="87f4f-195">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="87f4f-196">Stack1:System.Windows.Controls.StackPanel.$Content</span><span class="sxs-lookup"><span data-stu-id="87f4f-196">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="87f4f-197">Ignorovat</span><span class="sxs-lookup"><span data-stu-id="87f4f-197">Ignore</span></span>|<span data-ttu-id="87f4f-198">FALSE</span><span class="sxs-lookup"><span data-stu-id="87f4f-198">FALSE</span></span>|<span data-ttu-id="87f4f-199">FALSE</span><span class="sxs-lookup"><span data-stu-id="87f4f-199">FALSE</span></span>||<span data-ttu-id="87f4f-200">#Text1;#Text2</span><span class="sxs-lookup"><span data-stu-id="87f4f-200">#Text1;#Text2</span></span>|
   |<span data-ttu-id="87f4f-201">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="87f4f-201">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="87f4f-202">Text1:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="87f4f-202">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="87f4f-203">Žádné</span><span class="sxs-lookup"><span data-stu-id="87f4f-203">None</span></span>|<span data-ttu-id="87f4f-204">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="87f4f-204">TRUE</span></span>|<span data-ttu-id="87f4f-205">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="87f4f-205">TRUE</span></span>||<span data-ttu-id="87f4f-206">Hello World</span><span class="sxs-lookup"><span data-stu-id="87f4f-206">Hello World</span></span>|
   |<span data-ttu-id="87f4f-207">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="87f4f-207">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="87f4f-208">Text2:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="87f4f-208">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="87f4f-209">Žádný</span><span class="sxs-lookup"><span data-stu-id="87f4f-209">None</span></span>|<span data-ttu-id="87f4f-210">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="87f4f-210">TRUE</span></span>|<span data-ttu-id="87f4f-211">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="87f4f-211">TRUE</span></span>||<span data-ttu-id="87f4f-212">Goodbye World</span><span class="sxs-lookup"><span data-stu-id="87f4f-212">Goodbye World</span></span>|
  
   <span data-ttu-id="87f4f-213">Všimněte si, že všechny hodnoty **komentáře** pole neobsahují žádné hodnoty; Pokud pole nemá hodnotu, je prázdný.</span><span class="sxs-lookup"><span data-stu-id="87f4f-213">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="87f4f-214">Všimněte si také, že položka v prvním řádku není ani čitelná ani měnit a má "Ignorovat" jako jeho **kategorie** hodnoty, které označuje, že hodnota není lokalizovatelné.</span><span class="sxs-lookup"><span data-stu-id="87f4f-214">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4. <span data-ttu-id="87f4f-215">Aby se usnadnilo zjišťování lokalizovatelné položek v analyzované soubory, zejména ve velkých souborech si seřadíte nebo vyfiltrujete položky podle **kategorie**, **čitelnost**, a **Modifiability**.</span><span class="sxs-lookup"><span data-stu-id="87f4f-215">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="87f4f-216">Můžete například vyfiltrovat hodnoty nejde přečíst a neupravitelných.</span><span class="sxs-lookup"><span data-stu-id="87f4f-216">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a><span data-ttu-id="87f4f-217">Přeložit lokalizovatelné obsahu</span><span class="sxs-lookup"><span data-stu-id="87f4f-217">Translate the Localizable Content</span></span>  
 <span data-ttu-id="87f4f-218">Použijte jakýkoli nástroj, že máte k dispozici pro převod extrahovaného obsahu.</span><span class="sxs-lookup"><span data-stu-id="87f4f-218">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="87f4f-219">Je dobrým způsobem, jak to provést pro zápis souboru prostředky, které soubor .csv a zobrazit v [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], aby překlad změní na poslední sloupec (hodnota).</span><span class="sxs-lookup"><span data-stu-id="87f4f-219">A good way to do this is to write the resources to a .csv file and view them in [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], making translation changes to the last column (value).</span></span>  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="87f4f-220">Locbaml – použít ke generování nové. resources.dll souboru</span><span class="sxs-lookup"><span data-stu-id="87f4f-220">Use LocBaml to Generate a New .resources.dll File</span></span>  
 <span data-ttu-id="87f4f-221">Obsah, který byl identifikován analýzou HelloApp.resources.dll s locbaml – byl přeložen a musí být sloučeny zpět do původní aplikace.</span><span class="sxs-lookup"><span data-stu-id="87f4f-221">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="87f4f-222">Použití **generovat** nebo **-g** možnost k vygenerování nového. resources.dll souboru.</span><span class="sxs-lookup"><span data-stu-id="87f4f-222">Use the **generate** or **-g** option to generate a new .resources.dll file.</span></span>  
  
1. <span data-ttu-id="87f4f-223">Použijte následující syntaxi pro vytvoření nového souboru HelloApp.resources.dll.</span><span class="sxs-lookup"><span data-stu-id="87f4f-223">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="87f4f-224">Označit jazykovou verzi jako en US (/ cul:en-US).</span><span class="sxs-lookup"><span data-stu-id="87f4f-224">Mark the culture as en-US (/cul:en-US).</span></span>  
  
     <span data-ttu-id="87f4f-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span><span class="sxs-lookup"><span data-stu-id="87f4f-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="87f4f-226">Pokud vstupní soubor Hello.csv, není ve stejném adresáři jako spustitelný soubor, LocBaml.exe, přesuňte jeden ze souborů tak, že oba soubory jsou ve stejném adresáři.</span><span class="sxs-lookup"><span data-stu-id="87f4f-226">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2. <span data-ttu-id="87f4f-227">Nahraďte původní soubor v adresáři C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll HelloApp.resources.dll váš nově vytvořený soubor HelloApp.resources.dll.</span><span class="sxs-lookup"><span data-stu-id="87f4f-227">Replace the old HelloApp.resources.dll file in the C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll directory with your newly created HelloApp.resources.dll file.</span></span>  
  
3. <span data-ttu-id="87f4f-228">"Hello World" a "Goodbye World" by měl nyní přeložený do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="87f4f-228">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4. <span data-ttu-id="87f4f-229">Pro převod na jinou jazykovou verzi, pomocí jazyka, který se překládá na jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="87f4f-229">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="87f4f-230">Následující příklad ukazuje, jak převést French-Canadian:</span><span class="sxs-lookup"><span data-stu-id="87f4f-230">The following example shows how to translate to French-Canadian:</span></span>  
  
     <span data-ttu-id="87f4f-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span><span class="sxs-lookup"><span data-stu-id="87f4f-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span></span>  
  
5. <span data-ttu-id="87f4f-232">Ve stejném sestavení jako sestavení hlavní aplikace vytvořte novou složku specifické pro jazykovou verzi k umístění nového satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="87f4f-232">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="87f4f-233">U French-Canadian bude složka fr-CA.</span><span class="sxs-lookup"><span data-stu-id="87f4f-233">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6. <span data-ttu-id="87f4f-234">Zkopírujte do nové složky generovaných satelitních sestavení.</span><span class="sxs-lookup"><span data-stu-id="87f4f-234">Copy the generated satellite assembly to the new folder.</span></span>  
  
7. <span data-ttu-id="87f4f-235">Otestovat nové satelitní sestavení, budete muset změnit jazykové verze, ve kterém aplikace poběží.</span><span class="sxs-lookup"><span data-stu-id="87f4f-235">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="87f4f-236">Toto lze provést jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="87f4f-236">You can do this in one of two ways:</span></span>  
  
    -   <span data-ttu-id="87f4f-237">Změnit místní nastavení operačního systému (**Start** &#124; **ovládací panely** &#124; **místní a jazykové nastavení**).</span><span class="sxs-lookup"><span data-stu-id="87f4f-237">Change your operating system's regional settings (**Start** &#124; **Control Panel** &#124; **Regional and Language Options**).</span></span>  
  
    -   <span data-ttu-id="87f4f-238">Ve vaší aplikaci přidejte následující kód do souboru App.xaml.cs:</span><span class="sxs-lookup"><span data-stu-id="87f4f-238">In your application, add the following code to App.xaml.cs:</span></span>  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a><span data-ttu-id="87f4f-239">Některé tipy pro používání locbaml –</span><span class="sxs-lookup"><span data-stu-id="87f4f-239">Some Tips for Using LocBaml</span></span>  
  
-   <span data-ttu-id="87f4f-240">Všechna závislá sestavení, definující vlastní ovládací prvky musí být zkopírován do místního adresáře locbaml – nebo instaluje se do mezipaměti GAC.</span><span class="sxs-lookup"><span data-stu-id="87f4f-240">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="87f4f-241">To je nezbytné, protože lokalizace rozhraní API musí mít přístup k závislé sestavení při čtení [!INCLUDE[TLA#tla_baml](../../../../includes/tlasharptla-baml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="87f4f-241">This is necessary because the localization API must have access to the dependent assemblies when it reads the [!INCLUDE[TLA#tla_baml](../../../../includes/tlasharptla-baml-md.md)].</span></span>  
  
-   <span data-ttu-id="87f4f-242">Pokud hlavní sestavení je podepsáno, musí být vygenerovaný knihovna DLL prostředků podepsané také v pořadí, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="87f4f-242">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
-   <span data-ttu-id="87f4f-243">Verze lokalizovaný prostředek knihovny DLL musí být synchronizovány s hlavním sestavením.</span><span class="sxs-lookup"><span data-stu-id="87f4f-243">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a><span data-ttu-id="87f4f-244">Co se chystá</span><span class="sxs-lookup"><span data-stu-id="87f4f-244">What's Next</span></span>  
 <span data-ttu-id="87f4f-245">Nyní byste měli mít základní znalosti o tom, jak používat locbaml – nástroj.</span><span class="sxs-lookup"><span data-stu-id="87f4f-245">You should now have a basic understanding of how to use the LocBaml tool.</span></span>  <span data-ttu-id="87f4f-246">Můžete by měl být schopen provést soubor obsahující identifikátory UID.</span><span class="sxs-lookup"><span data-stu-id="87f4f-246">You should be able to make a file that contains Uids.</span></span> <span data-ttu-id="87f4f-247">S použitím locbaml – nástroj, byste měli analyzovat soubor, který chcete extrahovat lokalizovatelné obsah a po obsahu se kombinují, by měla být schopna generovat. resources.dll soubor, který sloučí přeloženého obsahu.</span><span class="sxs-lookup"><span data-stu-id="87f4f-247">By using the LocBaml tool, you should be able to parse a file to extract the localizable content, and after the content is translated, you should be able to generate a .resources.dll file that merges the translated content.</span></span> <span data-ttu-id="87f4f-248">Toto téma neobsahuje všechny možné podrobnosti, ale Teď máte znalosti, které jsou nezbytné pro účely locbaml – lokalizace vašich aplikací.</span><span class="sxs-lookup"><span data-stu-id="87f4f-248">This topic does not include every possible detail, but you now have the knowledge necessary to use LocBaml for localizing your applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87f4f-249">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87f4f-249">See also</span></span>

- [<span data-ttu-id="87f4f-250">Globalizace pro WPF</span><span class="sxs-lookup"><span data-stu-id="87f4f-250">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="87f4f-251">Přehled automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="87f4f-251">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
