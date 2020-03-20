---
title: Nástroj pro analýzu sestavení (Mefx)
ms.date: 03/30/2017
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
ms.openlocfilehash: 7d0acf16ace5aad60b32b7139a58a258fb080ee0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181291"
---
# <a name="composition-analysis-tool-mefx"></a><span data-ttu-id="fcb41-102">Nástroj pro analýzu sestavení (Mefx)</span><span class="sxs-lookup"><span data-stu-id="fcb41-102">Composition Analysis Tool (Mefx)</span></span>
<span data-ttu-id="fcb41-103">Nástroj Mefx (Composition Analysis Tool) je aplikace příkazového řádku, která analyzuje soubory knihovny (.dll) a aplikací (.exe) obsahující součásti Mef (Managed Extensibility Framework).</span><span class="sxs-lookup"><span data-stu-id="fcb41-103">The Composition Analysis Tool (Mefx) is a command-line application that analyzes library (.dll) and application (.exe) files containing Managed Extensibility Framework (MEF) parts.</span></span> <span data-ttu-id="fcb41-104">Primárním účelem Mefx je poskytnout vývojářům způsob, jak diagnostikovat selhání složení v jejich MEF aplikacích bez požadavku přidat těžkopádný trasovací kód do samotné aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcb41-104">The primary purpose of Mefx is to provide developers a way to diagnose composition failures in their MEF applications without the requirement to add cumbersome tracing code to the application itself.</span></span> <span data-ttu-id="fcb41-105">Může být také užitečné porozumět částem z knihovny poskytované třetí stranou.</span><span class="sxs-lookup"><span data-stu-id="fcb41-105">It can also be useful to help understand parts from a library provided by a third party.</span></span> <span data-ttu-id="fcb41-106">Toto téma popisuje, jak používat Mefx a poskytuje odkaz na jeho syntaxi.</span><span class="sxs-lookup"><span data-stu-id="fcb41-106">This topic describes how to use Mefx and provides a reference for its syntax.</span></span>  
  
<a name="getting_mefx"></a>
## <a name="getting-mefx"></a><span data-ttu-id="fcb41-107">Získání Mefx</span><span class="sxs-lookup"><span data-stu-id="fcb41-107">Getting Mefx</span></span>  
 <span data-ttu-id="fcb41-108">Mefx je k dispozici na GitHubu na [managed rozšiřitelnosti Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span><span class="sxs-lookup"><span data-stu-id="fcb41-108">Mefx is available on GitHub at [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span></span> <span data-ttu-id="fcb41-109">Jednoduše stáhněte a rozbalte nástroj.</span><span class="sxs-lookup"><span data-stu-id="fcb41-109">Simply download and unzip the tool.</span></span>  
  
<a name="basic_syntax"></a>
## <a name="basic-syntax"></a><span data-ttu-id="fcb41-110">Základní syntaxe</span><span class="sxs-lookup"><span data-stu-id="fcb41-110">Basic Syntax</span></span>  
 <span data-ttu-id="fcb41-111">Mefx je vyvolán z příkazového řádku v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="fcb41-111">Mefx is invoked from the command line in the following format:</span></span>  
  
```console
mefx [files and directories] [action] [options]  
```  
  
 <span data-ttu-id="fcb41-112">První sada argumentů určuje soubory a adresáře, ze kterých mají být načteny součásti pro analýzu.</span><span class="sxs-lookup"><span data-stu-id="fcb41-112">The first set of arguments specify the files and directories from which to load parts for analysis.</span></span> <span data-ttu-id="fcb41-113">Zadejte soubor `/file:` s přepínačem a `/directory:` adresář s přepínačem.</span><span class="sxs-lookup"><span data-stu-id="fcb41-113">Specify a file with the `/file:` switch, and a directory with the `/directory:` switch.</span></span> <span data-ttu-id="fcb41-114">Můžete zadat více souborů nebo adresářů, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="fcb41-114">You can specify multiple files or directories, as shown in the following example:</span></span>  
  
```console  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
> <span data-ttu-id="fcb41-115">Každý soubor DLL nebo .exe by měl být načten pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="fcb41-115">Each .dll or .exe should only be loaded one time.</span></span> <span data-ttu-id="fcb41-116">Pokud je soubor načten vícekrát, nástroj může vrátit nesprávné informace.</span><span class="sxs-lookup"><span data-stu-id="fcb41-116">If a file is loaded multiple times, the tool may return incorrect information.</span></span>  
  
 <span data-ttu-id="fcb41-117">Po seznamu souborů a adresářů je nutné zadat příkaz a všechny možnosti pro tento příkaz.</span><span class="sxs-lookup"><span data-stu-id="fcb41-117">After the list of files and directories, you must specify a command, and any options for that command.</span></span>  
  
<a name="listing_available_parts"></a>
## <a name="listing-available-parts"></a><span data-ttu-id="fcb41-118">Výpis dostupných částí</span><span class="sxs-lookup"><span data-stu-id="fcb41-118">Listing Available Parts</span></span>  
 <span data-ttu-id="fcb41-119">Pomocí `/parts` akce můžete vypsat všechny části deklarované v načtených souborech.</span><span class="sxs-lookup"><span data-stu-id="fcb41-119">Use the `/parts` action to list all the parts declared in the files loaded.</span></span> <span data-ttu-id="fcb41-120">Výsledkem je jednoduchý seznam názvů součástí.</span><span class="sxs-lookup"><span data-stu-id="fcb41-120">The result is a simple list of part names.</span></span>  
  
```console
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 <span data-ttu-id="fcb41-121">Další informace o součástech `/verbose` získáte pomocí možnosti.</span><span class="sxs-lookup"><span data-stu-id="fcb41-121">For more information about the parts, use the `/verbose` option.</span></span> <span data-ttu-id="fcb41-122">Tím se vyjádí další informace pro všechny dostupné díly.</span><span class="sxs-lookup"><span data-stu-id="fcb41-122">This will output more information for all available parts.</span></span> <span data-ttu-id="fcb41-123">Chcete-li získat další informace o `/type` jednom `/parts`dílu, použijte místo akce .</span><span class="sxs-lookup"><span data-stu-id="fcb41-123">To get more information about a single part, use the `/type` action instead of `/parts`.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>
## <a name="listing-imports-and-exports"></a><span data-ttu-id="fcb41-124">Výpis importů a exportů</span><span class="sxs-lookup"><span data-stu-id="fcb41-124">Listing Imports and Exports</span></span>  
 <span data-ttu-id="fcb41-125">Akce `/imports` `/exports` a zobrazí seznam všech importovaných částí a všech exportovaných částí.</span><span class="sxs-lookup"><span data-stu-id="fcb41-125">The `/imports` and `/exports` actions will list all the imported parts and all the exported parts, respectively.</span></span> <span data-ttu-id="fcb41-126">Můžete také uvést části, které importují nebo `/importers` `/exporters` exportují určitý typ pomocí akce nebo.</span><span class="sxs-lookup"><span data-stu-id="fcb41-126">You can also list the parts that import or export a particular type by using the `/importers` or `/exporters` actions.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 <span data-ttu-id="fcb41-127">Tuto `/verbose` možnost můžete také použít na tyto akce.</span><span class="sxs-lookup"><span data-stu-id="fcb41-127">You can also apply the `/verbose` option to these actions.</span></span>  
  
<a name="finding_rejected_parts"></a>
## <a name="finding-rejected-parts"></a><span data-ttu-id="fcb41-128">Hledání odmítnutých dílů</span><span class="sxs-lookup"><span data-stu-id="fcb41-128">Finding Rejected Parts</span></span>  
 <span data-ttu-id="fcb41-129">Jakmile nahraje dostupné díly, Mefx používá kompozici MEF motor ukládat je.</span><span class="sxs-lookup"><span data-stu-id="fcb41-129">Once it has loaded the available parts, Mefx uses the MEF composition engine to compose them.</span></span> <span data-ttu-id="fcb41-130">Části, které nelze úspěšně skládat, se označují jako *odmítnuté*.</span><span class="sxs-lookup"><span data-stu-id="fcb41-130">Parts that cannot be successfully composed are referred to as *rejected*.</span></span> <span data-ttu-id="fcb41-131">Chcete-li vypsat `/rejected` všechny odmítnuté části, použijte akci.</span><span class="sxs-lookup"><span data-stu-id="fcb41-131">To list all the rejected parts, use the `/rejected` action.</span></span>  
  
 <span data-ttu-id="fcb41-132">`/verbose` Tuto možnost můžete použít `/rejected` s akcí k tisku podrobných informací o odmítnutých dílech.</span><span class="sxs-lookup"><span data-stu-id="fcb41-132">You can use the `/verbose` option with the `/rejected` action to print detailed information about rejected parts.</span></span> <span data-ttu-id="fcb41-133">V následujícím příkladu `ClassLibrary1` dll `AddIn` obsahuje část, která `MemberPart` `ChainOne` importuje a části.</span><span class="sxs-lookup"><span data-stu-id="fcb41-133">In the following example, the `ClassLibrary1` DLL contains the `AddIn` part, which imports the `MemberPart` and `ChainOne` parts.</span></span> <span data-ttu-id="fcb41-134">`ChainOne`dovozu `ChainTwo`, `ChainTwo` ale neexistuje.</span><span class="sxs-lookup"><span data-stu-id="fcb41-134">`ChainOne` imports `ChainTwo`, but `ChainTwo` does not exist.</span></span> <span data-ttu-id="fcb41-135">To znamená, že `ChainOne` je `AddIn` odmítnut, což způsobuje, že má být odmítnut.</span><span class="sxs-lookup"><span data-stu-id="fcb41-135">This means that `ChainOne` is rejected, which causes `AddIn` to be rejected.</span></span>  
  
```console  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 <span data-ttu-id="fcb41-136">Následující ukazuje úplný výstup předchozího příkazu:</span><span class="sxs-lookup"><span data-stu-id="fcb41-136">The following shows the complete output of the previous command:</span></span>  
  
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
  
 <span data-ttu-id="fcb41-137">Zajímavé informace jsou obsaženy `[Exception]` `[Unsuitable]` ve výsledcích.</span><span class="sxs-lookup"><span data-stu-id="fcb41-137">The interesting information is contained in the `[Exception]` and `[Unsuitable]` results.</span></span> <span data-ttu-id="fcb41-138">Výsledek `[Exception]` poskytuje informace o tom, proč byla část odmítnuta.</span><span class="sxs-lookup"><span data-stu-id="fcb41-138">The `[Exception]` result provides information about why a part was rejected.</span></span> <span data-ttu-id="fcb41-139">Výsledek `[Unsuitable]` označuje, proč jinak odpovídající díl nelze použít k vyplnění importu; v tomto případě, protože tato část byla sama zamítnuta z důvodu chybějících dovozů.</span><span class="sxs-lookup"><span data-stu-id="fcb41-139">The `[Unsuitable]` result indicates why an otherwise-matching part could not be used to fill an import; in this case, because that part was itself rejected for missing imports.</span></span>  
  
<a name="analyzing_primary_causes"></a>
## <a name="analyzing-primary-causes"></a><span data-ttu-id="fcb41-140">Analýza primárních příčin</span><span class="sxs-lookup"><span data-stu-id="fcb41-140">Analyzing Primary Causes</span></span>  
 <span data-ttu-id="fcb41-141">Pokud je v řetězci dlouhých závislostí propojeno několik částí, může problém týkající se části poblíž dna způsobit odmítnutí celého řetězce.</span><span class="sxs-lookup"><span data-stu-id="fcb41-141">If several parts are linked in a long dependency chain, a problem involving a part near the bottom may cause the entire chain to be rejected.</span></span> <span data-ttu-id="fcb41-142">Diagnostika těchto problémů může být obtížná, protože hlavní příčina selhání není vždy zřejmá.</span><span class="sxs-lookup"><span data-stu-id="fcb41-142">Diagnosing these problems can be difficult because the root cause of the failure is not always obvious.</span></span> <span data-ttu-id="fcb41-143">Chcete-li pomoci s problémem, můžete použít `/causes` akci, která se pokusí najít hlavní příčinu jakéhokoli kaskádového odmítnutí.</span><span class="sxs-lookup"><span data-stu-id="fcb41-143">To help with the problem, you can use the `/causes` action, which attempts to find the root cause of any cascading rejection.</span></span>  
  
 <span data-ttu-id="fcb41-144">Použití `/causes` akce v předchozím příkladu by `ChainOne`vypsat pouze informace pro , `AddIn`jehož nevyplněný import je hlavní příčinou odmítnutí .</span><span class="sxs-lookup"><span data-stu-id="fcb41-144">Using the `/causes` action on the previous example would list only information for `ChainOne`, whose unfilled import is the root cause of the rejection of `AddIn`.</span></span> <span data-ttu-id="fcb41-145">Akci `/causes` lze použít jak v `/verbose` normálním, tak v možnostech.</span><span class="sxs-lookup"><span data-stu-id="fcb41-145">The `/causes` action can be used in both normal and `/verbose` options.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fcb41-146">Ve většině případů bude Mefx schopen diagnostikovat hlavní příčinu kaskádového selhání.</span><span class="sxs-lookup"><span data-stu-id="fcb41-146">In most cases, Mefx will be able to diagnose the root cause of a cascading failure.</span></span> <span data-ttu-id="fcb41-147">Však v případech, kdy části jsou přidány programově do kontejneru, případy `ExportProvider` zahrnující hierarchické kontejnery nebo případy zahrnující vlastní implementace, Mefx nebude moci diagnostikovat příčinu.</span><span class="sxs-lookup"><span data-stu-id="fcb41-147">However, in cases where parts are added programmatically to a container, cases involving hierarchical containers, or cases involving custom `ExportProvider` implementations, Mefx will not be able to diagnose the cause.</span></span> <span data-ttu-id="fcb41-148">Obecně platí, že dříve popsané případy je třeba se vyhnout, pokud je to možné, protože selhání je obecně obtížné diagnostikovat.</span><span class="sxs-lookup"><span data-stu-id="fcb41-148">In general, the previously described cases should be avoided where possible, as failures are generally difficult to diagnose.</span></span>  
  
<a name="white_lists"></a>
## <a name="white-lists"></a><span data-ttu-id="fcb41-149">Bílé seznamy</span><span class="sxs-lookup"><span data-stu-id="fcb41-149">White Lists</span></span>  
 <span data-ttu-id="fcb41-150">Tato `/whitelist` možnost umožňuje zadat textový soubor se seznamem částí, u kterých se očekává odmítnutí.</span><span class="sxs-lookup"><span data-stu-id="fcb41-150">The `/whitelist` option enables you to specify a text file that lists parts that are expected to be rejected.</span></span> <span data-ttu-id="fcb41-151">Neočekávaná odmítnutí budou označena příznakem.</span><span class="sxs-lookup"><span data-stu-id="fcb41-151">Unexpected rejections will then be flagged.</span></span> <span data-ttu-id="fcb41-152">To může být užitečné při analýze neúplné knihovny nebo dílčí knihovny, která chybí některé závislosti.</span><span class="sxs-lookup"><span data-stu-id="fcb41-152">This can be useful when you analyze an incomplete library, or a sub-library that is missing some dependencies.</span></span> <span data-ttu-id="fcb41-153">Možnost `/whitelist` lze použít na `/rejected` `/causes` akce nebo.</span><span class="sxs-lookup"><span data-stu-id="fcb41-153">The `/whitelist` option can be applied to the `/rejected` or `/causes` actions.</span></span>  
  
 <span data-ttu-id="fcb41-154">Zvažte soubor s názvem test.txt, který obsahuje text "ClassLibrary1.ChainOne".</span><span class="sxs-lookup"><span data-stu-id="fcb41-154">Consider a file named test.txt that contains the text "ClassLibrary1.ChainOne".</span></span> <span data-ttu-id="fcb41-155">Pokud spustíte `/rejected` akci `/whitelist` s možností v předchozím příkladu, vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="fcb41-155">If you run the `/rejected` action with the `/whitelist` option on the previous example, it will produce the following output:</span></span>  
  
```console
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
