---
title: Události Trasování událostí pro Windows zavaděče
ms.date: 03/30/2017
helpviewer_keywords:
- loader events [.NET Framework]
- ETW, loader events (CLR)
ms.assetid: cb403cc6-56f8-4609-b467-cdfa09f07909
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6177bdff873feb75eb15dba53bcdb5197260fa9d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046396"
---
# <a name="loader-etw-events"></a>Události Trasování událostí pro Windows zavaděče
<a name="top"></a>Tyto události shromažďují informace týkající se načítání a uvolňování aplikačních domén, sestavení a modulů.  
  
 Všechny události zavaděče jsou vyvolány v rámci `LoaderKeyword` klíčového slova 0x8. `StartRundown` `LoaderRundownKeyword` / Události a jsou vyvolány pod (0x8) s `EndRundown` povolenou. `DCStart` `DCEnd` (Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)  
  
 Události zavaděče jsou rozděleny do následujících možností:  
  
- [Události domény aplikace](#application_domain_events)  
  
- [Události sestavení zavaděče CLR](#clr_loader_assembly_events)  
  
- [Události modulu](#module_events)  
  
- [Události modulu CLR pro domény](#clr_domain_module_events)  
  
- [Události rozsahu modulu](#module_range_events)  
  
<a name="application_domain_events"></a>   
## <a name="application-domain-events"></a>Události domény aplikace  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Událost|Level|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`AppDomainLoad_V1` a `AppDomainUnLoad_V1`|Informační (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`AppDomainDCStart_V1`|Informační (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`AppDomainDCEnd_V1`|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`AppDomainLoad_V1`(protokolováno pro všechny domény aplikace)|156|Vyvolá se vždy, když je vytvořena doména aplikace během životnosti procesu.|  
|`AppDomainUnLoad_V1`|157|Vyvolá se vždy, když je doména aplikace zničena během životnosti procesu.|  
|`AppDomainDCStart_V1`|157|Vytvoří výčet domén aplikace při spuštění doběhu.|  
|`AppDomainDCEnd_V1`|158|Vytvoří výčet aplikačních domén během koncového doběhu.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|AppDomainID|win:UInt64|Jedinečný identifikátor pro doménu aplikace.|  
|AppDomainFlags|Win: UInt32|0x1: Výchozí doména.<br /><br /> 0x2: Spouštěcí.<br /><br /> 0x4: Doména aplikace, bit 28-31: Zásady sdílení této domény<br /><br /> 0: Sdílená doména.|  
|AppDomainName|win:UnicodeString|Popisný název domény aplikace Může dojít ke změně během životnosti procesu.|  
|AppDomainIndex|Win: UInt32|Index této domény aplikace|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="clr_loader_assembly_events"></a>   
## <a name="clr-loader-assembly-events"></a>Události sestavení zavaděče CLR  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Událost|Level|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`AssemblyLoad` a `AssemblyUnload`|Informační (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`AssemblyDCStart`|Informační (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`AssemblyDCEnd`|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`AssemblyLoad_V1`|154|Vyvolá se při načtení sestavení.|  
|`AssemblyUnload_V1`|155|Je aktivována, když je sestavení uvolněno.|  
|`AssemblyDCStart_V1`|155|Vytvoří výčet sestavení během spouštěcího doběhu.|  
|`AssemblyDCEnd_V1`|156|Vytvoří výčet sestavení během koncového doběhu.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|AssemblyID|win:UInt64|Jedinečné ID pro sestavení|  
|AppDomainID|win:UInt64|ID domény tohoto sestavení|  
|BindingID|win:UInt64|ID, které jedinečně identifikuje vazbu sestavení.|  
|AssemblyFlags –|Win: UInt32|0x1: Neutrální sestavení domény<br /><br /> 0x2: Dynamické sestavení.<br /><br /> 0x4: Sestavení má nativní bitovou kopii.<br /><br /> 0x8: Kolekční sestavení.|  
|Doplňk|win:UnicodeString|Plně kvalifikovaný název sestavení.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="module_events"></a>   
## <a name="module-events"></a>Události modulu  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Událost|Level|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`ModuleLoad_V2` a `ModuleUnload_V2`|Informační (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`ModuleDCStart_V2`|Informační (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`ModuleDCEnd_V2`|Informační (4)|  
||||  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`ModuleLoad_V2`|152|Je aktivována, když je modul načten během životnosti procesu.|  
|`ModuleUnload_V2`|153|Je aktivována, když dojde k uvolnění modulu během životnosti procesu.|  
|`ModuleDCStart_V2`|153|Vytvoří výčet modulů během spouštěcího doběhu.|  
|`ModuleDCEnd_V2`|154|Vytvoří výčet modulů během koncového doběhu.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ModuleID|win:UInt64|Jedinečné ID pro modul|  
|AssemblyID|win:UInt64|ID sestavení, ve kterém se nachází tento modul.|  
|ModuleFlags|Win: UInt32|0x1: Neutrální modul domény<br /><br /> 0x2: Modul má nativní bitovou kopii.<br /><br /> 0x4: Dynamický modul.<br /><br /> 0x8: Modul manifestu|  
|Reserved1|Win: UInt32|Rezervované pole|  
|ModuleILPath|win:UnicodeString|Cesta k obrázku jazyka MSIL (Microsoft Intermediate Language) pro modul nebo název dynamického modulu, pokud se jedná o dynamické sestavení (zakončené znakem null).|  
|ModuleNativePath|win:UnicodeString|Cesta k nativní imagi modulu, pokud je k dispozici (zakončené znakem null).|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
|ManagedPdbSignature|Win: GUID|Podpis identifikátoru GUID databáze spravovaného programu (PDB), který odpovídá tomuto modulu. (Viz poznámky.)|  
|ManagedPdbAge|Win: UInt32|Věkové číslo zapsané do spravovaného souboru PDB, který odpovídá tomuto modulu. (Viz poznámky.)|  
|ManagedPdbBuildPath|win:UnicodeString|Cesta k umístění, kde byl sestaven spravovaný soubor PDB odpovídající tomuto modulu. V některých případech to může být jen název souboru. (Viz poznámky.)|  
|NativePdbSignature|Win: GUID|Podpis identifikátoru GUID PDB generátoru nativních imagí (NGen), který odpovídá tomuto modulu (Pokud je k dispozici). (Viz poznámky.)|  
|NativePdbAge|Win: UInt32|Věkové číslo zapsané do souboru PDB NGen, který odpovídá tomuto modulu, pokud je k dispozici. (Viz poznámky.)|  
|NativePdbBuildPath|win:UnicodeString|Cesta k umístění, kde byla sestavena služba NGen PDB odpovídající tomuto modulu, je-li k dispozici. V některých případech to může být jen název souboru. (Viz poznámky.)|  
  
### <a name="remarks"></a>Poznámky  
  
- Pole, která mají v názvech "PDB", můžou používat nástroje pro profilaci k vyhledání soubory PDB, které odpovídají modulům načteným během relace profilování. Hodnoty těchto polí odpovídají datům zapsaným do částí IMAGE_DIRECTORY_ENTRY_DEBUG modulu, které obvykle používají ladicí programy k vyhledání soubory PDB, které odpovídají načteným modulům.  
  
- Názvy polí začínající řetězcem "ManagedPdb" odkazují na Managed PDB odpovídající modulu MSIL, který byl vygenerován spravovaným kompilátorem (například kompilátorem C# nebo Visual Basic). Tento soubor PDB používá spravovaný formát PDB a popisuje, jak prvky z původního spravovaného zdrojového kódu, jako jsou soubory, čísla řádků a názvy symbolů, namapovány na prvky jazyka MSIL, které jsou zkompilovány do modulu MSIL.  
  
- Názvy polí začínající řetězcem "NativePdb" odkazují na Generátor NGen PDB generovaný voláním `NGEN createPDB`. Tento soubor PDB používá nativní formát PDB a popisuje, jak prvky z původního spravovaného zdrojového kódu, jako jsou soubory, čísla řádků a názvy symbolů, se mapují na nativní prvky, které jsou zkompilovány do modulu NGen.  
  
 [Zpět na začátek](#top)  
  
<a name="clr_domain_module_events"></a>   
## <a name="clr-domain-module-events"></a>Události modulu CLR pro domény  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Událost|Level|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|Informační (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`DomainModuleDCStart_V1`|Informační (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`DomainModuleDCEnd_V1`|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`DomainModuleLoad_V1`|151|Je aktivována, když je modul načten pro doménu aplikace.|  
|`DomainModuleDCStart_V1`|151|Vytvoří výčet modulů načtených pro doménu aplikace během spuštění doběhu a zaznamená se do protokolu pro všechny domény aplikace.|  
|`DomainModuleDCEnd_V1`|152|Vytvoří výčet modulů načtených pro doménu aplikace během ukončení doběhu a zaznamená se do protokolu pro všechny domény aplikace.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ModuleID|win:UInt64|Identifikuje sestavení, ke kterému tento modul patří.|  
|AssemblyID|win:UInt64|ID sestavení, ve kterém se nachází tento modul.|  
|AppDomainID|win:UInt64|ID domény aplikace, ve které se tento modul používá|  
|ModuleFlags|Win: UInt32|0x1: Neutrální modul domény<br /><br /> 0x2: Modul má nativní bitovou kopii.<br /><br /> 0x4: Dynamický modul.<br /><br /> 0x8: Modul manifestu|  
|Reserved1|Win: UInt32|Rezervované pole|  
|ModuleILPath|win:UnicodeString|Cesta k obrázku jazyka MSIL pro modul nebo název dynamického modulu, pokud se jedná o dynamické sestavení (zakončené znakem null).|  
|ModuleNativePath|win:UnicodeString|Cesta k nativní imagi modulu, pokud je k dispozici (zakončené znakem null).|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="module_range_events"></a>   
## <a name="module-range-events"></a>Události rozsahu modulu  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Událost|Level|  
|-----------------------------------|-----------|-----------|  
|`PerfTrackKeyWord`)|`ModuleRange`|Informační (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCStart`|Informační (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCEnd`|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`ModuleRange`|158|Tato událost je přítomna v případě, že načtená image generátoru nativních bitových kopií (NGen) je optimalizovaná pomocí daty IBC a obsahuje informace o aktivních oddílech image NGen.|  
|`ModuleRangeDCStart`|160|`ModuleRange` Událost aktivovaná na začátku doběhu|  
|`ModuleRangeDCEnd`|161|`ModuleRange` Událost aktivovaná na konci doběhu|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Win: UInt16|Jednoznačně identifikuje konkrétní instanci CLR v procesu, pokud je načteno více instancí modulu CLR.|  
|ModuleID|win:UInt64|Identifikuje sestavení, ke kterému tento modul patří.|  
|RangeBegin|Win: UInt32|Posun v modulu, který představuje začátek rozsahu zadaného typu rozsahu.|  
|RangeSize|Win: UInt32|Velikost zadaného rozsahu v bajtech|  
|Hodnotu RangeType|Win: UInt32|Jedna hodnota 0x4, která představuje studené daty IBC rozsahy. Toto pole může v budoucnu představovat více hodnot.|  
|RangeSize1|Win: UInt32|0 označuje chybná data.|  
|RangeBegin2|win:UnicodeString||  
  
### <a name="remarks"></a>Poznámky  
 Pokud byla načtená image Ngen v procesu .NET Framework optimalizovaná pomocí daty IBC, `ModuleRange` událost obsahující aktivní rozsahy v imagi Ngen se zaprotokoluje společně s jejími `moduleID` a `ClrInstanceID`.  Pokud není image NGen optimalizovaná pomocí daty IBC, tato událost se neprotokoluje. Chcete-li určit název modulu, musí být tato událost řazena s událostmi trasování událostí pro Windows načtení modulu.  
  
 Velikost datové části pro tuto událost je proměnná. `Count` pole indikuje počet posunů rozsahu obsažených v události.  Tato událost musí být seřazena s událostí systému Windows `IStart` , aby bylo možné určit skutečné rozsahy. Událost načtení bitové kopie systému Windows se zaprotokoluje při každém načtení image a obsahuje virtuální adresu načteného obrázku.  
  
 Události rozsahu modulu se vystavují v jakékoli úrovni ETW, která je větší nebo se rovná 4, a jsou klasifikované jako informativní události.  
  
## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](clr-etw-events.md)
