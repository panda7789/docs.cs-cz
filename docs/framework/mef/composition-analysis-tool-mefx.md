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
Nástroj pro analýzu kompozice (Mefx) je aplikace příkazového řádku, která analyzuje soubory knihovny (. dll) a aplikace (. exe) obsahující součásti Managed Extensibility Framework (MEF). Hlavním účelem Mefx je poskytnout vývojářům způsob, jak diagnostikovat chyby ve svých aplikacích MEF bez nutnosti přidat nenáročný kód trasování do samotné aplikace. Může být také užitečné k pochopení částí z knihovny poskytované třetí stranou. Toto téma popisuje, jak používat Mefx a poskytuje odkaz na jeho syntaxi.  
  
<a name="getting_mefx"></a>
## <a name="getting-mefx"></a>Získání Mefx  
 Mefx je k dispozici na GitHubu na adrese [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0). Stačí stáhnout a rozbalit nástroj.  
  
<a name="basic_syntax"></a>
## <a name="basic-syntax"></a>Základní syntaxe  
 Mefx je vyvolána z příkazového řádku v následujícím formátu:  
  
```console
mefx [files and directories] [action] [options]  
```  
  
 První sada argumentů Určuje soubory a adresáře, ze kterých se mají načíst části pro analýzu. Zadejte soubor s `/file:` přepínačem a adresář s `/directory:` přepínačem. Můžete zadat více souborů nebo adresářů, jak je znázorněno v následujícím příkladu:  
  
```console  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
> Každý soubor. dll nebo. exe by se měl načíst jenom jednou. Pokud je soubor načten několikrát, může nástroj vrátit nesprávné informace.  
  
 Po seznamu souborů a adresářů musíte zadat příkaz a všechny možnosti tohoto příkazu.  
  
<a name="listing_available_parts"></a>
## <a name="listing-available-parts"></a>Výpis dostupných částí  
 Použijte `/parts` akci k vypsání všech částí deklarovaných v načtených souborech. Výsledkem je jednoduchý seznam názvů částí.  
  
```console
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 Další informace o součástech získáte pomocí `/verbose` možnosti. Tím se zobrazí další informace pro všechny dostupné části. Chcete-li získat další informace o jedné části, použijte `/type` akci místo `/parts`.  
  
```console  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>
## <a name="listing-imports-and-exports"></a>Výpis importu a exportů  
 Akce `/imports` a `/exports` zobrazí seznam všech importovaných částí a všech exportovaných částí v uvedeném pořadí. Můžete také uvést části, které importují nebo exportují konkrétní typ pomocí akcí `/importers` nebo. `/exporters`  
  
```console  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 Tuto `/verbose` možnost můžete použít také u těchto akcí.  
  
<a name="finding_rejected_parts"></a>
## <a name="finding-rejected-parts"></a>Hledání odmítnutých částí  
 Po načtení dostupných částí Mefx použije modul kompozice MEF k jejich sestavení. Části, které se nedají úspěšně sestavit, se označují jako *zamítnuté*. Chcete-li zobrazit seznam všech odmítnutých částí `/rejected` , použijte akci.  
  
 K tisku podrobných `/verbose` informací o zamítnutých částech můžete použít možnost s `/rejected` akcí. V následujícím `ClassLibrary1` příkladu knihovna DLL `AddIn` obsahuje část, která importuje části `MemberPart` a. `ChainOne` `ChainOne`Importuje `ChainTwo`, ale `ChainTwo` neexistuje. To znamená, `ChainOne` že se zamítlo, `AddIn` což způsobí odmítnutí.  
  
```console  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 Následující příklad ukazuje úplný výstup předchozího příkazu:  
  
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
  
 Zajímavé informace jsou obsaženy ve výsledcích `[Exception]` a. `[Unsuitable]` `[Exception]` Výsledek poskytuje informace o tom, proč byla část odmítnuta. `[Unsuitable]` Výsledek indikuje, proč nelze použít část, která by se shodovala s naplněním importu; v takovém případě, protože tato část byla pro chybějící importy odmítnutá.  
  
<a name="analyzing_primary_causes"></a>
## <a name="analyzing-primary-causes"></a>Analýza primárních příčin  
 Je-li v dlouhém řetězu závislostí propojeno několik částí, může dojít k zamítnutí celého řetězce. Diagnostikování těchto problémů může být obtížné, protože hlavní příčina selhání není vždy zřejmá. K tomu, abyste mohli problém vyřešit, můžete použít `/causes` akci, která se pokusí najít hlavní příčinu kaskádového zamítnutí.  
  
 Pomocí `/causes` akce v předchozím příkladu by se měly zobrazit jenom informace pro `ChainOne`, jejichž vyplněný import je hlavní příčinou zamítnutí `AddIn`. Tuto `/causes` akci lze použít v normálním i `/verbose` možnosti.  
  
> [!NOTE]
> Ve většině případů bude Mefx moci diagnostikovat hlavní příčinu kaskádového selhání. V případech, kdy jsou do kontejneru přidány části programově, případy zahrnující hierarchické kontejnery, nebo případy zahrnující vlastní `ExportProvider` implementace, Mefx nebude moci diagnostikovat příčinu. Obecně by se výše popsané případy měly vyhýbat, pokud je to možné, protože chyby obecně obtížně diagnostikují.  
  
<a name="white_lists"></a>
## <a name="white-lists"></a>Prázdné seznamy  
 `/whitelist` Možnost umožňuje zadat textový soubor se seznamem částí, u kterých se očekává odmítnutí. Neočekávaná zamítnutí budou označena příznakem. To může být užitečné při analýze nekompletní knihovny nebo podknihovny, ve které chybí některé závislosti. `/whitelist` Možnost lze použít na akce `/rejected` nebo `/causes` .  
  
 Zvažte soubor s názvem test. txt, který obsahuje text "ClassLibrary1. ChainOne". Pokud spustíte `/rejected` akci s `/whitelist` možností v předchozím příkladu, vytvoří se následující výstup:  
  
```console
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
