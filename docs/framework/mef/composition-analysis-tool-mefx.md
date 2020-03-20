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
# <a name="composition-analysis-tool-mefx"></a>Nástroj pro analýzu sestavení (Mefx)
Nástroj Mefx (Composition Analysis Tool) je aplikace příkazového řádku, která analyzuje soubory knihovny (.dll) a aplikací (.exe) obsahující součásti Mef (Managed Extensibility Framework). Primárním účelem Mefx je poskytnout vývojářům způsob, jak diagnostikovat selhání složení v jejich MEF aplikacích bez požadavku přidat těžkopádný trasovací kód do samotné aplikace. Může být také užitečné porozumět částem z knihovny poskytované třetí stranou. Toto téma popisuje, jak používat Mefx a poskytuje odkaz na jeho syntaxi.  
  
<a name="getting_mefx"></a>
## <a name="getting-mefx"></a>Získání Mefx  
 Mefx je k dispozici na GitHubu na [managed rozšiřitelnosti Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0). Jednoduše stáhněte a rozbalte nástroj.  
  
<a name="basic_syntax"></a>
## <a name="basic-syntax"></a>Základní syntaxe  
 Mefx je vyvolán z příkazového řádku v následujícím formátu:  
  
```console
mefx [files and directories] [action] [options]  
```  
  
 První sada argumentů určuje soubory a adresáře, ze kterých mají být načteny součásti pro analýzu. Zadejte soubor `/file:` s přepínačem a `/directory:` adresář s přepínačem. Můžete zadat více souborů nebo adresářů, jak je znázorněno v následujícím příkladu:  
  
```console  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
> Každý soubor DLL nebo .exe by měl být načten pouze jednou. Pokud je soubor načten vícekrát, nástroj může vrátit nesprávné informace.  
  
 Po seznamu souborů a adresářů je nutné zadat příkaz a všechny možnosti pro tento příkaz.  
  
<a name="listing_available_parts"></a>
## <a name="listing-available-parts"></a>Výpis dostupných částí  
 Pomocí `/parts` akce můžete vypsat všechny části deklarované v načtených souborech. Výsledkem je jednoduchý seznam názvů součástí.  
  
```console
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 Další informace o součástech `/verbose` získáte pomocí možnosti. Tím se vyjádí další informace pro všechny dostupné díly. Chcete-li získat další informace o `/type` jednom `/parts`dílu, použijte místo akce .  
  
```console  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>
## <a name="listing-imports-and-exports"></a>Výpis importů a exportů  
 Akce `/imports` `/exports` a zobrazí seznam všech importovaných částí a všech exportovaných částí. Můžete také uvést části, které importují nebo `/importers` `/exporters` exportují určitý typ pomocí akce nebo.  
  
```console  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 Tuto `/verbose` možnost můžete také použít na tyto akce.  
  
<a name="finding_rejected_parts"></a>
## <a name="finding-rejected-parts"></a>Hledání odmítnutých dílů  
 Jakmile nahraje dostupné díly, Mefx používá kompozici MEF motor ukládat je. Části, které nelze úspěšně skládat, se označují jako *odmítnuté*. Chcete-li vypsat `/rejected` všechny odmítnuté části, použijte akci.  
  
 `/verbose` Tuto možnost můžete použít `/rejected` s akcí k tisku podrobných informací o odmítnutých dílech. V následujícím příkladu `ClassLibrary1` dll `AddIn` obsahuje část, která `MemberPart` `ChainOne` importuje a části. `ChainOne`dovozu `ChainTwo`, `ChainTwo` ale neexistuje. To znamená, že `ChainOne` je `AddIn` odmítnut, což způsobuje, že má být odmítnut.  
  
```console  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 Následující ukazuje úplný výstup předchozího příkazu:  
  
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
  
 Zajímavé informace jsou obsaženy `[Exception]` `[Unsuitable]` ve výsledcích. Výsledek `[Exception]` poskytuje informace o tom, proč byla část odmítnuta. Výsledek `[Unsuitable]` označuje, proč jinak odpovídající díl nelze použít k vyplnění importu; v tomto případě, protože tato část byla sama zamítnuta z důvodu chybějících dovozů.  
  
<a name="analyzing_primary_causes"></a>
## <a name="analyzing-primary-causes"></a>Analýza primárních příčin  
 Pokud je v řetězci dlouhých závislostí propojeno několik částí, může problém týkající se části poblíž dna způsobit odmítnutí celého řetězce. Diagnostika těchto problémů může být obtížná, protože hlavní příčina selhání není vždy zřejmá. Chcete-li pomoci s problémem, můžete použít `/causes` akci, která se pokusí najít hlavní příčinu jakéhokoli kaskádového odmítnutí.  
  
 Použití `/causes` akce v předchozím příkladu by `ChainOne`vypsat pouze informace pro , `AddIn`jehož nevyplněný import je hlavní příčinou odmítnutí . Akci `/causes` lze použít jak v `/verbose` normálním, tak v možnostech.  
  
> [!NOTE]
> Ve většině případů bude Mefx schopen diagnostikovat hlavní příčinu kaskádového selhání. Však v případech, kdy části jsou přidány programově do kontejneru, případy `ExportProvider` zahrnující hierarchické kontejnery nebo případy zahrnující vlastní implementace, Mefx nebude moci diagnostikovat příčinu. Obecně platí, že dříve popsané případy je třeba se vyhnout, pokud je to možné, protože selhání je obecně obtížné diagnostikovat.  
  
<a name="white_lists"></a>
## <a name="white-lists"></a>Bílé seznamy  
 Tato `/whitelist` možnost umožňuje zadat textový soubor se seznamem částí, u kterých se očekává odmítnutí. Neočekávaná odmítnutí budou označena příznakem. To může být užitečné při analýze neúplné knihovny nebo dílčí knihovny, která chybí některé závislosti. Možnost `/whitelist` lze použít na `/rejected` `/causes` akce nebo.  
  
 Zvažte soubor s názvem test.txt, který obsahuje text "ClassLibrary1.ChainOne". Pokud spustíte `/rejected` akci `/whitelist` s možností v předchozím příkladu, vytvoří následující výstup:  
  
```console
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
