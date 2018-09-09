---
title: Rozhraní hostování CLR přidaná v rozhraní .NET Framework 4 a 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9086502968fb9046237e77b76b4038a9f32f4ef
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253088"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a>Rozhraní hostování CLR přidaná v rozhraní .NET Framework 4 a 4.5
Tato část popisuje nespravovaná rozhraní můžete integrovat common language runtime (CLR) v nastavení používají hostitelé [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]a novějších verzí do svých aplikací. Tato rozhraní poskytuje metody pro hostitele konfigurace a načtení modulu runtime do procesu.  
  
 Počínaje [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], všechny hostitelské rozhraní mají následující vlastnosti:  
  
-   Správa životního cyklu používají (`AddRef` a `Release`), zapouzdření (implicitní context) a `QueryInterface` z modelu COM.  
  
-   Existuje nepoužívejte typy modelu COM, jako `BSTR`, `SAFEARRAY`, nebo `VARIANT`.  
  
-   Neexistují žádné modely objektu apartment, agregace nebo aktivace registru, použít [funkce CoCreateInstance](https://go.microsoft.com/fwlink/?LinkId=142894).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [ICLRAppDomainResourceMonitor – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 Poskytuje metody, které se kontrolovat využití procesoru a paměti doménu aplikace.  
  
 [ICLRDomainManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 Umožňuje hostiteli určit, který se použije k inicializaci výchozí domény aplikace a k určení vlastností inicializace správce domény aplikace.  
  
 [ICLRGCManager2 – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 Poskytuje [setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metodu, která umožňuje hostiteli nastavte velikost segmentu kolekce uvolnění paměti a maximální velikost 0. generace kolekce systému uvolňování paměti na hodnoty vyšší než `DWORD`.  
  
 [ICLRMetaHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 Poskytuje metody vrátit konkrétní verzi modulu CLR, seznam všech nainstalovaných CLRs, vypsat všechny moduly Runtime v procesu, vrátí rozhraní aktivace a zjistit verzi modulu CLR použitou ke kompilaci sestavení.  
  
 [ICLRMetaHostPolicy – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 Poskytuje [getrequestedruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metodu, která poskytuje rozhraní CLR na základě kritérií zásad, spravované sestavení, verzi a konfigurační soubor.  
  
 [ICLRRuntimeInfo – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 Poskytuje metody, které vracejí informace o konkrétní modulu runtime, včetně verze, adresáře a načíst stav.  
  
 [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 Poskytuje základní globální statické funkce pro podepisování sestavení se silnými názvy. Všechny [iclrstrongname –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) metody vrací standardní COM HRESULT.  
  
 [ICLRStrongName2 – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 Umožňuje vytvořit silné názvy pomocí algoritmu SHA-2 skupiny Hashovacích algoritmů zabezpečení (SHA-256, SHA-384 a SHA-512).  
  
 [ICLRTask2 – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 Obsahuje všechny funkce, které jsou součástí [iclrtask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); navíc poskytuje metody, které umožňují zrušení vláken k zpozdit u aktuálního vlákna.  
  
## <a name="related-sections"></a>Související oddíly  
 [Zastaralá rozhraní a třídy typu Coclass pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Popisuje rozhraní hostování, opatřeného rozhraní .NET Framework verze 1.0 a 1.1.  
  
 [Rozhraní pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 Popisuje rozhraní hostování, opatřeného rozhraní .NET Framework verze 2.0, 3.0 a 3.5.  
  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 Zavádí hostování v rozhraní .NET Framework.
