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
# <a name="composition-analysis-tool-mefx"></a>Nástroj pro analýzu sestavení (Mefx)
Nástroj pro analýzu sestavení (sestavení Mefx) je aplikace příkazového řádku, která analyzuje knihovny (DLL.dll) a soubory aplikace (.exe) obsahující části Managed Extensibility Framework (MEF). Primárním účelem Mefx je vývojáři poskytnout způsob, jak diagnostikovat chyby složení ve svých aplikacích MEF bez nutnosti přidání komplikované trasování kódu do vlastní aplikace. Také může být užitečné při pochopit částí z knihovny od třetích stran. Toto téma popisuje, jak používat Mefx a poskytuje odkaz pro její syntaxe.  
  
<a name="getting_mefx"></a>   
## <a name="getting-mefx"></a>Získávání Mefx  
 Je k dispozici na webu GitHub na Mefx [spravované rozhraní rozšiřitelnosti](https://github.com/MicrosoftArchive/mef/releases/tag/4.0). Jednoduše stáhněte a rozbalte nástroj.  
  
<a name="basic_syntax"></a>   
## <a name="basic-syntax"></a>Základní syntaxe  
 Mefx je volána z příkazového řádku v následujícím formátu:  
  
```  
mefx [files and directories] [action] [options]  
```  
  
 První sadu argumentů zadejte soubory a adresáře, ze kterého chcete načíst součásti pro analýzu. Zadejte soubor s `/file:` přepínače a adresář se `/directory:` přepínače. Více souborů či adresářů, můžete určit, jak je znázorněno v následujícím příkladu:  
  
```  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
>  Každý .exe nebo .dll by měl být načteny pouze jednou. Pokud je soubor načten vícekrát, nástroj může vrátit nesprávné informace.  
  
 Po seznam souborů a adresářů je nutné zadat příkaz a možnosti pro tento příkaz.  
  
<a name="listing_available_parts"></a>   
## <a name="listing-available-parts"></a>Výpis dostupných částí  
 Použití `/parts` akce k zobrazení seznamu všech částí deklarována v souborech načíst. Výsledkem je jednoduchý seznam názvů část.  
  
```  
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 Další informace o části použijte `/verbose` možnost. Další informace o všech dostupných částí to bude výstup. Chcete-li získat další informace o jedné součásti, použijte `/type` akce místo `/parts`.  
  
```  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>   
## <a name="listing-imports-and-exports"></a>Výpis import a export  
 `/imports` a `/exports` akce zobrazí seznam všech importovaných části a všechny exportovaný části, v uvedeném pořadí. Můžete také vytvořit seznam částí, které importovat nebo exportovat konkrétní typ pomocí `/importers` nebo `/exporters` akce.  
  
```  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 Můžete taky použít `/verbose` možnost tyto akce.  
  
<a name="finding_rejected_parts"></a>   
## <a name="finding-rejected-parts"></a>Hledání odmítl částí  
 Jakmile se načetl části k dispozici, Mefx používá modul složení MEF k jejich vytvoření. Částí, které nemůžou být složené úspěšně se označují jako *odmítl*. Chcete-li seznam odmítnutých částí, použijte `/rejected` akce.  
  
 Můžete použít `/verbose` možnost s `/rejected` akce tisknout podrobné informace o odmítnuta částí. V následujícím příkladu `ClassLibrary1` obsahuje knihovnu DLL `AddIn` součástí, které importy `MemberPart` a `ChainOne` částí. `ChainOne`Importuje `ChainTwo`, ale `ChainTwo` neexistuje. To znamená, že `ChainOne` byl odmítnut, který spustí `AddIn` zamítnutí.  
  
```  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 Na obrázku je kompletní výstup předchozí příkaz:  
  
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
  
 Je součástí zajímavé informace `[Exception]` a `[Unsuitable]` výsledky. `[Exception]` Výsledek obsahuje informace o proč byla odmítnuta součástí. `[Unsuitable]` Výsledek označuje, proč nebylo možné z jinak odpovídající části použitou k vyplnění importu; v takovém případě vzhledem k tomu, že část byla samotné odmítnutých pro importy chybí.  
  
<a name="analyzing_primary_causes"></a>   
## <a name="analyzing-primary-causes"></a>Analýza primární způsobí, že  
 Pokud několik částí jsou propojené v řetězu dlouho závislostí, může způsobit problém zahrnující součástí v dolní celý řetěz se odmítne. Diagnostikování těchto problémů může být složité, protože hlavní příčinu selhání není vždy zřejmé. Chcete-li pomoci s problémem, můžete použít `/causes` akce, která se pokusí najít příčinu žádné kaskádových odmítání.  
  
 Pomocí `/causes` akce v předchozím příkladu by zobrazovaly pouze informace o `ChainOne`, jejichž nevyplněný importu se hlavní příčinu zamítnutí `AddIn`. `/causes` Akci lze použít v obou normální a `/verbose` možnosti.  
  
> [!NOTE]
>  Ve většině případů bude moct diagnostikou hlavní příčiny selhání kaskádových Mefx. Však v případech, kde součásti jsou přidány prostřednictvím kódu programu do kontejneru, případech zahrnující hierarchické kontejnery nebo případech zahrnující vlastní `ExportProvider` implementacích Mefx nebude možné při určování příčin. Obecně platí výše popsaných případech je nutno kde je to možné, jako jsou obecně obtížné diagnostikovat chyby.  
  
<a name="white_lists"></a>   
## <a name="white-lists"></a>Seznamy povolených  
 `/whitelist` Možnost umožňuje zadat textový soubor, který obsahuje seznam částí, které budou odmítnuty. Se označilo poté neočekávané zamítnutí. To může být užitečné, když analyzujete neúplné knihovny nebo dílčí knihovny, která chybí některé závislosti. `/whitelist` Možnost lze použít k `/rejected` nebo `/causes` akce.  
  
 Vezměte v úvahu soubor s názvem test.txt, který obsahuje text "ClassLibrary1.ChainOne". Pokud spustíte `/rejected` akce s `/whitelist` možnost na předchozí příklad, vygeneruje následující výstup:  
  
```  
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
