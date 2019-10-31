---
title: IAppDomainSetup – rozhraní
ms.date: 03/30/2017
api_name:
- IAppDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainSetup
helpviewer_keywords:
- IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type:
- apiref
ms.openlocfilehash: 0fab64c31d4a73995c16d21767f4569f21c7df9a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126875"
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup – rozhraní
Poskytne vlastnosti, které umožní hostiteli nakonfigurovat <xref:System.AppDomain?displayProperty=nameWithType> typ před voláním metody [ICorRuntimeHost:: CreateDomainEx –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) , aby ji bylo možné vytvořit.  
  
## <a name="properties"></a>Vlastnosti  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|Získá nebo nastaví název adresáře, který obsahuje aplikaci.|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|Získá nebo nastaví název aplikace.|  
|<xref:System.AppDomainSetup.CachePath%2A>|Získá nebo nastaví název oblasti specifické pro aplikaci, ve které jsou soubory kopírovány stínové kopie.|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|Získá nebo nastaví název konfiguračního souboru pro aplikaci.|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|Získá nebo nastaví název adresáře, kde jsou uloženy a otevřeny dynamicky generované soubory.|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|Získá nebo nastaví cestu k souboru s licencí, který je přidružený k této doméně.|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|Získá nebo nastaví seznam adresářů v kombinaci s <xref:System.AppDomainSetup.ApplicationBase%2A> adresářem pro testování privátních sestavení.|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|Získává nebo nastavuje řetězcovou hodnotu, která zahrnuje nebo vylučuje <xref:System.AppDomainSetup.ApplicationBase%2A> z vyhledávací cesty pro aplikaci.|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|Získá nebo nastaví názvy adresářů, které obsahují sestavení pro vytváření stínových kopií.|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|Získá nebo nastaví řetězec, který označuje, zda je stínové kopírování zapnuto nebo vypnuto. Platné hodnoty jsou "true" nebo "false".|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `IAppDomainSetup` odpovídá spravovanému rozhraní <xref:System.IAppDomainSetup>, které implementuje typ <xref:System.AppDomainSetup>. Podrobné popisy jeho vlastností najdete v tématu <xref:System.IAppDomainSetup?displayProperty=nameWithType>.  
  
 `IAppDomainSetup` představuje informace o vazbě sestavení, které lze přidat do instance <xref:System.AppDomain> před jejím vytvořením. Například hostitel může nastavit vlastnost <xref:System.AppDomainSetup.ApplicationBase%2A>, aby navázala kořenový adresář, který modul CLR (Common Language Runtime) pro spravovaná sestavení vyhledá.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
