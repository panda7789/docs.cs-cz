---
title: Události Trasování událostí pro Windows zavaděče
ms.date: 03/30/2017
helpviewer_keywords:
- loader events [.NET Framework]
- ETW, loader events (CLR)
ms.assetid: cb403cc6-56f8-4609-b467-cdfa09f07909
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4746e9e7c8c83caf09ccf51749e9e3cbe69ec52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="loader-etw-events"></a>Události Trasování událostí pro Windows zavaděče
<a name="top"></a> Tyto události shromažďovat informace týkající se načítání a uvolnění domény aplikace, sestavení a moduly.  
  
 Všechny události zavaděče jsou vyvolány v části `LoaderKeyword` – klíčové slovo (0x8). `DCStart` a `DCEnd` události jsou vyvolány v části `LoaderRundownKeyword` (0x8) s `StartRundown` / `EndRundown` povolena. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
 Události zavaděče jsou rozděleny do následující:  
  
-   [Události domény aplikace](#application_domain_events)  
  
-   [Události sestavení CLR zavaděče](#clr_loader_assembly_events)  
  
-   [Události modulu](#module_events)  
  
-   [Události modulu CLR domény](#clr_domain_module_events)  
  
-   [Rozsah modulu události](#module_range_events)  
  
<a name="application_domain_events"></a>   
## <a name="application-domain-events"></a>Události domény aplikace  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|Událost|úroveň|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`AppDomainLoad_V1` A `AppDomainUnLoad_V1`|Informativní (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`AppDomainDCStart_V1`|Informativní (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`AppDomainDCEnd_V1`|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`AppDomainLoad_V1` (přihlášení pro všechny domény aplikace)|156|Vyvolána vždy, když během doby platnosti procesu dojde k vytvoření domény aplikace.|  
|`AppDomainUnLoad_V1`|157|Vyvolána vždy, když během doby platnosti procesu zničena domény aplikace.|  
|`AppDomainDCStart_V1`|157|Vytvoří výčet aplikační domény při spuštění rundown.|  
|`AppDomainDCEnd_V1`|158|Vytvoří výčet aplikační domény během rundown end.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|AppDomainID|Win: UInt64|Jedinečný identifikátor pro doménu aplikace.|  
|AppDomainFlags|Win: UInt32|0x1: výchozí doménu.<br /><br /> 0x2: spustitelný soubor.<br /><br /> 0x4: aplikační domény bit 28-31: sdílení zásady tuto doménu.<br /><br /> 0: sdílené domény.|  
|AppDomainName|Win: UnicodeString|Aplikace popisný název domény. Může se měnit po dobu životnosti procesu.|  
|AppDomainIndex|Win: UInt32|Index tuto doménu aplikace.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="clr_loader_assembly_events"></a>   
## <a name="clr-loader-assembly-events"></a>Události sestavení CLR zavaděče  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|Událost|úroveň|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`AssemblyLoad` A `AssemblyUnload`|Informativní (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`AssemblyDCStart`|Informativní (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`AssemblyDCEnd`|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`AssemblyLoad_V1`|154|Vyvolá, když je načteno sestavení.|  
|`AssemblyUnload_V1`|155|Vyvolá, když je odpojen sestavení.|  
|`AssemblyDCStart_V1`|155|Vytvoří výčet sestavení během spuštění rundown.|  
|`AssemblyDCEnd_V1`|156|Vytvoří výčet sestavení během rundown end.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|AssemblyID|Win: UInt64|Jedinečné ID pro sestavení.|  
|AppDomainID|Win: UInt64|ID domény toto sestavení.|  
|BindingID|Win: UInt64|ID, která jednoznačně identifikuje vazby sestavení.|  
|AssemblyFlags|Win: UInt32|0x1: neutrální sestavení domény.<br /><br /> 0x2: dynamické sestavení.<br /><br /> 0x4: sestavení má nativních bitových kopií.<br /><br /> 0x8: collectible sestavení.|  
|AssemblyName|Win: UnicodeString|Plně kvalifikovaný název sestavení.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="module_events"></a>   
## <a name="module-events"></a>Události modulu  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|Událost|úroveň|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`ModuleLoad_V2` A `ModuleUnload_V2`|Informativní (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`ModuleDCStart_V2`|Informativní (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`ModuleDCEnd_V2`|Informativní (4)|  
||||  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`ModuleLoad_V2`|152|Vyvolá, když modul je načtena po dobu platnosti procesu.|  
|`ModuleUnload_V2`|153|Vyvolá, když modul je odpojen po dobu platnosti procesu.|  
|`ModuleDCStart_V2`|153|Vytvoří výčet moduly během spuštění rundown.|  
|`ModuleDCEnd_V2`|154|Vytvoří výčet moduly během rundown end.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ID modulu|Win: UInt64|Jedinečné ID pro modul.|  
|AssemblyID|Win: UInt64|ID sestavení, ve které tento modul nachází.|  
|ModuleFlags|Win: UInt32|0x1: neutrální modul domény.<br /><br /> 0x2: modul má nativních bitových kopií.<br /><br /> 0x4: dynamické modulu.<br /><br /> 0x8: manifestu modulu.|  
|Reserved1|Win: UInt32|Vyhrazené pole.|  
|ModuleILPath|Win: UnicodeString|Cesta k obrázku (MSIL intermediate language) společnosti Microsoft pro modul, nebo název dynamického modulu, pokud je dynamická sestavení (ukončené hodnotou null).|  
|ModuleNativePath|Win: UnicodeString|Cesta k obrázku nativní modul, pokud je k dispozici (ukončené hodnotou null).|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
|ManagedPdbSignature|Win: GUID|Identifikátor GUID podpis databázi spravovaný program (PDB), který odpovídá tento modul. (Viz poznámky.)|  
|ManagedPdbAge|Win: UInt32|Stáří číslo zapsána do spravovaných PDB, který odpovídá tento modul. (Viz poznámky.)|  
|ManagedPdbBuildPath|Win: UnicodeString|Cesta k umístění, kde spravované PDB, který odpovídá tento modul byl sestaven. V některých případech to může být jen název souboru. (Viz poznámky.)|  
|NativePdbSignature|Win: GUID|Identifikátor GUID podpis generátor (NGen) PDB odpovídající tento modul, pokud je k dispozici. (Viz poznámky.)|  
|NativePdbAge|Win: UInt32|Stáří číslo zapsána do souboru PDB NGen, který odpovídá tento modul, pokud je k dispozici. (Viz poznámky.)|  
|NativePdbBuildPath|Win: UnicodeString|Cesta k umístění, kde byl sestaven NGen PDB, který odpovídá tento modul, pokud je k dispozici. V některých případech to může být jen název souboru. (Viz poznámky.)|  
  
### <a name="remarks"></a>Poznámky  
  
-   Pole, které jsou v jejich názvy "Pdb" lze pomocí nástroje pro profilaci najít soubory PDB, které odpovídají moduly, které byly načteny během relace profilování. Data zapsaná do částí IMAGE_DIRECTORY_ENTRY_DEBUG modulu obvykle používané ladicí programy pro usnadnění vyhledání soubory PDB, které odpovídají načíst moduly odpovídají hodnoty těchto polí.  
  
-   Názvy polí, které začínají "ManagedPdb" naleznete spravované PDB odpovídající MSIL modul, který byl vygenerován spravované kompilátorem (například kompilátor jazyka C# nebo Visual Basic). Tato PDB používá formát spravované PDB a popisuje, jak elementy z původní spravované zdrojového kódu, jako jsou soubory, čísla řádků a názvy symbolů, mapování na MSIL elementy, které jsou zkompilovány do modulu MSIL.  
  
-   Názvy polí, které začínají "NativePdb" odkazovat na PDB NGen generované volání `NGEN createPDB`. Tato PDB používá nativní formát PDB a popisuje, jak elementy z původní spravované zdrojového kódu, jako jsou soubory, čísla řádků a názvy symbolů, mapování na nativní prvky, které jsou zkompilovány do modulu NGen.  
  
 [Zpět na začátek](#top)  
  
<a name="clr_domain_module_events"></a>   
## <a name="clr-domain-module-events"></a>Události modulu CLR domény  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|Událost|úroveň|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|Informativní (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`DomainModuleDCStart_V1`|Informativní (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`DomainModuleDCEnd_V1`|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`DomainModuleLoad_V1`|151|Vyvolá, když modul je načtena pro doménu aplikace.|  
|`DomainModuleDCStart_V1`|151|Vytvoří výčet moduly načtené pro doménu aplikace během spuštění rundown a je zaznamenána pro všechny domény aplikace.|  
|`DomainModuleDCEnd_V1`|152|Vytvoří výčet moduly načtené pro doménu aplikace během rundown end a je zaznamenána pro všechny domény aplikace.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ID modulu|Win: UInt64|Identifikuje sestavení, ke kterému patří tento modul.|  
|AssemblyID|Win: UInt64|ID sestavení, ve které tento modul nachází.|  
|AppDomainID|Win: UInt64|ID domény aplikace, ve kterém se tento modul se používá.|  
|ModuleFlags|Win: UInt32|0x1: neutrální modul domény.<br /><br /> 0x2: modul má nativních bitových kopií.<br /><br /> 0x4: dynamické modulu.<br /><br /> 0x8: manifestu modulu.|  
|Reserved1|Win: UInt32|Vyhrazené pole.|  
|ModuleILPath|Win: UnicodeString|Cesta k obrázku MSIL pro modul, nebo název dynamického modulu, pokud je dynamická sestavení (ukončené hodnotou null).|  
|ModuleNativePath|Win: UnicodeString|Cesta k obrázku nativní modul, pokud je k dispozici (ukončené hodnotou null).|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="module_range_events"></a>   
## <a name="module-range-events"></a>Rozsah modulu události  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|Událost|úroveň|  
|-----------------------------------|-----------|-----------|  
|`PerfTrackKeyWord`)|`ModuleRange`|Informativní (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCStart`|Informativní (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCEnd`|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`ModuleRange`|158|Tato událost je přítomen, pokud bylo optimalizováno s b-ISDN bitovou kopii načíst generátor (NGen) a obsahuje informace o aktivní části NGen bitové kopie.|  
|`ModuleRangeDCStart`|160|A `ModuleRange` na začátku rundown je aktivována událost.|  
|`ModuleRangeDCEnd`|161|A `ModuleRange` událost je aktivována na konci rundown.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Win: UInt16|Pokud jsou načteno několik instancí CLR jednoznačně identifikuje konkrétní instanci modulu CLR v procesu.|  
|ID modulu|Win: UInt64|Identifikuje sestavení, ke kterému patří tento modul.|  
|RangeBegin|Win: UInt32|Posun v modul, který představuje počátek rozsahu pro typ zadaný rozsah.|  
|RangeSize|Win: UInt32|Velikost v bajtech zadaný rozsah.|  
|RangeType|Win: UInt32|Jednu hodnotu 0x4 představují rozsahy Cold b-ISDN. Toto pole může představovat více hodnot v budoucnu.|  
|RangeSize1|Win: UInt32|Hodnota 0 znamená chybná data.|  
|RangeBegin2|Win: UnicodeString||  
  
### <a name="remarks"></a>Poznámky  
 Pokud bylo optimalizováno NGen bitovou kopii načíst v rozhraní .NET Framework procesu s b-ISDN, `ModuleRange` je zaznamenána událost, který obsahuje aktivní rozsahy v bitové kopii NGen spolu s jeho `moduleID` a `ClrInstanceID`.  Pokud bitovou kopii NGen není optimalizována s b-ISDN, tato událost se neprotokolují. Pokud chcete zjistit název modulu, musí tato událost porovnávají s události modulu načtení trasování událostí pro Windows.  
  
 Velikost datové části pro tuto událost je proměnná; `Count` pole označuje číslo, odsazení rozsahu obsažené v události.  Tato událost má Kompletovat s Windows `IStart` událostí k určení skutečné rozsahy. Načtení bitové kopie systému Windows událost zaznamená vždy, když je načteno bitovou kopii a obsahuje virtuální adresu načíst bitové kopie.  
  
 Události modulu rozsah při vyvolání pod všechny úrovně ETW větší než nebo rovna hodnotě 4 a jsou klasifikovány jako informační události.  
  
## <a name="see-also"></a>Viz také  
 [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
