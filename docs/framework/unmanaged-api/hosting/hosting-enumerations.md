---
title: Výčty hostování
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged enumerations [.NET Framework], hosting
- enumerations [.NET Framework hosting]
- hosting enumerations [.NET Framework]
ms.assetid: e09131eb-1f7d-4f52-ae42-7393e9b62ef6
ms.openlocfilehash: 8edace3191ee4477b19f199d5db6c891c993dcd5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504300"
---
# <a name="hosting-enumerations"></a>Výčty hostování
Tato část popisuje nespravované výčty, které používá rozhraní API pro hostování.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [CLSID_RESOLUTION_FLAGS – výčet](clsid-resolution-flags-enumeration.md)  
 Obsahuje hodnoty, které určují, jak by měl modul CLR (Common Language Runtime) vyřešit `CLSID` .  
  
 [COR_GC_STAT_TYPES – výčet](cor-gc-stat-types-enumeration.md)  
 Určuje statistiku, která má být zaznamenána pro uvolňování paměti.  
  
 [COR_GC_THREAD_STATS_TYPES – výčet](cor-gc-thread-stats-types-enumeration.md)  
 Označuje statistiku uvolňování paměti pro vlákno.  
  
 [EApiCategories – výčet](eapicategories-enumeration.md)  
 Popisuje kategorie schopností, které může hostitel zablokovat, aby běžel v částečně důvěryhodném kódu.  
  
 [EBindPolicyLevels – výčet](ebindpolicylevels-enumeration.md)  
 Poskytuje příznaky, které určují úroveň, na které se má použít nebo upravit zásady sestavení.  
  
 [ECLRAssemblyIdentityFlags – výčet](eclrassemblyidentityflags-enumeration.md)  
 Určuje typ identity sestavení.  
  
 [EClrEvent – výčet](eclrevent-enumeration.md)  
 Popisuje události CLR, pro které může hostitel registrovat zpětná volání.  
  
 [EClrFailure – výčet](eclrfailure-enumeration.md)  
 V této části najdete popis sady selhání, pro které může hostitel nastavit akce zásad.  
  
 [EClrOperation – výčet](eclroperation-enumeration.md)  
 Popisuje sadu operací, pro které může hostitel použít akce zásad.  
  
 [EClrUnhandledException – výčet](eclrunhandledexception-enumeration.md)  
 Popisuje dostupné možnosti pro správu výjimek, které jsou v uživatelském kódu neošetřené.  
  
 [EContextType – výčet](econtexttype-enumeration.md)  
 Popisuje kontext zabezpečení aktuálně zpracovávaného vlákna.  
  
 [ECustomDumpFlavor – výčet](ecustomdumpflavor-enumeration.md)  
 Obsahuje hodnoty, které určují, které položky se mají zahrnout do vlastní podmnožiny výpisu haldy při vytváření sestav chyb.  
  
 [ECustomDumpItemKind – výčet](ecustomdumpitemkind-enumeration.md)  
 Vyhrazeno pro budoucí rozšíření struktury [struktury CustomDumpItem –](customdumpitem-structure.md) .  
  
 [EHostApplicationPolicy – výčet](ehostapplicationpolicy-enumeration.md)  
 Označuje způsob úpravy objektu rozhraní [rozhraní IHostAssemblyManager](ihostassemblymanager-interface.md) . Tento výčet je zastaralý.  
  
 [EHostBindingPolicyModifyFlags – výčet](ehostbindingpolicymodifyflags-enumeration.md)  
 Umožňuje hostiteli zadat typ přesměrování, který má modul CLR provést při použití změn zásad ze zdrojového sestavení na cílové sestavení.  
  
 [EInitializeNewDomainFlags – výčet](einitializenewdomainflags-enumeration.md)  
 Povolí hostiteli poskytovat modul runtime s informacemi o inicializaci domény aplikace.  
  
 [EMemoryAvailable – výčet](ememoryavailable-enumeration.md)  
 Obsahuje hodnoty, které udávají množství volné fyzické paměti v počítači.  
  
 [EMemoryCriticalLevel – výčet](ememorycriticallevel-enumeration.md)  
 Obsahuje hodnoty, které indikují dopad selhání při požadavku na přidělení konkrétní paměti, ale nelze je splnit.  
  
 [EPolicyAction – výčet](epolicyaction-enumeration.md)  
 Popisuje akce zásad, které může hostitel nastavit pro operace popsané ve [výčtu EClrOperation –](eclroperation-enumeration.md) a chyby popsané ve [výčtu EClrFailure –](eclrfailure-enumeration.md).  
  
 [ESymbolReadingPolicy – výčet](esymbolreadingpolicy-enumeration.md)  
 Obsahuje hodnoty, které nastavují zásady pro soubory programu pro čtení databáze programu (PDB).  
  
 [ETaskType – výčet](etasktype-enumeration.md)  
 Obsahuje hodnoty, které označují druh úlohy reprezentované [rozhraním ICLRTask](iclrtask-interface.md) nebo rozhraním [rozhraní IHostTask](ihosttask-interface.md) .  
  
 [HOST_TYPE – výčet](host-type-enumeration.md)  
 Obsahuje hodnoty, které určují typ hostitele, který spouští aplikaci.  
  
 [MALLOC_TYPE – výčet](malloc-type-enumeration.md)  
 Obsahuje hodnoty, které určují charakteristiky přidělené paměti.  
  
 [METAHOST_CONFIG_FLAGS – výčet](metahost-config-flags-enumeration.md)  
 Popisuje možné příznaky vrácené v `pdwConfigFlags` parametru metody [ICLRMetaHostPolicy –:: GetRequestedRuntime –](iclrmetahostpolicy-getrequestedruntime-method.md) .  
  
 [METAHOST_POLICY_FLAGS – výčet](metahost-policy-flags-enumeration.md)  
 Poskytuje zásady vytváření vazeb, které jsou společné pro většinu hostitelů modulu runtime.  
  
 [RUNTIME_INFO_FLAGS – výčet](runtime-info-flags-enumeration.md)  
 Obsahuje hodnoty, které určují, jaké informace o modulu CLR by měly být vráceny.  
  
 [StackOverflowType – výčet](stackoverflowtype-enumeration.md)  
 Obsahuje hodnoty, které indikují základní příčinu události přetečení zásobníku.  
  
 [STARTUP_FLAGS – výčet](startup-flags-enumeration.md)  
 Obsahuje hodnoty, které indikují chování při spuštění modulu CLR.  
  
 [ValidatorFlags – výčet](validatorflags-enumeration.md)  
 Obsahuje hodnoty, které určují typ ověřování, který by měl být proveden ve volání [metody Validate](iclrvalidator-validate-method.md).  
  
 [WAIT_OPTION – výčet](wait-option-enumeration.md)  
 Určuje akci, kterou má hostitel provést, pokud operace vyžadovaná rozhraním CLR zablokuje.  
  
## <a name="related-sections"></a>Související oddíly  
 [Třídy typu coclass hostování](hosting-coclasses.md)  
  
 [Rozhraní pro hostování](hosting-interfaces.md)  
  
 [Zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md)  
  
 [Struktury pro hostování](hosting-structures.md)
