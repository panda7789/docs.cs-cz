---
title: ICorRuntimeHost – rozhraní
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost
helpviewer_keywords:
- ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ecf6bff10e98ab7f008cfd176f59687f34d89553
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43471952"
---
# <a name="icorruntimehost-interface"></a>ICorRuntimeHost – rozhraní
Poskytuje metody, které umožní hostitele ke spouštění a zastavování common language runtime (CLR) explicitně, vytvoření a konfigurace domény aplikace, pro přístup k výchozí doménu a chcete získat výčet všech doménách spuštěných v rámci procesu.  
  
 V rozhraní .NET Framework verze 2.0, toto rozhraní je nahrazena sadou [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CloseEnum – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-closeenum-method.md)|Obnoví domény enumerátor zpět na začátek seznamu domén.|  
|[CreateDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)|Vytvoří doménu aplikace. Volající přijímá ukazatel rozhraní typu <xref:System._AppDomain> do instance typu <xref:System.AppDomain?displayProperty=nameWithType>.|  
|[CreateDomainEx – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)|Vytvoří doménu aplikace. Tato metoda umožňuje volajícímu předejte instanci iappdomainsetup – ke konfiguraci dalších funkcí vráceného <xref:System._AppDomain> instance.|  
|[CreateDomainSetup – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)|Získá ukazatel rozhraní typu `IAppDomainSetup` do <xref:System.AppDomainSetup> instance. `IAppDomainSetup` poskytuje metody pro konfiguraci aspektů doménu aplikace před jeho vytvoření.|  
|[CreateEvidence – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)|Získá ukazatel rozhraní typu <xref:System.Security.Principal.IIdentity>, což umožňuje hostiteli vytvořit legitimace zabezpečení předat [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) nebo [createdomainex –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md).|  
|[CreateLogicalThreadState – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createlogicalthreadstate-method.md)|Nepoužívejte.|  
|[CurrentDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-currentdomain-method.md)|Získá ukazatel rozhraní typu <xref:System._AppDomain> , která představuje doménu načten v aktuálním vláknu.|  
|[DeleteLogicalThreadState – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-deletelogicalthreadstate-method.md)|Nepoužívejte.|  
|[EnumDomains – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)|Získá enumerátor pro domény v aktuálním procesu.|  
|[GetConfiguration – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getconfiguration-method.md)|Získá objekt, který umožňuje hostiteli zadejte požadovanou konfiguraci zpětného volání modulu CLR.|  
|[GetDefaultDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getdefaultdomain-method.md)|Získá ukazatel rozhraní typu <xref:System._AppDomain> , která představuje výchozí doménu pro aktuální proces.|  
|[LocksHeldByLogicalThread – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-locksheldbylogicalthread-method.md)|Nepoužívejte.|  
|[MapFile – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-mapfile-method.md)|Mapuje zadaný soubor do paměti. Tato metoda je zastaralá.|  
|[NextDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-nextdomain-method.md)|Získá ukazatel rozhraní na další doménu ve výčtu.|  
|[Start – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-start-method.md)|Spuštění modulu CLR.|  
|[Stop – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-stop-method.md)|Zastaví provádění kódu v modulu runtime pro aktuální proces.|  
|[SwitchInLogicalThreadState – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchinlogicalthreadstate-method.md)|Nepoužívejte.|  
|[SwitchOutLogicalThreadState – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchoutlogicalthreadstate-method.md)|Nepoužívejte.|  
|[UnloadDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-unloaddomain-method.md)|Uvolní zadanou doménu aplikace z aktuálního procesu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Viz také  
 <xref:System.AppDomain>  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [ICLRRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [Hostitelská prostředí modulu runtime](https://msdn.microsoft.com/library/99d9246a-b994-4fe5-985c-8588d1d59998)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [CorRuntimeHost – třída typu coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
