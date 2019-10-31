---
title: Nástroj pro analýzu sestavení (Mefx)
ms.date: 03/30/2017
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
ms.openlocfilehash: bb2748b16a16d7d01b076402889829f5b31a1912
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126374"
---
# <a name="composition-analysis-tool-mefx"></a><span data-ttu-id="f4a54-102">Nástroj pro analýzu sestavení (Mefx)</span><span class="sxs-lookup"><span data-stu-id="f4a54-102">Composition Analysis Tool (Mefx)</span></span>
<span data-ttu-id="f4a54-103">Nástroj pro analýzu kompozice (Mefx) je aplikace příkazového řádku, která analyzuje soubory knihovny (. dll) a aplikace (. exe) obsahující součásti Managed Extensibility Framework (MEF).</span><span class="sxs-lookup"><span data-stu-id="f4a54-103">The Composition Analysis Tool (Mefx) is a command-line application that analyzes library (.dll) and application (.exe) files containing Managed Extensibility Framework (MEF) parts.</span></span> <span data-ttu-id="f4a54-104">Hlavním účelem Mefx je poskytnout vývojářům způsob, jak diagnostikovat chyby ve svých aplikacích MEF bez nutnosti přidat nenáročný kód trasování do samotné aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4a54-104">The primary purpose of Mefx is to provide developers a way to diagnose composition failures in their MEF applications without the requirement to add cumbersome tracing code to the application itself.</span></span> <span data-ttu-id="f4a54-105">Může být také užitečné k pochopení částí z knihovny poskytované třetí stranou.</span><span class="sxs-lookup"><span data-stu-id="f4a54-105">It can also be useful to help understand parts from a library provided by a third party.</span></span> <span data-ttu-id="f4a54-106">Toto téma popisuje, jak používat Mefx a poskytuje odkaz na jeho syntaxi.</span><span class="sxs-lookup"><span data-stu-id="f4a54-106">This topic describes how to use Mefx and provides a reference for its syntax.</span></span>  
  
<a name="getting_mefx"></a>   
## <a name="getting-mefx"></a><span data-ttu-id="f4a54-107">Získání Mefx</span><span class="sxs-lookup"><span data-stu-id="f4a54-107">Getting Mefx</span></span>  
 <span data-ttu-id="f4a54-108">Mefx je k dispozici na GitHubu na adrese [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span><span class="sxs-lookup"><span data-stu-id="f4a54-108">Mefx is available on GitHub at [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span></span> <span data-ttu-id="f4a54-109">Stačí stáhnout a rozbalit nástroj.</span><span class="sxs-lookup"><span data-stu-id="f4a54-109">Simply download and unzip the tool.</span></span>  
  
<a name="basic_syntax"></a>   
## <a name="basic-syntax"></a><span data-ttu-id="f4a54-110">Základní syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4a54-110">Basic Syntax</span></span>  
 <span data-ttu-id="f4a54-111">Mefx je vyvolána z příkazového řádku v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="f4a54-111">Mefx is invoked from the command line in the following format:</span></span>  
  
```console
mefx [files and directories] [action] [options]  
```  
  
 <span data-ttu-id="f4a54-112">První sada argumentů Určuje soubory a adresáře, ze kterých se mají načíst části pro analýzu.</span><span class="sxs-lookup"><span data-stu-id="f4a54-112">The first set of arguments specify the files and directories from which to load parts for analysis.</span></span> <span data-ttu-id="f4a54-113">Zadejte soubor s přepínačem `/file:` a adresářem s přepínačem `/directory:`.</span><span class="sxs-lookup"><span data-stu-id="f4a54-113">Specify a file with the `/file:` switch, and a directory with the `/directory:` switch.</span></span> <span data-ttu-id="f4a54-114">Můžete zadat více souborů nebo adresářů, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f4a54-114">You can specify multiple files or directories, as shown in the following example:</span></span>  
  
```console  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
> <span data-ttu-id="f4a54-115">Každý soubor. dll nebo. exe by se měl načíst jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="f4a54-115">Each .dll or .exe should only be loaded one time.</span></span> <span data-ttu-id="f4a54-116">Pokud je soubor načten několikrát, může nástroj vrátit nesprávné informace.</span><span class="sxs-lookup"><span data-stu-id="f4a54-116">If a file is loaded multiple times, the tool may return incorrect information.</span></span>  
  
 <span data-ttu-id="f4a54-117">Po seznamu souborů a adresářů musíte zadat příkaz a všechny možnosti tohoto příkazu.</span><span class="sxs-lookup"><span data-stu-id="f4a54-117">After the list of files and directories, you must specify a command, and any options for that command.</span></span>  
  
<a name="listing_available_parts"></a>   
## <a name="listing-available-parts"></a><span data-ttu-id="f4a54-118">Výpis dostupných částí</span><span class="sxs-lookup"><span data-stu-id="f4a54-118">Listing Available Parts</span></span>  
 <span data-ttu-id="f4a54-119">Použijte akci `/parts` k vypsání všech částí deklarované v načtených souborech.</span><span class="sxs-lookup"><span data-stu-id="f4a54-119">Use the `/parts` action to list all the parts declared in the files loaded.</span></span> <span data-ttu-id="f4a54-120">Výsledkem je jednoduchý seznam názvů částí.</span><span class="sxs-lookup"><span data-stu-id="f4a54-120">The result is a simple list of part names.</span></span>  
  
```console
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 <span data-ttu-id="f4a54-121">Další informace o součástech získáte pomocí možnosti `/verbose`.</span><span class="sxs-lookup"><span data-stu-id="f4a54-121">For more information about the parts, use the `/verbose` option.</span></span> <span data-ttu-id="f4a54-122">Tím se zobrazí další informace pro všechny dostupné části.</span><span class="sxs-lookup"><span data-stu-id="f4a54-122">This will output more information for all available parts.</span></span> <span data-ttu-id="f4a54-123">Chcete-li získat další informace o jedné části, použijte `/type` akci místo `/parts`.</span><span class="sxs-lookup"><span data-stu-id="f4a54-123">To get more information about a single part, use the `/type` action instead of `/parts`.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>   
## <a name="listing-imports-and-exports"></a><span data-ttu-id="f4a54-124">Výpis importu a exportů</span><span class="sxs-lookup"><span data-stu-id="f4a54-124">Listing Imports and Exports</span></span>  
 <span data-ttu-id="f4a54-125">Akce `/imports` a `/exports` zobrazí seznam všech importovaných částí a všech exportovaných částí v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f4a54-125">The `/imports` and `/exports` actions will list all the imported parts and all the exported parts, respectively.</span></span> <span data-ttu-id="f4a54-126">Můžete také uvést části, které importují nebo exportují konkrétní typ pomocí akcí `/importers` nebo `/exporters`.</span><span class="sxs-lookup"><span data-stu-id="f4a54-126">You can also list the parts that import or export a particular type by using the `/importers` or `/exporters` actions.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 <span data-ttu-id="f4a54-127">U těchto akcí můžete také použít možnost `/verbose`.</span><span class="sxs-lookup"><span data-stu-id="f4a54-127">You can also apply the `/verbose` option to these actions.</span></span>  
  
<a name="finding_rejected_parts"></a>   
## <a name="finding-rejected-parts"></a><span data-ttu-id="f4a54-128">Hledání odmítnutých částí</span><span class="sxs-lookup"><span data-stu-id="f4a54-128">Finding Rejected Parts</span></span>  
 <span data-ttu-id="f4a54-129">Po načtení dostupných částí Mefx použije modul kompozice MEF k jejich sestavení.</span><span class="sxs-lookup"><span data-stu-id="f4a54-129">Once it has loaded the available parts, Mefx uses the MEF composition engine to compose them.</span></span> <span data-ttu-id="f4a54-130">Části, které se nedají úspěšně sestavit, se označují jako *zamítnuté*.</span><span class="sxs-lookup"><span data-stu-id="f4a54-130">Parts that cannot be successfully composed are referred to as *rejected*.</span></span> <span data-ttu-id="f4a54-131">Chcete-li zobrazit seznam všech odmítnutých částí, použijte akci `/rejected`.</span><span class="sxs-lookup"><span data-stu-id="f4a54-131">To list all the rejected parts, use the `/rejected` action.</span></span>  
  
 <span data-ttu-id="f4a54-132">K tisku podrobných informací o zamítnutých částech můžete použít možnost `/verbose` s akcí `/rejected`.</span><span class="sxs-lookup"><span data-stu-id="f4a54-132">You can use the `/verbose` option with the `/rejected` action to print detailed information about rejected parts.</span></span> <span data-ttu-id="f4a54-133">V následujícím příkladu `ClassLibrary1` DLL obsahuje `AddIn` část, která importuje `MemberPart` a `ChainOne` části.</span><span class="sxs-lookup"><span data-stu-id="f4a54-133">In the following example, the `ClassLibrary1` DLL contains the `AddIn` part, which imports the `MemberPart` and `ChainOne` parts.</span></span> <span data-ttu-id="f4a54-134">`ChainOne` importuje `ChainTwo`, ale `ChainTwo` neexistuje.</span><span class="sxs-lookup"><span data-stu-id="f4a54-134">`ChainOne` imports `ChainTwo`, but `ChainTwo` does not exist.</span></span> <span data-ttu-id="f4a54-135">To znamená, že `ChainOne` zamítnutá, což způsobí odmítnutí `AddIn`.</span><span class="sxs-lookup"><span data-stu-id="f4a54-135">This means that `ChainOne` is rejected, which causes `AddIn` to be rejected.</span></span>  
  
```console  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 <span data-ttu-id="f4a54-136">Následující příklad ukazuje úplný výstup předchozího příkazu:</span><span class="sxs-lookup"><span data-stu-id="f4a54-136">The following shows the complete output of the previous command:</span></span>  
  
```output
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
  
 <span data-ttu-id="f4a54-137">Zajímavé informace jsou obsaženy v `[Exception]` a `[Unsuitable]` výsledky.</span><span class="sxs-lookup"><span data-stu-id="f4a54-137">The interesting information is contained in the `[Exception]` and `[Unsuitable]` results.</span></span> <span data-ttu-id="f4a54-138">Výsledek `[Exception]` poskytuje informace o tom, proč byla část odmítnuta.</span><span class="sxs-lookup"><span data-stu-id="f4a54-138">The `[Exception]` result provides information about why a part was rejected.</span></span> <span data-ttu-id="f4a54-139">Výsledek `[Unsuitable]` indikuje, proč nelze použít součást, která by se shodovala s naplněním importu; v takovém případě, protože tato část byla pro chybějící importy odmítnutá.</span><span class="sxs-lookup"><span data-stu-id="f4a54-139">The `[Unsuitable]` result indicates why an otherwise-matching part could not be used to fill an import; in this case, because that part was itself rejected for missing imports.</span></span>  
  
<a name="analyzing_primary_causes"></a>   
## <a name="analyzing-primary-causes"></a><span data-ttu-id="f4a54-140">Analýza primárních příčin</span><span class="sxs-lookup"><span data-stu-id="f4a54-140">Analyzing Primary Causes</span></span>  
 <span data-ttu-id="f4a54-141">Je-li v dlouhém řetězu závislostí propojeno několik částí, může dojít k zamítnutí celého řetězce.</span><span class="sxs-lookup"><span data-stu-id="f4a54-141">If several parts are linked in a long dependency chain, a problem involving a part near the bottom may cause the entire chain to be rejected.</span></span> <span data-ttu-id="f4a54-142">Diagnostikování těchto problémů může být obtížné, protože hlavní příčina selhání není vždy zřejmá.</span><span class="sxs-lookup"><span data-stu-id="f4a54-142">Diagnosing these problems can be difficult because the root cause of the failure is not always obvious.</span></span> <span data-ttu-id="f4a54-143">Pro usnadnění tohoto problému můžete použít akci `/causes`, která se pokusí najít hlavní příčinu kaskádového zamítnutí.</span><span class="sxs-lookup"><span data-stu-id="f4a54-143">To help with the problem, you can use the `/causes` action, which attempts to find the root cause of any cascading rejection.</span></span>  
  
 <span data-ttu-id="f4a54-144">Když použijete akci `/causes` v předchozím příkladu, budou se zobrazovat jenom informace pro `ChainOne`, jejichž vyplněný import je hlavní příčinou zamítnutí `AddIn`.</span><span class="sxs-lookup"><span data-stu-id="f4a54-144">Using the `/causes` action on the previous example would list only information for `ChainOne`, whose unfilled import is the root cause of the rejection of `AddIn`.</span></span> <span data-ttu-id="f4a54-145">Akci `/causes` lze použít jak v normálních, tak v možnostech `/verbose`.</span><span class="sxs-lookup"><span data-stu-id="f4a54-145">The `/causes` action can be used in both normal and `/verbose` options.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4a54-146">Ve většině případů bude Mefx moci diagnostikovat hlavní příčinu kaskádového selhání.</span><span class="sxs-lookup"><span data-stu-id="f4a54-146">In most cases, Mefx will be able to diagnose the root cause of a cascading failure.</span></span> <span data-ttu-id="f4a54-147">V případech, kdy jsou do kontejneru přidány části programově, případy zahrnující hierarchické kontejnery nebo případy zahrnující vlastní implementace `ExportProvider`, Mefx nebude možné příčinu diagnostikovat.</span><span class="sxs-lookup"><span data-stu-id="f4a54-147">However, in cases where parts are added programmatically to a container, cases involving hierarchical containers, or cases involving custom `ExportProvider` implementations, Mefx will not be able to diagnose the cause.</span></span> <span data-ttu-id="f4a54-148">Obecně by se výše popsané případy měly vyhýbat, pokud je to možné, protože chyby obecně obtížně diagnostikují.</span><span class="sxs-lookup"><span data-stu-id="f4a54-148">In general, the previously described cases should be avoided where possible, as failures are generally difficult to diagnose.</span></span>  
  
<a name="white_lists"></a>   
## <a name="white-lists"></a><span data-ttu-id="f4a54-149">Prázdné seznamy</span><span class="sxs-lookup"><span data-stu-id="f4a54-149">White Lists</span></span>  
 <span data-ttu-id="f4a54-150">Možnost `/whitelist` umožňuje zadat textový soubor se seznamem částí, u kterých se očekává, že budou odmítnuty.</span><span class="sxs-lookup"><span data-stu-id="f4a54-150">The `/whitelist` option enables you to specify a text file that lists parts that are expected to be rejected.</span></span> <span data-ttu-id="f4a54-151">Neočekávaná zamítnutí budou označena příznakem.</span><span class="sxs-lookup"><span data-stu-id="f4a54-151">Unexpected rejections will then be flagged.</span></span> <span data-ttu-id="f4a54-152">To může být užitečné při analýze nekompletní knihovny nebo podknihovny, ve které chybí některé závislosti.</span><span class="sxs-lookup"><span data-stu-id="f4a54-152">This can be useful when you analyze an incomplete library, or a sub-library that is missing some dependencies.</span></span> <span data-ttu-id="f4a54-153">Možnost `/whitelist` lze použít pro akce `/rejected` nebo `/causes`.</span><span class="sxs-lookup"><span data-stu-id="f4a54-153">The `/whitelist` option can be applied to the `/rejected` or `/causes` actions.</span></span>  
  
 <span data-ttu-id="f4a54-154">Zvažte soubor s názvem test. txt, který obsahuje text "ClassLibrary1. ChainOne".</span><span class="sxs-lookup"><span data-stu-id="f4a54-154">Consider a file named test.txt that contains the text "ClassLibrary1.ChainOne".</span></span> <span data-ttu-id="f4a54-155">Pokud spustíte akci `/rejected` s možností `/whitelist` v předchozím příkladu, vytvoří se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f4a54-155">If you run the `/rejected` action with the `/whitelist` option on the previous example, it will produce the following output:</span></span>  
  
```console
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
