---
title: Nástroj pro analýzu sestavení (Mefx)
ms.date: 03/30/2017
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6851ac334d439f2e5c0f6056f5226e3faa1503d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61872336"
---
# <a name="composition-analysis-tool-mefx"></a>Nástroj pro analýzu sestavení (Mefx)
Nástroj pro analýzu sestavení (Mefx) je aplikace příkazového řádku, která analyzuje knihovny (.dll) a soubory aplikace (.exe) obsahující části Managed Extensibility Framework (MEF). Primárním účelem Mefx je vývojářům poskytuje způsob, jak Diagnostika selhání sestavení ve svých aplikacích MEF bez nutnosti přidat kód náročné trasování do vlastní aplikace. Může být také užitečné porozumět částí z knihovny poskytované třetích stran. Toto téma popisuje způsob použití Mefx a poskytuje odkaz pro její syntaxe.  
  
<a name="getting_mefx"></a>   
## <a name="getting-mefx"></a>Získávání Mefx  
 Je k dispozici na Githubu v Mefx [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0). Jednoduše stáhněte a rozbalte nástroj.  
  
<a name="basic_syntax"></a>   
## <a name="basic-syntax"></a>Základní syntaxe  
 Mefx vyvolat pomocí příkazového řádku v následujícím formátu:  
  
```  
mefx [files and directories] [action] [options]  
```  
  
 První sadu argumentů určit soubory a adresáře, ze kterého se má načíst součásti pro analýzu. Zadejte soubor s `/file:` přepínače a adresář se `/directory:` přepnout. Můžete zadat více souborů či adresářů, jak je znázorněno v následujícím příkladu:  
  
```  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
>  Každý .dll nebo .exe by měla načíst pouze jednou. Pokud je soubor načten více než jednou, nástroj může vrátit nesprávné informace.  
  
 Po seznam souborů a adresářů je nutné zadat příkazu a možnosti pro tento příkaz.  
  
<a name="listing_available_parts"></a>   
## <a name="listing-available-parts"></a>Výpis dostupných částí  
 Použití `/parts` akci vypsat všechny součásti deklarované v souborech načíst. Výsledkem je jednoduchý seznam názvů část.  
  
```  
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 Další informace o součástech, použijte `/verbose` možnost. To bude výstupní Další informace o všech dostupných částí. Chcete-li získat další informace o jedné součásti, použijte `/type` akce místo `/parts`.  
  
```  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>   
## <a name="listing-imports-and-exports"></a>Výpis importy a exporty  
 `/imports` a `/exports` akce zobrazí seznam všechny importované části a všechny exportované části, v uvedeném pořadí. Můžete také zařadit části, které importovat nebo exportovat pomocí určitého typu `/importers` nebo `/exporters` akce.  
  
```  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 Můžete také použít `/verbose` možnost tyto akce.  
  
<a name="finding_rejected_parts"></a>   
## <a name="finding-rejected-parts"></a>Zjištění odmítl částí  
 Po jeho načtení dostupných částí, používá Mefx Kompoziční modul rozhraní MEF k vytvořte z nich. Části, které nemohou být složené úspěšně jsou označovány jako *odmítl*. K zobrazení seznamu všechny odmítnuté části, použijte `/rejected` akce.  
  
 Můžete použít `/verbose` spolu s možností `/rejected` akce k vytištění podrobné informace o odmítl částí. V následujícím příkladu `ClassLibrary1` obsahuje knihovny DLL `AddIn` část, která importuje `MemberPart` a `ChainOne` částí. `ChainOne` Importuje `ChainTwo`, ale `ChainTwo` neexistuje. To znamená, že `ChainOne` byl odmítnut, které způsobí, že `AddIn` zamítnutí.  
  
```  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 Následuje úplný výstup z předchozího příkazu:  
  
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
  
 Zajímavé informace jsou součástí `[Exception]` a `[Unsuitable]` výsledky. `[Exception]` Výsledek obsahuje informace o proč byla odmítnuta část. `[Unsuitable]` Výsledek vyplývá, proč nelze použít jako součást jinak odpovídající tak, aby vyplnil importu, v tomto případě protože tuto část byl sám odmítnutých pro chybějící importuje.  
  
<a name="analyzing_primary_causes"></a>   
## <a name="analyzing-primary-causes"></a>Analýza primární způsobí, že  
 Pokud několik částí jsou propojeny v řetězec dlouhý závislostí, může způsobit problém zahrnující část dole celý řetěz zamítnutí. Diagnostika těchto problémů může být obtížné, protože hlavní příčinu selhání není vždy zřejmé. Chcete-li pomoci s problémem, který můžete použít `/causes` akce, která se pokusí najít původní příčinu možných žádné kaskádové zamítnutí.  
  
 Použití `/causes` akce v předchozím příkladu by zobrazila seznam pouze informace o `ChainOne`, jehož nevyplněným import je hlavní příčinou zamítnutí `AddIn`. `/causes` Akce lze použít v obou normální a `/verbose` možnosti.  
  
> [!NOTE]
>  Ve většině případů budou moci diagnostikovat původní příčinu selhání kaskádové Mefx. Ale v případech, kde částí se prostřednictvím kódu programu do kontejneru přidá, případech hierarchické kontejnery nebo případech vlastní `ExportProvider` implementacích Mefx nebude možné určování příčin problémů. Obecně platí, výše popsaných případech mělo by se vyhnout tam, kde je to možné, jsou obecně obtížné diagnostikovat selhání.  
  
<a name="white_lists"></a>   
## <a name="white-lists"></a>Bílý list  
 `/whitelist` Možnost umožňuje zadat textový soubor, který obsahuje části, které se očekává zamítnutí. Neočekávané zamítnutí pak mají označit příznakem. To může být užitečné při analýze neúplné knihovny nebo dílčí knihovnu, která chybí některé závislosti. `/whitelist` Možnost lze použít pouze k `/rejected` nebo `/causes` akce.  
  
 Vezměte v úvahu soubor s názvem test.txt, který obsahuje text "ClassLibrary1.ChainOne". Pokud spustíte `/rejected` akce s `/whitelist` možnost v předchozím příkladu, vytvoří následující výstup:  
  
```  
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
