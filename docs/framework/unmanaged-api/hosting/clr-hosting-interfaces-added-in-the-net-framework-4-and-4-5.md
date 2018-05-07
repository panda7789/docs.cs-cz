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
ms.openlocfilehash: 982f5780a40dd8cbce02ec33f7e6f77589cd3717
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a>Rozhraní hostování CLR přidaná v rozhraní .NET Framework 4 a 4.5
Tato část popisuje rozhraní, která nespravované hostitelů můžete použít k integraci common language runtime (CLR) v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]a novější verze do svých aplikací. Tato rozhraní poskytují metody pro hostitele ke konfiguraci a načtení modulu runtime do procesu.  
  
 Od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], všechny hostingu rozhraní mít následující vlastnosti:  
  
-   Používají správu životního cyklu (`AddRef` a `Release`), zapouzdření (implicitní kontextu) a `QueryInterface` z modelu COM.  
  
-   Existuje nepoužívejte typy modelu COM, jako `BSTR`, `SAFEARRAY`, nebo `VARIANT`.  
  
-   Nejsou žádné modely typu apartment, agregace nebo registru aktivace, použít [funkce CoCreateInstance](http://go.microsoft.com/fwlink/?LinkId=142894).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [ICLRAppDomainResourceMonitor – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 Poskytuje metody, které zkontrolovat doménu aplikace využití paměti a procesoru.  
  
 [ICLRDomainManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 Umožňuje na hostiteli a poté zadejte správce domény aplikace, který se použije k chybě při inicializaci výchozí doméně aplikace a k určení inicializační vlastnosti.  
  
 [ICLRGCManager2 – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 Poskytuje [setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metoda, která umožňuje pro hostitele a nastavte velikost segmentu kolekce paměti a maximální velikost systém kolekce paměti generace 0 hodnoty větší než `DWORD`.  
  
 [ICLRMetaHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 Poskytuje metody vrátit konkrétní verzi modulu CLR se zobrazí seznam všech nainstalovaných CLRs, seznamu všechny moduly Runtime v procesu, vraťte rozhraní aktivace a zjistit verze CLR používá ke kompilaci sestavení.  
  
 [ICLRMetaHostPolicy – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 Poskytuje [getrequestedruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metoda, která poskytuje CLR rozhraní na základě zásad kritéria, spravované sestavení, verze a konfigurační soubor.  
  
 [ICLRRuntimeInfo – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 Poskytuje metody, které vracejí informace o konkrétní modul runtime, včetně verze, adresář a stavové zatížení.  
  
 [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 Poskytuje základní globální statické funkce pro podepisování sestavení se silnými názvy. Všechny [iclrstrongname –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) metody vrací standardní hodnoty HRESULT COM.  
  
 [ICLRStrongName2 – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 Poskytuje možnost vytvořit silné názvy pomocí skupiny zabezpečení (SHA-256, SHA-384 a SHA-512) algoritmy Hash SHA-2.  
  
 [ICLRTask2 – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 Obsahuje všechny funkce [iclrtask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); kromě toho poskytuje metody, které umožňují zrušení vláken na opožděno na aktuální vlákno.  
  
## <a name="related-sections"></a>Související oddíly  
 [Zastaralá rozhraní a třídy typu Coclass pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Popisuje rozhraní hostování součástí rozhraní .NET Framework verze 1.0 a 1.1.  
  
 [Rozhraní pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 Popisuje rozhraní hostování součástí rozhraní .NET Framework verze 2.0, 3.0 a 3.5.  
  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 Představuje hostování v rozhraní .NET Framework.
