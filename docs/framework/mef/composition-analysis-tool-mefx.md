---
title: "Nástroj pro analýzu sestavení (Mefx)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 740ba87fd247e05b1bc32e3732819514ba2806ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="composition-analysis-tool-mefx"></a><span data-ttu-id="1ab67-102">Nástroj pro analýzu sestavení (Mefx)</span><span class="sxs-lookup"><span data-stu-id="1ab67-102">Composition Analysis Tool (Mefx)</span></span>
<span data-ttu-id="1ab67-103">Nástroj pro analýzu sestavení (sestavení Mefx) je aplikace příkazového řádku, která analyzuje knihovny (DLL.dll) a soubory aplikace (.exe) obsahující části Managed Extensibility Framework (MEF).</span><span class="sxs-lookup"><span data-stu-id="1ab67-103">The Composition Analysis Tool (Mefx) is a command-line application that analyzes library (.dll) and application (.exe) files containing Managed Extensibility Framework (MEF) parts.</span></span> <span data-ttu-id="1ab67-104">Primárním účelem Mefx je vývojáři poskytnout způsob, jak diagnostikovat chyby složení ve svých aplikacích MEF bez nutnosti přidání komplikované trasování kódu do vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="1ab67-104">The primary purpose of Mefx is to provide developers a way to diagnose composition failures in their MEF applications without the requirement to add cumbersome tracing code to the application itself.</span></span> <span data-ttu-id="1ab67-105">Také může být užitečné při pochopit částí z knihovny od třetích stran.</span><span class="sxs-lookup"><span data-stu-id="1ab67-105">It can also be useful to help understand parts from a library provided by a third party.</span></span> <span data-ttu-id="1ab67-106">Toto téma popisuje, jak používat Mefx a poskytuje odkaz pro její syntaxe.</span><span class="sxs-lookup"><span data-stu-id="1ab67-106">This topic describes how to use Mefx and provides a reference for its syntax.</span></span>  
  
<a name="getting_mefx"></a>   
## <a name="getting-mefx"></a><span data-ttu-id="1ab67-107">Získávání Mefx</span><span class="sxs-lookup"><span data-stu-id="1ab67-107">Getting Mefx</span></span>  
 <span data-ttu-id="1ab67-108">Je k dispozici na webu GitHub na Mefx [spravované rozhraní rozšiřitelnosti](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span><span class="sxs-lookup"><span data-stu-id="1ab67-108">Mefx is available on GitHub at [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span></span> <span data-ttu-id="1ab67-109">Jednoduše stáhněte a rozbalte nástroj.</span><span class="sxs-lookup"><span data-stu-id="1ab67-109">Simply download and unzip the tool.</span></span>  
  
<a name="basic_syntax"></a>   
## <a name="basic-syntax"></a><span data-ttu-id="1ab67-110">Základní syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ab67-110">Basic Syntax</span></span>  
 <span data-ttu-id="1ab67-111">Mefx je volána z příkazového řádku v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="1ab67-111">Mefx is invoked from the command line in the following format:</span></span>  
  
```  
mefx [files and directories] [action] [options]  
```  
  
 <span data-ttu-id="1ab67-112">První sadu argumentů zadejte soubory a adresáře, ze kterého chcete načíst součásti pro analýzu.</span><span class="sxs-lookup"><span data-stu-id="1ab67-112">The first set of arguments specify the files and directories from which to load parts for analysis.</span></span> <span data-ttu-id="1ab67-113">Zadejte soubor s `/file:` přepínače a adresář se `/directory:` přepínače.</span><span class="sxs-lookup"><span data-stu-id="1ab67-113">Specify a file with the `/file:` switch, and a directory with the `/directory:` switch.</span></span> <span data-ttu-id="1ab67-114">Více souborů či adresářů, můžete určit, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1ab67-114">You can specify multiple files or directories, as shown in the following example:</span></span>  
  
```  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
>  <span data-ttu-id="1ab67-115">Každý .exe nebo .dll by měl být načteny pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="1ab67-115">Each .dll or .exe should only be loaded one time.</span></span> <span data-ttu-id="1ab67-116">Pokud je soubor načten vícekrát, nástroj může vrátit nesprávné informace.</span><span class="sxs-lookup"><span data-stu-id="1ab67-116">If a file is loaded multiple times, the tool may return incorrect information.</span></span>  
  
 <span data-ttu-id="1ab67-117">Po seznam souborů a adresářů je nutné zadat příkaz a možnosti pro tento příkaz.</span><span class="sxs-lookup"><span data-stu-id="1ab67-117">After the list of files and directories, you must specify a command, and any options for that command.</span></span>  
  
<a name="listing_available_parts"></a>   
## <a name="listing-available-parts"></a><span data-ttu-id="1ab67-118">Výpis dostupných částí</span><span class="sxs-lookup"><span data-stu-id="1ab67-118">Listing Available Parts</span></span>  
 <span data-ttu-id="1ab67-119">Použití `/parts` akce k zobrazení seznamu všech částí deklarována v souborech načíst.</span><span class="sxs-lookup"><span data-stu-id="1ab67-119">Use the `/parts` action to list all the parts declared in the files loaded.</span></span> <span data-ttu-id="1ab67-120">Výsledkem je jednoduchý seznam názvů část.</span><span class="sxs-lookup"><span data-stu-id="1ab67-120">The result is a simple list of part names.</span></span>  
  
```  
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 <span data-ttu-id="1ab67-121">Další informace o části použijte `/verbose` možnost.</span><span class="sxs-lookup"><span data-stu-id="1ab67-121">For more information about the parts, use the `/verbose` option.</span></span> <span data-ttu-id="1ab67-122">Další informace o všech dostupných částí to bude výstup.</span><span class="sxs-lookup"><span data-stu-id="1ab67-122">This will output more information for all available parts.</span></span> <span data-ttu-id="1ab67-123">Chcete-li získat další informace o jedné součásti, použijte `/type` akce místo `/parts`.</span><span class="sxs-lookup"><span data-stu-id="1ab67-123">To get more information about a single part, use the `/type` action instead of `/parts`.</span></span>  
  
```  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>   
## <a name="listing-imports-and-exports"></a><span data-ttu-id="1ab67-124">Výpis import a export</span><span class="sxs-lookup"><span data-stu-id="1ab67-124">Listing Imports and Exports</span></span>  
 <span data-ttu-id="1ab67-125">`/imports` a `/exports` akce zobrazí seznam všech importovaných části a všechny exportovaný části, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="1ab67-125">The `/imports` and `/exports` actions will list all the imported parts and all the exported parts, respectively.</span></span> <span data-ttu-id="1ab67-126">Můžete také vytvořit seznam částí, které importovat nebo exportovat konkrétní typ pomocí `/importers` nebo `/exporters` akce.</span><span class="sxs-lookup"><span data-stu-id="1ab67-126">You can also list the parts that import or export a particular type by using the `/importers` or `/exporters` actions.</span></span>  
  
```  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 <span data-ttu-id="1ab67-127">Můžete taky použít `/verbose` možnost tyto akce.</span><span class="sxs-lookup"><span data-stu-id="1ab67-127">You can also apply the `/verbose` option to these actions.</span></span>  
  
<a name="finding_rejected_parts"></a>   
## <a name="finding-rejected-parts"></a><span data-ttu-id="1ab67-128">Hledání odmítl částí</span><span class="sxs-lookup"><span data-stu-id="1ab67-128">Finding Rejected Parts</span></span>  
 <span data-ttu-id="1ab67-129">Jakmile se načetl části k dispozici, Mefx používá modul složení MEF k jejich vytvoření.</span><span class="sxs-lookup"><span data-stu-id="1ab67-129">Once it has loaded the available parts, Mefx uses the MEF composition engine to compose them.</span></span> <span data-ttu-id="1ab67-130">Částí, které nemůžou být složené úspěšně se označují jako *odmítl*.</span><span class="sxs-lookup"><span data-stu-id="1ab67-130">Parts that cannot be successfully composed are referred to as *rejected*.</span></span> <span data-ttu-id="1ab67-131">Chcete-li seznam odmítnutých částí, použijte `/rejected` akce.</span><span class="sxs-lookup"><span data-stu-id="1ab67-131">To list all the rejected parts, use the `/rejected` action.</span></span>  
  
 <span data-ttu-id="1ab67-132">Můžete použít `/verbose` možnost s `/rejected` akce tisknout podrobné informace o odmítnuta částí.</span><span class="sxs-lookup"><span data-stu-id="1ab67-132">You can use the `/verbose` option with the `/rejected` action to print detailed information about rejected parts.</span></span> <span data-ttu-id="1ab67-133">V následujícím příkladu `ClassLibrary1` obsahuje knihovnu DLL `AddIn` součástí, které importy `MemberPart` a `ChainOne` částí.</span><span class="sxs-lookup"><span data-stu-id="1ab67-133">In the following example, the `ClassLibrary1` DLL contains the `AddIn` part, which imports the `MemberPart` and `ChainOne` parts.</span></span> <span data-ttu-id="1ab67-134">`ChainOne`Importuje `ChainTwo`, ale `ChainTwo` neexistuje.</span><span class="sxs-lookup"><span data-stu-id="1ab67-134">`ChainOne` imports `ChainTwo`, but `ChainTwo` does not exist.</span></span> <span data-ttu-id="1ab67-135">To znamená, že `ChainOne` byl odmítnut, který spustí `AddIn` zamítnutí.</span><span class="sxs-lookup"><span data-stu-id="1ab67-135">This means that `ChainOne` is rejected, which causes `AddIn` to be rejected.</span></span>  
  
```  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 <span data-ttu-id="1ab67-136">Na obrázku je kompletní výstup předchozí příkaz:</span><span class="sxs-lookup"><span data-stu-id="1ab67-136">The following shows the complete output of the previous command:</span></span>  
  
```  
[Part] ClassLibrary1.AddIn from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] ClassLibrary1.AddIn (ContractName="ClassLibrary1.AddIn")  
  [Import] ClassLibrary1.AddIn.memberPart (ContractName="ClassLibrary1.MemberPart")  
    [SatisfiedBy] ClassLibrary1.MemberPart (ContractName="ClassLibrary1.MemberPart") from: ClassLibrary1.MemberPart from: AssemblyCatalog (Assembly="ClassLibrar  
y1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Import] ClassLibrary1.AddIn.chain (ContractName="ClassLibrary1.ChainOne")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainOne") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainOne".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
    [Unsuitable] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
from: ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
      [Because] PartDefinitionIsRejected, The part providing the export is rejected because of other issues.  
  
[Part] ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Primary Rejection]  
  [Export] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
  [Import] ClassLibrary1.ChainOne.chain (ContractName="ClassLibrary1.ChainTwo")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainTwo") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainTwo".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
```  
  
 <span data-ttu-id="1ab67-137">Je součástí zajímavé informace `[Exception]` a `[Unsuitable]` výsledky.</span><span class="sxs-lookup"><span data-stu-id="1ab67-137">The interesting information is contained in the `[Exception]` and `[Unsuitable]` results.</span></span> <span data-ttu-id="1ab67-138">`[Exception]` Výsledek obsahuje informace o proč byla odmítnuta součástí.</span><span class="sxs-lookup"><span data-stu-id="1ab67-138">The `[Exception]` result provides information about why a part was rejected.</span></span> <span data-ttu-id="1ab67-139">`[Unsuitable]` Výsledek označuje, proč nebylo možné z jinak odpovídající části použitou k vyplnění importu; v takovém případě vzhledem k tomu, že část byla samotné odmítnutých pro importy chybí.</span><span class="sxs-lookup"><span data-stu-id="1ab67-139">The `[Unsuitable]` result indicates why an otherwise-matching part could not be used to fill an import; in this case, because that part was itself rejected for missing imports.</span></span>  
  
<a name="analyzing_primary_causes"></a>   
## <a name="analyzing-primary-causes"></a><span data-ttu-id="1ab67-140">Analýza primární způsobí, že</span><span class="sxs-lookup"><span data-stu-id="1ab67-140">Analyzing Primary Causes</span></span>  
 <span data-ttu-id="1ab67-141">Pokud několik částí jsou propojené v řetězu dlouho závislostí, může způsobit problém zahrnující součástí v dolní celý řetěz se odmítne.</span><span class="sxs-lookup"><span data-stu-id="1ab67-141">If several parts are linked in a long dependency chain, a problem involving a part near the bottom may cause the entire chain to be rejected.</span></span> <span data-ttu-id="1ab67-142">Diagnostikování těchto problémů může být složité, protože hlavní příčinu selhání není vždy zřejmé.</span><span class="sxs-lookup"><span data-stu-id="1ab67-142">Diagnosing these problems can be difficult because the root cause of the failure is not always obvious.</span></span> <span data-ttu-id="1ab67-143">Chcete-li pomoci s problémem, můžete použít `/causes` akce, která se pokusí najít příčinu žádné kaskádových odmítání.</span><span class="sxs-lookup"><span data-stu-id="1ab67-143">To help with the problem, you can use the `/causes` action, which attempts to find the root cause of any cascading rejection.</span></span>  
  
 <span data-ttu-id="1ab67-144">Pomocí `/causes` akce v předchozím příkladu by zobrazovaly pouze informace o `ChainOne`, jejichž nevyplněný importu se hlavní příčinu zamítnutí `AddIn`.</span><span class="sxs-lookup"><span data-stu-id="1ab67-144">Using the `/causes` action on the previous example would list only information for `ChainOne`, whose unfilled import is the root cause of the rejection of `AddIn`.</span></span> <span data-ttu-id="1ab67-145">`/causes` Akci lze použít v obou normální a `/verbose` možnosti.</span><span class="sxs-lookup"><span data-stu-id="1ab67-145">The `/causes` action can be used in both normal and `/verbose` options.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ab67-146">Ve většině případů bude moct diagnostikou hlavní příčiny selhání kaskádových Mefx.</span><span class="sxs-lookup"><span data-stu-id="1ab67-146">In most cases, Mefx will be able to diagnose the root cause of a cascading failure.</span></span> <span data-ttu-id="1ab67-147">Však v případech, kde součásti jsou přidány prostřednictvím kódu programu do kontejneru, případech zahrnující hierarchické kontejnery nebo případech zahrnující vlastní `ExportProvider` implementacích Mefx nebude možné při určování příčin.</span><span class="sxs-lookup"><span data-stu-id="1ab67-147">However, in cases where parts are added programmatically to a container, cases involving hierarchical containers, or cases involving custom `ExportProvider` implementations, Mefx will not be able to diagnose the cause.</span></span> <span data-ttu-id="1ab67-148">Obecně platí výše popsaných případech je nutno kde je to možné, jako jsou obecně obtížné diagnostikovat chyby.</span><span class="sxs-lookup"><span data-stu-id="1ab67-148">In general, the previously described cases should be avoided where possible, as failures are generally difficult to diagnose.</span></span>  
  
<a name="white_lists"></a>   
## <a name="white-lists"></a><span data-ttu-id="1ab67-149">Seznamy povolených</span><span class="sxs-lookup"><span data-stu-id="1ab67-149">White Lists</span></span>  
 <span data-ttu-id="1ab67-150">`/whitelist` Možnost umožňuje zadat textový soubor, který obsahuje seznam částí, které budou odmítnuty.</span><span class="sxs-lookup"><span data-stu-id="1ab67-150">The `/whitelist` option enables you to specify a text file that lists parts that are expected to be rejected.</span></span> <span data-ttu-id="1ab67-151">Se označilo poté neočekávané zamítnutí.</span><span class="sxs-lookup"><span data-stu-id="1ab67-151">Unexpected rejections will then be flagged.</span></span> <span data-ttu-id="1ab67-152">To může být užitečné, když analyzujete neúplné knihovny nebo dílčí knihovny, která chybí některé závislosti.</span><span class="sxs-lookup"><span data-stu-id="1ab67-152">This can be useful when you analyze an incomplete library, or a sub-library that is missing some dependencies.</span></span> <span data-ttu-id="1ab67-153">`/whitelist` Možnost lze použít k `/rejected` nebo `/causes` akce.</span><span class="sxs-lookup"><span data-stu-id="1ab67-153">The `/whitelist` option can be applied to the `/rejected` or `/causes` actions.</span></span>  
  
 <span data-ttu-id="1ab67-154">Vezměte v úvahu soubor s názvem test.txt, který obsahuje text "ClassLibrary1.ChainOne".</span><span class="sxs-lookup"><span data-stu-id="1ab67-154">Consider a file named test.txt that contains the text "ClassLibrary1.ChainOne".</span></span> <span data-ttu-id="1ab67-155">Pokud spustíte `/rejected` akce s `/whitelist` možnost na předchozí příklad, vygeneruje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1ab67-155">If you run the `/rejected` action with the `/whitelist` option on the previous example, it will produce the following output:</span></span>  
  
```  
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
