---
title: "Výčty hostování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged enumerations [.NET Framework], hosting
- enumerations [.NET Framework hosting]
- hosting enumerations [.NET Framework]
ms.assetid: e09131eb-1f7d-4f52-ae42-7393e9b62ef6
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc6b5df39c9fad6182f0ee6e4ff95638e9aaf448
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-enumerations"></a>Výčty hostování
Tato část popisuje nespravovaná vyčíslení, které používá rozhraní API hostování.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [CLSID_RESOLUTION_FLAGS – výčet](../../../../docs/framework/unmanaged-api/hosting/clsid-resolution-flags-enumeration.md)  
 Obsahuje hodnoty, které označují, jak by měla vyřešit common language runtime (CLR) `CLSID`.  
  
 [COR_GC_STAT_TYPES – výčet](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)  
 Určuje statistiky, které mají být zaznamenány pro uvolnění paměti.  
  
 [COR_GC_THREAD_STATS_TYPES – výčet](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-types-enumeration.md)  
 Označuje statistiku kolekce paměti na vlákno.  
  
 [EApiCategories – výčet](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 Popisuje kategorie funkcí, které hostitele může blokovat ve spuštění v částečně důvěryhodným kódem.  
  
 [EBindPolicyLevels – výčet](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md)  
 Poskytuje příznaky, které určují úroveň, kdy má nastavení nebo změna zásad sestavení.  
  
 [ECLRAssemblyIdentityFlags – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md)  
 Určuje typ identity sestavení.  
  
 [EClrEvent – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 Popisuje události CLR, pro které hostitele může registrace zpětných volání.  
  
 [EClrFailure – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 Popisuje sadu chyb, pro které hostitele může nastavit zásady akce.  
  
 [EClrOperation – výčet](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 Popisuje sadu operací, pro které můžete použít hostitele akce zásad.  
  
 [EClrUnhandledException – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)  
 Popisuje dostupné možnosti pro správu výjimky, které jsou neošetřené v uživatelském kódu.  
  
 [EContextType – výčet](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 Popisuje kontext zabezpečení aktuálně prováděné vlákno.  
  
 [ECustomDumpFlavor – výčet](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 Obsahuje hodnoty, které označují, které položky, které chcete zahrnout do podmnožinu haldy vlastní dump při zasílání zpráv o chybách.  
  
 [ECustomDumpItemKind – výčet](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 Vyhrazeno pro budoucí rozšíření [customdumpitem – struktura](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) struktura.  
  
 [EHostApplicationPolicy – výčet](../../../../docs/framework/unmanaged-api/hosting/ehostapplicationpolicy-enumeration.md)  
 Určuje, jak upravit [ihostassemblymanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md) rozhraní objektu. Tento výčet je zastaralá.  
  
 [EHostBindingPolicyModifyFlags – výčet](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md)  
 Umožňuje hostiteli určovat typ přesměrování, které modulu CLR by měla provádět při použití změny zásad ze sestavení zdrojové do cílové sestavení.  
  
 [EInitializeNewDomainFlags – výčet](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)  
 Umožňuje hostitele modulu runtime poskytnout informace o inicializaci domény aplikace.  
  
 [EMemoryAvailable – výčet](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md)  
 Obsahuje hodnoty, které označují množství volného fyzické paměti v počítači.  
  
 [EMemoryCriticalLevel – výčet](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)  
 Obsahuje hodnoty, které označují dopad selhání při přidělování konkrétní paměti bylo vyzváno, ale nemůže být splněna.  
  
 [EPolicyAction – výčet](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 Popisuje akce zásad, které jsou hostiteli můžete nastavit pro operace popsaného [EClrOperation – výčet](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) a selhání popsaného [EClrFailure – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).  
  
 [ESymbolReadingPolicy – výčet](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md)  
 Obsahuje hodnoty, které nastavit zásady pro soubory databáze (PDB) program pro čtení.  
  
 [ETaskType – výčet](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md)  
 Obsahuje hodnoty, které označují druh úloh reprezentována [iclrtask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) nebo [ihosttask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) rozhraní.  
  
 [HOST_TYPE – výčet](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md)  
 Obsahuje hodnoty, které určují typ hostitele, který je spuštění aplikace.  
  
 [MALLOC_TYPE – výčet](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md)  
 Obsahuje hodnoty, které určují charakteristiky paměti, které je právě přiděleno.  
  
 [METAHOST_CONFIG_FLAGS – výčet](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md)  
 Popisuje možné příznaky, vrátí se v `pdwConfigFlags` parametr [iclrmetahostpolicy::getrequestedruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metoda.  
  
 [METAHOST_POLICY_FLAGS – výčet](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)  
 Poskytuje vazby zásady, které jsou společné pro většinu modulu runtime.  
  
 [RUNTIME_INFO_FLAGS – výčet](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)  
 Obsahuje hodnoty, které označují, jaké informace o modulu CLR by měla být vrácena.  
  
 [StackOverflowType – výčet](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md)  
 Obsahuje hodnoty, které označují základní příčinu události přetečení zásobníku.  
  
 [STARTUP_FLAGS – výčet](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)  
 Obsahuje hodnoty, které označují chování při spouštění modulu CLR.  
  
 [ValidatorFlags – výčet](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)  
 Obsahuje hodnoty, které označují typ ověření, která má být provedena ve volání [metoda ověření](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md).  
  
 [WAIT_OPTION – výčet](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)  
 Určuje akci, kterou hostitele by měla provést, pokud operace požadoval bloky CLR.  
  
## <a name="related-sections"></a>Související oddíly  
 [Třídy typu coclass pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
  
 [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [Struktury pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
