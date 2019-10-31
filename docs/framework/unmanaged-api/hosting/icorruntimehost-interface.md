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
ms.openlocfilehash: e66e1468a864ec85d88f759c481c7a9707d37f7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139545"
---
# <a name="icorruntimehost-interface"></a>ICorRuntimeHost – rozhraní
Poskytuje metody, které umožňují hostiteli explicitně spustit a zastavit modul CLR (Common Language Runtime), vytvořit a nakonfigurovat domény aplikace, získat přístup k výchozí doméně a vytvořit výčet všech domén spuštěných v procesu.  
  
 V .NET Framework verze 2,0 je toto rozhraní nahrazeno [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CloseEnum – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-closeenum-method.md)|Obnoví enumerátor domény zpátky na začátek seznamu domén.|  
|[CreateDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)|Vytvoří doménu aplikace. Volající obdrží ukazatel rozhraní typu <xref:System._AppDomain> do instance typu <xref:System.AppDomain?displayProperty=nameWithType>.|  
|[CreateDomainEx – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)|Vytvoří doménu aplikace. Tato metoda umožňuje volajícímu předat instanci IAppDomainSetup – ke konfiguraci dalších funkcí vrácené instance <xref:System._AppDomain>.|  
|[CreateDomainSetup – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)|Získá ukazatel rozhraní typu `IAppDomainSetup` k instanci <xref:System.AppDomainSetup>. `IAppDomainSetup` poskytuje metody pro konfiguraci aspektů aplikační domény před jejich vytvořením.|  
|[CreateEvidence – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)|Získá ukazatel rozhraní typu <xref:System.Security.Principal.IIdentity>, který umožňuje hostiteli vytvořit legitimaci zabezpečení pro předání do [CreateDomain –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) nebo [CreateDomainEx –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md).|  
|[CreateLogicalThreadState – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createlogicalthreadstate-method.md)|Nepoužívejte.|  
|[CurrentDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-currentdomain-method.md)|Načte ukazatel rozhraní typu <xref:System._AppDomain>, který představuje doménu načtenou v aktuálním vlákně.|  
|[DeleteLogicalThreadState – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-deletelogicalthreadstate-method.md)|Nepoužívejte.|  
|[EnumDomains – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)|Získá enumerátor pro domény v aktuálním procesu.|  
|[GetConfiguration – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getconfiguration-method.md)|Získává objekt, který umožňuje hostiteli určit konfiguraci zpětného volání CLR.|  
|[GetDefaultDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getdefaultdomain-method.md)|Načte ukazatel rozhraní typu <xref:System._AppDomain>, který představuje výchozí doménu pro aktuální proces.|  
|[LocksHeldByLogicalThread – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-locksheldbylogicalthread-method.md)|Nepoužívejte.|  
|[MapFile – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-mapfile-method.md)|Namapuje zadaný soubor na paměť. Tato metoda je zastaralá.|  
|[NextDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-nextdomain-method.md)|Získá ukazatel rozhraní do další domény ve výčtu.|  
|[Start – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-start-method.md)|Spustí modul CLR.|  
|[Stop – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-stop-method.md)|Zastaví provádění kódu v modulu runtime pro aktuální proces.|  
|[SwitchInLogicalThreadState – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchinlogicalthreadstate-method.md)|Nepoužívejte.|  
|[SwitchOutLogicalThreadState – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchoutlogicalthreadstate-method.md)|Nepoužívejte.|  
|[UnloadDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-unloaddomain-method.md)|Uvolní zadanou doménu aplikace z aktuálního procesu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** 1,0, 1,1  
  
## <a name="see-also"></a>Viz také:

- <xref:System.AppDomain>
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [Hostitelé modulu runtime](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost – třída typu coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
