---
title: Události Trasování událostí pro Windows zavaděče
ms.date: 03/30/2017
helpviewer_keywords:
- loader events [.NET Framework]
- ETW, loader events (CLR)
ms.assetid: cb403cc6-56f8-4609-b467-cdfa09f07909
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87ec70b2b27c8886ac9b567498d75f9294437bed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949263"
---
# <a name="loader-etw-events"></a>Události Trasování událostí pro Windows zavaděče
<a name="top"></a> Tyto události shromažďovat informace týkající se načítání a uvolňování domény aplikace, sestavení a modulů.  
  
 Všechny události zavaděče jsou vyvolány `LoaderKeyword` – klíčové slovo (0x8). `DCStart` a `DCEnd` události jsou vyvolány `LoaderRundownKeyword` (0x8) s `StartRundown` / `EndRundown` povolena. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
 Události zavaděče jsou rozděleny do následujících akcí:  
  
- [Události domény aplikace](#application_domain_events)  
  
- [Události zavaděče sestavení CLR](#clr_loader_assembly_events)  
  
- [Události modulu](#module_events)  
  
- [Události modulu CLR domény](#clr_domain_module_events)  
  
- [Rozsah modulu událostí](#module_range_events)  
  
<a name="application_domain_events"></a>   
## <a name="application-domain-events"></a>Události domény aplikace  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|Událost|úroveň|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`AppDomainLoad_V1` a `AppDomainUnLoad_V1`|Informativní (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`AppDomainDCStart_V1`|Informativní (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`AppDomainDCEnd_V1`|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`AppDomainLoad_V1` (zaznamenána pro všechny domény aplikací)|156|Vyvolá se pokaždé, když se po celou dobu životnosti procesu domény aplikace.|  
|`AppDomainUnLoad_V1`|157|Vyvolá se pokaždé, když se po celou dobu životnosti procesu je zničen domény aplikace.|  
|`AppDomainDCStart_V1`|157|Vytvoří výčet domén aplikací během začátek doběhu.|  
|`AppDomainDCEnd_V1`|158|Vytvoří výčet domén aplikací během konec doběhu.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|AppDomainID|win:UInt64|Jedinečný identifikátor pro doménu aplikace.|  
|AppDomainFlags|win:UInt32|0x1: Výchozí doménu.<br /><br /> 0x2: Spustitelný soubor.<br /><br /> 0x4: Domény aplikace bit 28-31: Sdílení zásady této domény.<br /><br /> 0: Sdílené domény.|  
|AppDomainName|win:UnicodeString|Aplikace popisný název domény. Může změnit během životnosti procesu.|  
|AppDomainIndex|Win:UInt32|Index této domény aplikace.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="clr_loader_assembly_events"></a>   
## <a name="clr-loader-assembly-events"></a>Události zavaděče sestavení CLR  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|Událost|úroveň|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`AssemblyLoad` a `AssemblyUnload`|Informativní (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`AssemblyDCStart`|Informativní (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`AssemblyDCEnd`|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`AssemblyLoad_V1`|154|Vyvoláno, když je sestavení načteno.|  
|`AssemblyUnload_V1`|155|Vyvolá se při sestavení je uvolněna.|  
|`AssemblyDCStart_V1`|155|Vytvoří výčet sestavení během začátek doběhu.|  
|`AssemblyDCEnd_V1`|156|Vytvoří výčet sestavení během konec doběhu.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|AssemblyID|win:UInt64|Jedinečné ID pro sestavení.|  
|AppDomainID|win:UInt64|ID domény toto sestavení.|  
|BindingID|win:UInt64|ID, které jednoznačně identifikuje vazby sestavení.|  
|Assemblyflags –|win:UInt32|0x1: Neutrální sestavení domény.<br /><br /> 0x2: Dynamické sestavení.<br /><br /> 0x4: Sestavení nemá nativní bitovou kopii.<br /><br /> 0x8: Kolekční sestavení.|  
|AssemblyName|win:UnicodeString|Plně kvalifikovaný název sestavení.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="module_events"></a>   
## <a name="module-events"></a>Události modulu  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|Událost|úroveň|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`ModuleLoad_V2` a `ModuleUnload_V2`|Informativní (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`ModuleDCStart_V2`|Informativní (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`ModuleDCEnd_V2`|Informativní (4)|  
||||  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`ModuleLoad_V2`|152|Vyvoláno, když je modul je načten během životního cyklu procesu.|  
|`ModuleUnload_V2`|153|Vyvoláno, když modul je uvolněn po celou dobu životnosti procesu.|  
|`ModuleDCStart_V2`|153|Vytvoří výčet modulů během začátek doběhu.|  
|`ModuleDCEnd_V2`|154|Vytvoří výčet modulů během konec doběhu.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ID modulu|win:UInt64|Jedinečné ID pro modul.|  
|AssemblyID|win:UInt64|ID sestavení, ve kterém se nachází tento modul.|  
|ModuleFlags|win:UInt32|0x1: Neutrální modul domény.<br /><br /> 0x2: Modul nemá nativní bitovou kopii.<br /><br /> 0x4: Dynamický modul.<br /><br /> 0x8: Modul manifestu.|  
|Reserved1|win:UInt32|Vyhrazené pole.|  
|ModuleILPath|win:UnicodeString|Cesta k obrázku Microsoft intermediate language (MSIL) pro modul, nebo název dynamického modulu, pokud je dynamické sestavení (zakončený hodnotou null).|  
|ModuleNativePath|win:UnicodeString|Cesta k modulu nativní bitové kopie, pokud jsou k dispozici (zakončený hodnotou null).|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
|ManagedPdbSignature|win:GUID|Podpis GUID databáze spravované programu (PDB), který odpovídá tento modul. (Viz poznámky).|  
|ManagedPdbAge|win:UInt32|Stáří číslo zapsána do spravované PDB, který odpovídá tento modul. (Viz poznámky).|  
|ManagedPdbBuildPath|win:UnicodeString|Cesta k umístění, ve kterém byla vytvořena spravovaná PDB, který odpovídá tento modul. V některých případech to může být pouze název souboru. (Viz poznámky).|  
|NativePdbSignature|win:GUID|Identifikátor GUID podpis Native Image Generator (NGen) PDB, který odpovídá tento modul, pokud je k dispozici. (Viz poznámky).|  
|NativePdbAge|win:UInt32|Stáří číslo zapsána do NGen PDB, který odpovídá tento modul, pokud je k dispozici. (Viz poznámky).|  
|NativePdbBuildPath|win:UnicodeString|Cesta k umístění, kde byl vytvořen NGen PDB, který odpovídá tento modul, pokud je k dispozici. V některých případech to může být pouze název souboru. (Viz poznámky).|  
  
### <a name="remarks"></a>Poznámky  
  
- Pole, která mají "Pdb" v názvu můžete využívat nástroje pro profilaci k vyhledání souborů pdb, které odpovídají moduly, které byly načteny během relace profilování. Hodnoty těchto polí odpovídat data zapsaná do částí IMAGE_DIRECTORY_ENTRY_DEBUG modulu obvykle používají ladicí programy pro usnadnění vyhledání pdb, které odpovídají načtené moduly.  
  
- Názvy polí, které začínají řetězcem "ManagedPdb" odkazovat spravovaný modul MSIL, který byl vygenerován spravované kompilátory odpovídající PDB (například C# nebo kompilátor jazyka Visual Basic). Tento soubor PDB používá spravované formát PDB a popisuje, jak prvky z původní spravovaném zdrojovém kódu, jako jsou soubory, čísla řádků a názvy symbolů se mapují na prvky jazyka MSIL, které jsou kompilovány do modulu MSIL.  
  
- Názvy polí, které začínají řetězcem "NativePdb" odkazovat PDB NGen generován voláním `NGEN createPDB`. Tento soubor PDB využívá nativní formát PDB a popisuje, jak prvky z původní spravovaném zdrojovém kódu, jako jsou soubory, čísla řádků a názvy symbolů se mapují na nativní prvky, které jsou kompilovány do modulu technologie NGen.  
  
 [Zpět na začátek](#top)  
  
<a name="clr_domain_module_events"></a>   
## <a name="clr-domain-module-events"></a>Události modulu CLR domény  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|Událost|úroveň|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|Informativní (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`DomainModuleDCStart_V1`|Informativní (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`DomainModuleDCEnd_V1`|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`DomainModuleLoad_V1`|151|Vyvolá se při načtení modulu pro doménu aplikace.|  
|`DomainModuleDCStart_V1`|151|Vytvoří výčet modulů pro doménu aplikace během začátek doběhu a je zaznamenána pro všechny domény aplikace.|  
|`DomainModuleDCEnd_V1`|152|Vytvoří výčet modulů pro doménu aplikace během konec doběhu a je zaznamenána pro všechny domény aplikace.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ID modulu|win:UInt64|Určuje sestavení, ke kterému patří tento modul.|  
|AssemblyID|win:UInt64|ID sestavení, ve kterém se nachází tento modul.|  
|AppDomainID|win:UInt64|ID domény aplikace 00Z tento modul se používá.|  
|ModuleFlags|win:UInt32|0x1: Neutrální modul domény.<br /><br /> 0x2: Modul nemá nativní bitovou kopii.<br /><br /> 0x4: Dynamický modul.<br /><br /> 0x8: Modul manifestu.|  
|Reserved1|win:UInt32|Vyhrazené pole.|  
|ModuleILPath|win:UnicodeString|Cesta k obrázku jazyka MSIL pro modul, nebo název dynamického modulu, pokud je dynamické sestavení (zakončený hodnotou null).|  
|ModuleNativePath|win:UnicodeString|Cesta k modulu nativní bitové kopie, pokud jsou k dispozici (zakončený hodnotou null).|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="module_range_events"></a>   
## <a name="module-range-events"></a>Rozsah modulu událostí  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|Událost|úroveň|  
|-----------------------------------|-----------|-----------|  
|`PerfTrackKeyWord`)|`ModuleRange`|Informativní (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCStart`|Informativní (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCEnd`|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`ModuleRange`|158|Tato událost je k dispozici, pokud byla optimalizována s IBC načíst image Native Image Generator (NGen) a obsahuje informace o výměně části NGen image.|  
|`ModuleRangeDCStart`|160|A `ModuleRange` událost aktivuje na začátku doběhu.|  
|`ModuleRangeDCEnd`|161|A `ModuleRange` událost vyvolána na konci doběhu.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|win:UInt16|Jednoznačně identifikuje konkrétní instanci modulu CLR v procesu, pokud jsou načteno několik instancí modulu CLR.|  
|ID modulu|win:UInt64|Určuje sestavení, ke kterému patří tento modul.|  
|RangeBegin|win:UInt32|Posun v modulu, který představuje počátek rozsahu pro typ zadaný rozsah.|  
|RangeSize|win:UInt32|Velikost zadaného rozsahu bajtů.|  
|RangeType|win:UInt32|Jednu hodnotu 0x4 k reprezentaci studenou IBC rozsahy. Toto pole může představovat více hodnot v budoucnu.|  
|RangeSize1|win:UInt32|Hodnota 0 znamená chybnými daty.|  
|RangeBegin2|win:UnicodeString||  
  
### <a name="remarks"></a>Poznámky  
 Pokud se IBC, byl optimalizován načíst image NGen v procesu rozhraní .NET Framework `ModuleRange` , který obsahuje aktivní oblastí v NGen image zaznamená se spolu s jeho `moduleID` a `ClrInstanceID`.  Pokud NGen image není optimalizovaná s IBC, tato událost se protokoluje. Pokud chcete zjistit název modulu, musí tato událost porovnávají s události trasování událostí pro Windows načtení modulu.  
  
 Velikost datové části pro tuto událost je proměnné. `Count` pole označuje počet posunů rozsah obsažené v události.  Tato událost má Kompletovat s Windows `IStart` událostí k určení skutečné rozsahy. Událost načtení bitové kopie Windows se protokoluje pokaždé, když se obrázek je načten a obsahuje virtuální adresu načíst obrázek.  
  
 Události modulu rozsahu jsou vyvolávány v libovolné úrovni trasování událostí pro Windows, větší než nebo rovna 4 a jsou klasifikovány jako informační události.  
  
## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
