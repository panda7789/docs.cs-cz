---
title: Rozhraní hostování CLR přidaná v rozhraní .NET Framework 4 a 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: a524c0b0e01fbde95ce2341874511960b3e5738e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616850"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a>Rozhraní hostování CLR přidaná v rozhraní .NET Framework 4 a 4.5
Tato část popisuje rozhraní, která nespravované hostitele můžou použít k integraci modulu CLR (Common Language Runtime) v .NET Framework 4, .NET Framework 4,5 a novějších verzích do svých aplikací. Tato rozhraní poskytují metody pro hostitele ke konfiguraci a načtení modulu runtime do procesu.  
  
 Počínaje .NET Framework 4 mají všechna hostující rozhraní následující vlastnosti:  
  
- Používají správu životnosti ( `AddRef` a `Release` ), zapouzdření (implicitní kontext) a `QueryInterface` z modelu COM.  
  
- Nepoužívají typy COM, jako například `BSTR` , `SAFEARRAY` nebo `VARIANT` .  
  
- Neexistují žádné modely Apartment, agregace ani aktivace registru, které používají [funkci CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [ICLRAppDomainResourceMonitor – rozhraní](iclrappdomainresourcemonitor-interface.md)  
 Poskytuje metody, které kontrolují paměť a využití procesoru v doméně aplikace.  
  
 [ICLRDomainManager – rozhraní](iclrdomainmanager-interface.md)  
 Umožňuje hostiteli zadat správce aplikační domény, který se použije k inicializaci výchozí domény aplikace, a zadat vlastnosti inicializace.  
  
 [ICLRGCManager2 – rozhraní](iclrgcmanager2-interface.md)  
 Poskytuje metodu [SetGCStartupLimitsEx –](iclrgcmanager2-setgcstartuplimitsex-method.md) , která umožňuje hostiteli nastavit velikost segmentu uvolňování paměti a maximální velikost 0. generace systému uvolňování paměti na hodnoty větší než `DWORD` .  
  
 [ICLRMetaHost – rozhraní](iclrmetahost-interface.md)  
 Poskytuje metody, které vracejí konkrétní verzi CLR, vypíše všechny nainstalované CLRs, vypíše všechny vnitroprocesové moduly runtime, vrátí aktivační rozhraní a zjistí verzi CLR použitou pro zkompilování sestavení.  
  
 [ICLRMetaHostPolicy – rozhraní](iclrmetahostpolicy-interface.md)  
 Poskytuje metodu [GetRequestedRuntime –](iclrmetahostpolicy-getrequestedruntime-method.md) , která poskytuje rozhraní CLR na základě kritérií zásad, spravovaného sestavení, verze a konfiguračního souboru.  
  
 [ICLRRuntimeInfo – rozhraní](iclrruntimeinfo-interface.md)  
 Poskytuje metody, které vracejí informace o konkrétním modulu runtime, včetně verze, adresáře a stavu zatížení.  
  
 [ICLRStrongName – rozhraní](iclrstrongname-interface.md)  
 Poskytuje základní globální statické funkce pro podepisování sestavení se silnými názvy. Všechny metody [ICLRStrongName](iclrstrongname-interface.md) vrací standardní model COM HRESULTs.  
  
 [ICLRStrongName2 – rozhraní](iclrstrongname2-interface.md)  
 Poskytuje možnost vytvářet silné názvy pomocí skupiny SHA-2 algoritmů Secure Hash (SHA-256, SHA-384 a SHA-512).  
  
 [ICLRTask2 – rozhraní](iclrtask2-interface.md)  
 Poskytuje všechny funkce [rozhraní ICLRTask](iclrtask-interface.md); Kromě toho poskytuje metody, které umožňují, aby bylo přerušení vlákna zpožděno v aktuálním vlákně.  
  
## <a name="related-sections"></a>Související oddíly  
 [Zastaralá rozhraní a třídy typu Coclass pro hostování CLR](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Popisuje rozhraní hostování poskytovaná pomocí .NET Framework verze 1,0 a 1,1.  
  
 [Rozhraní hostování CLR](clr-hosting-interfaces.md)  
 Popisuje rozhraní hostování poskytovaná pomocí .NET Framework verze 2,0, 3,0 a 3,5.  
  
 [Hostování](index.md)  
 Zavádí hostování v .NET Framework.
