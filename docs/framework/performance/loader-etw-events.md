---
title: Události Trasování událostí pro Windows zavaděče
ms.date: 03/30/2017
helpviewer_keywords:
- loader events [.NET Framework]
- ETW, loader events (CLR)
ms.assetid: cb403cc6-56f8-4609-b467-cdfa09f07909
ms.openlocfilehash: 0f8f96cf73882ef6556e5b9e64cf9adf389a2318
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180550"
---
# <a name="loader-etw-events"></a>Události Trasování událostí pro Windows zavaděče
Tyto události shromažďují informace týkající se načítání a uvolňování aplikačních domén, sestavení a modulů.  
  
 Všechny události zavaděče `LoaderKeyword` jsou vyvolány pod klíčovým slovem (0x8). A `DCStart` události `DCEnd` jsou vyvolány `LoaderRundownKeyword` pod (0x8) s `StartRundown` / `EndRundown` povoleno. (Další informace naleznete [v tématu CLR ETW Klíčová slova a úrovně](clr-etw-keywords-and-levels.md).)  

## <a name="application-domain-events"></a>Události domény aplikace
 V následující tabulce je uvedeno klíčové slovo a úroveň.  
  
|Klíčové slovo pro zvýšení události|Událost|Úroveň|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`(0x8)|`AppDomainLoad_V1` a `AppDomainUnLoad_V1`|Informační (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`AppDomainDCStart_V1`|Informační (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`AppDomainDCEnd_V1`|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`AppDomainLoad_V1`(přihlášenpro všechny aplikační domény)|156|Vyvolána vždy, když je vytvořena doména aplikace během životnosti procesu.|  
|`AppDomainUnLoad_V1`|157|Vyvolána vždy, když je doména aplikace zničena během životnosti procesu.|  
|`AppDomainDCStart_V1`|157|Výčet domén aplikace během spuštění rundown.|  
|`AppDomainDCEnd_V1`|158|Výčet domén aplikace během koncového zchátráno.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ID domény aplikace|vítězství:UInt64|Jedinečný identifikátor pro doménu aplikace.|  
|Příznaky AppDomainFlags|vítězství:UInt32|0x1: Výchozí doména.<br /><br /> 0x2: Spustitelný soubor.<br /><br /> 0x4: Aplikační doména, bit 28-31: Zásady sdílení této domény.<br /><br /> 0: Sdílená doména.|  
|Název_domény aplikace|win:UnicodeString|Popisný název domény aplikace. Může se změnit během životnosti procesu.|  
|AppDomainIndex|Vítězství:UInt32|Index této domény aplikace.|  
|Id instance clr|vítězství:UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  

## <a name="clr-loader-assembly-events"></a>Události sestavení nakladače CLR  
 V následující tabulce je uvedeno klíčové slovo a úroveň.  
  
|Klíčové slovo pro zvýšení události|Událost|Úroveň|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`(0x8)|`AssemblyLoad` a `AssemblyUnload`|Informační (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`AssemblyDCStart`|Informační (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`AssemblyDCEnd`|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`AssemblyLoad_V1`|154|Vyvolána při načtení sestavení.|  
|`AssemblyUnload_V1`|155|Je aktivována při uvolnění sestavení.|  
|`AssemblyDCStart_V1`|155|Výčet sestavení během spuštění rundown.|  
|`AssemblyDCEnd_V1`|156|Výčet sestavení během ukončení rundown.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ID sestavení|vítězství:UInt64|Jedinečné ID pro sestavení.|  
|ID domény aplikace|vítězství:UInt64|ID domény tohoto sestavení.|  
|ID bindingid|vítězství:UInt64|ID, které jednoznačně identifikuje vazbu sestavení.|  
|AssemblyFlags|vítězství:UInt32|0x1: Neutrální sestavení domény.<br /><br /> 0x2: Dynamická sestava.<br /><br /> 0x4: Sestavení má nativní obrázek.<br /><br /> 0x8: Sběratelská sestava.|  
|Assemblyname|win:UnicodeString|Plně kvalifikovaný název sestavení.|  
|Id instance clr|vítězství:UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|

## <a name="module-events"></a>Události modulu
 V následující tabulce je uvedeno klíčové slovo a úroveň.  
  
|Klíčové slovo pro zvýšení události|Událost|Úroveň|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`(0x8)|`ModuleLoad_V2` a `ModuleUnload_V2`|Informační (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`ModuleDCStart_V2`|Informační (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`ModuleDCEnd_V2`|Informační (4)|  
||||  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`ModuleLoad_V2`|152|Je aktivována při načtení modulu během životnosti procesu.|  
|`ModuleUnload_V2`|153|Je aktivována při uvolnění modulu během životnosti procesu.|  
|`ModuleDCStart_V2`|153|Výčet modulů během spuštění rundown.|  
|`ModuleDCEnd_V2`|154|Výčet modulů během koncového zchátráno.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ID modulu|vítězství:UInt64|Jedinečné ID modulu.|  
|ID sestavení|vítězství:UInt64|ID sestavy, ve kterém je tento modul umístěn.|  
|Příznaky modulu|vítězství:UInt32|0x1: Neutrální modul domény.<br /><br /> 0x2: Modul má nativní obraz.<br /><br /> 0x4: Dynamický modul.<br /><br /> 0x8: Modul manifestu.|  
|Vyhrazeno1|vítězství:UInt32|Rezervované pole.|  
|ModulILPath|win:UnicodeString|Cesta image zprostředkující jazyk společnosti Microsoft (MSIL) pro modul nebo název dynamického modulu, pokud se jedná o dynamické sestavení (null ukončeno).|  
|ModulNaVPath|win:UnicodeString|Cesta nativního bitového obrázku modulu, pokud je k dispozici (null ukončeno).|  
|Id instance clr|vítězství:UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
|Podpis spravovaného pdb|výhra:IDENTIFIKÁTOR GUID|Podpis GUID databáze spravovaného programu (PDB), který odpovídá tomuto modulu. (Viz poznámky.)|  
|Řízená pdbage|vítězství:UInt32|Věkové číslo zapsané do spravovaného pdb, který odpovídá tomuto modulu. (Viz poznámky.)|  
|Cesta ManagedPdbBuildPath|win:UnicodeString|Cesta k umístění, kde byla vytvořena spravovaná databáze PDB, která odpovídá tomuto modulu. V některých případech to může být pouze název souboru. (Viz poznámky.)|  
|Podpis NativePdb|výhra:IDENTIFIKÁTOR GUID|Podpis GUID pdb generátoru nativního obrazu (NGen), který odpovídá tomuto modulu, pokud je k dispozici. (Viz poznámky.)|  
|Nativní pdbage|vítězství:UInt32|Věkové číslo napsané do PDB NGen, který odpovídá tomuto modulu, pokud je to možné. (Viz poznámky.)|  
|Nativní pdbBuildPath|win:UnicodeString|Cesta k umístění, kde ngen PDB, který odpovídá tento modul byl vytvořen, pokud je k dispozici. V některých případech to může být pouze název souboru. (Viz poznámky.)|  
  
### <a name="remarks"></a>Poznámky  
  
- Pole, která mají "Pdb" v jejich názvy lze použít profilování nástroje k vyhledání PDB, které odpovídají moduly, které byly načteny během relace profilování. Hodnoty těchto polí odpovídají datům zapsaným do IMAGE_DIRECTORY_ENTRY_DEBUG částí modulu, které obvykle používají ladicí program, k vyhledání datových dispon, které odpovídají načteným modulům.  
  
- Názvy polí začínající "ManagedPdb" odkazují na spravované PDB odpovídající modulu MSIL, který byl generován spravovaným kompilátorem (například kompilátorem jazyka C# nebo Visual Basic). Tento pdb používá spravovaný formát PDB a popisuje, jak se prvky z původního spravovaného zdrojového kódu, jako jsou soubory, čísla řádků a názvy symbolů, mapují na prvky MSIL, které jsou kompilovány do modulu MSIL.  
  
- Názvy polí, které začínají "NativePdb" odkazují na NGen `NGEN createPDB`PDB generované voláním . Tento pdb používá nativní formát PDB a popisuje, jak prvky z původního spravovaného zdrojového kódu, jako jsou soubory, čísla řádků a názvy symbolů, mapovat na nativní prvky, které jsou kompilovány do modulu NGen.  

## <a name="clr-domain-module-events"></a>Události modulu domény CLR
 V následující tabulce je uvedeno klíčové slovo a úroveň.  
  
|Klíčové slovo pro zvýšení události|Událost|Úroveň|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`(0x8)|`DomainModuleLoad_V1`|Informační (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`DomainModuleDCStart_V1`|Informační (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`DomainModuleDCEnd_V1`|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`DomainModuleLoad_V1`|151|Je aktivována při načtení modulu pro doménu aplikace.|  
|`DomainModuleDCStart_V1`|151|Výčet modulů načtených pro doménu aplikace během počátečního zchátralého období a je protokolován pro všechny aplikační domény.|  
|`DomainModuleDCEnd_V1`|152|Výčet modulů načtených pro doménu aplikace během koncového zchátralého období a je protokolován pro všechny aplikační domény.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ID modulu|vítězství:UInt64|Identifikuje sestavení, do kterého tento modul patří.|  
|ID sestavení|vítězství:UInt64|ID sestavy, ve kterém je tento modul umístěn.|  
|ID domény aplikace|vítězství:UInt64|ID domény aplikace, ve které se tento modul používá.|  
|Příznaky modulu|vítězství:UInt32|0x1: Neutrální modul domény.<br /><br /> 0x2: Modul má nativní obraz.<br /><br /> 0x4: Dynamický modul.<br /><br /> 0x8: Modul manifestu.|  
|Vyhrazeno1|vítězství:UInt32|Rezervované pole.|  
|ModulILPath|win:UnicodeString|Cesta bitové kopie MSIL pro modul nebo název dynamického modulu, pokud se jedná o dynamické sestavení (null ukončeno).|  
|ModulNaVPath|win:UnicodeString|Cesta nativního bitového obrázku modulu, pokud je k dispozici (null ukončeno).|  
|Id instance clr|vítězství:UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  

## <a name="module-range-events"></a>Události rozsahu modulů
 V následující tabulce je uvedeno klíčové slovo a úroveň.  
  
|Klíčové slovo pro zvýšení události|Událost|Úroveň|  
|-----------------------------------|-----------|-----------|  
|`PerfTrackKeyWord`)|`ModuleRange`|Informační (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCStart`|Informační (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCEnd`|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`ModuleRange`|158|Tato událost je k dispozici, pokud načtený nativní image Generátor (NGen) obraz byl optimalizován s IBC a obsahuje informace o horké části obrazu NGen.|  
|`ModuleRangeDCStart`|160|Událost `ModuleRange` vypálená na začátku zchátlého souboru.|  
|`ModuleRangeDCEnd`|161|Událost `ModuleRange` vypálená na konci zchátliny.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Id instance clr|vítězství:UInt16|Jednoznačně identifikuje konkrétní instanci CLR v procesu, pokud je načteno více instancí CLR.|  
|ID modulu|vítězství:UInt64|Identifikuje sestavení, do kterého tento modul patří.|  
|RangeBegin|vítězství:UInt32|Posun v modulu, který představuje začátek rozsahu pro zadaný typ rozsahu.|  
|Velikost rozsahu|vítězství:UInt32|Velikost zadaného rozsahu v bajtech.|  
|RangeType|vítězství:UInt32|Jedna hodnota, 0x4, představující rozsahy Studené IBC. Toto pole může v budoucnu představovat více hodnot.|  
|Velikost rozsahu1|vítězství:UInt32|0 označuje chybná data.|  
|RozsahBegin2|win:UnicodeString||  
  
### <a name="remarks"></a>Poznámky  
 Pokud byl načtený obraz NGen v procesu rozhraní .NET `ModuleRange` Framework optimalizován pomocí protokolu IBC, je událost, `moduleID` `ClrInstanceID`která obsahuje horké rozsahy v bitové kopii NGen, zaznamenána spolu s jeho a .  Pokud bitová kopie NGen není optimalizována s IBC, tato událost není zaznamenána. Chcete-li určit název modulu, musí být tato událost kompletována s událostmi etw zatížení modulu.  
  
 Velikost datové části pro tuto událost je proměnná; `Count` pole označuje počet posunů rozsahu obsažených v události.  Tato událost musí být kompletována s událostí systému Windows `IStart` k určení skutečných rozsahů. Událost Načítání bitových obrázků systému Windows je zaznamenána při každém načtení bitové kopie a obsahuje virtuální adresu načtené bitové kopie.  
  
 Události rozsahu modulu jsou aktivovány pod jakoukoli úroveň ETW větší nebo rovna 4 a jsou klasifikovány jako informační události.  
  
## <a name="see-also"></a>Viz také

- [Události ETW CLR](clr-etw-events.md)
