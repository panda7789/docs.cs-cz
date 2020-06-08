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
ms.openlocfilehash: 4b8018bb84dea08987d91f351b1ab0d9f3b48c56
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503897"
---
# <a name="icorruntimehost-interface"></a>ICorRuntimeHost – rozhraní
Poskytuje metody, které umožňují hostiteli explicitně spustit a zastavit modul CLR (Common Language Runtime), vytvořit a nakonfigurovat domény aplikace, získat přístup k výchozí doméně a vytvořit výčet všech domén spuštěných v procesu.  
  
 V .NET Framework verze 2,0 je toto rozhraní nahrazeno [ICLRRuntimeHost](iclrruntimehost-interface.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[CloseEnum – metoda](icorruntimehost-closeenum-method.md)|Obnoví enumerátor domény zpátky na začátek seznamu domén.|  
|[CreateDomain – metoda](icorruntimehost-createdomain-method.md)|Vytvoří doménu aplikace. Volající obdrží ukazatel rozhraní typu <xref:System._AppDomain> na instanci typu <xref:System.AppDomain?displayProperty=nameWithType> .|  
|[CreateDomainEx – metoda](icorruntimehost-createdomainex-method.md)|Vytvoří doménu aplikace. Tato metoda umožňuje volajícímu předat instanci IAppDomainSetup – ke konfiguraci dalších funkcí vrácené <xref:System._AppDomain> instance.|  
|[CreateDomainSetup – metoda](icorruntimehost-createdomainsetup-method.md)|Načte ukazatel rozhraní typu `IAppDomainSetup` na <xref:System.AppDomainSetup> instanci. `IAppDomainSetup`poskytuje metody pro konfiguraci aspektů aplikační domény před jejich vytvořením.|  
|[CreateEvidence – metoda](icorruntimehost-createevidence-method.md)|Načte ukazatel rozhraní typu <xref:System.Security.Principal.IIdentity> , který umožňuje hostiteli vytvořit legitimaci zabezpečení, která bude předána [CreateDomain –](icorruntimehost-createdomain-method.md) nebo [CreateDomainEx –](icorruntimehost-createdomainex-method.md).|  
|[CreateLogicalThreadState – metoda](icorruntimehost-createlogicalthreadstate-method.md)|Nepoužívat.|  
|[CurrentDomain – metoda](icorruntimehost-currentdomain-method.md)|Načte ukazatel rozhraní typu <xref:System._AppDomain> , který představuje doménu načtenou v aktuálním vlákně.|  
|[DeleteLogicalThreadState – metoda](icorruntimehost-deletelogicalthreadstate-method.md)|Nepoužívat.|  
|[EnumDomains – metoda](icorruntimehost-enumdomains-method.md)|Získá enumerátor pro domény v aktuálním procesu.|  
|[GetConfiguration – metoda](icorruntimehost-getconfiguration-method.md)|Získává objekt, který umožňuje hostiteli určit konfiguraci zpětného volání CLR.|  
|[GetDefaultDomain – metoda](icorruntimehost-getdefaultdomain-method.md)|Načte ukazatel rozhraní typu <xref:System._AppDomain> , který představuje výchozí doménu pro aktuální proces.|  
|[LocksHeldByLogicalThread – metoda](icorruntimehost-locksheldbylogicalthread-method.md)|Nepoužívat.|  
|[MapFile – metoda](icorruntimehost-mapfile-method.md)|Namapuje zadaný soubor na paměť. Tato metoda je zastaralá.|  
|[NextDomain – metoda](icorruntimehost-nextdomain-method.md)|Získá ukazatel rozhraní do další domény ve výčtu.|  
|[Start – metoda](icorruntimehost-start-method.md)|Spustí modul CLR.|  
|[Stop – metoda](icorruntimehost-stop-method.md)|Zastaví provádění kódu v modulu runtime pro aktuální proces.|  
|[SwitchInLogicalThreadState – metoda](icorruntimehost-switchinlogicalthreadstate-method.md)|Nepoužívat.|  
|[SwitchOutLogicalThreadState – metoda](icorruntimehost-switchoutlogicalthreadstate-method.md)|Nepoužívat.|  
|[UnloadDomain – metoda](icorruntimehost-unloaddomain-method.md)|Uvolní zadanou doménu aplikace z aktuálního procesu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** 1,0, 1,1  
  
## <a name="see-also"></a>Viz také:

- <xref:System.AppDomain>
- [Hosting](index.md)
- [ICLRRuntimeHost – rozhraní](iclrruntimehost-interface.md)
- [Hostitelé modulu runtime](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))
- [Rozhraní pro hostování](hosting-interfaces.md)
- [CorRuntimeHost – třída typu coclass](corruntimehost-coclass.md)
