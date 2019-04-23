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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbde873481aea9de94862117a99079301965f33c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220068"
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup – rozhraní
Poskytne vlastnosti, které povolí hostitelské ke konfiguraci <xref:System.AppDomain?displayProperty=nameWithType> typ před voláním [icorruntimehost::createdomainex –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metoda k jeho vytvoření.  
  
## <a name="properties"></a>Vlastnosti  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|Získá nebo nastaví název adresáře, který obsahuje aplikaci.|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|Získá nebo nastaví název aplikace.|  
|<xref:System.AppDomainSetup.CachePath%2A>|Získá nebo nastaví název oblasti konkrétní aplikaci kde soubory jsou vytvořena stínová kopie.|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|Získá nebo nastaví název konfiguračního souboru pro aplikaci.|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|Získá nebo nastaví název adresáře, kde se ukládají a získávají dynamicky generované soubory.|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|Získá nebo nastaví cestu k souboru licencí, který je přidružený k této doméně.|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|Získá nebo nastaví seznam adresářů, v kombinaci s <xref:System.AppDomainSetup.ApplicationBase%2A> adresář pro sběr dat pro soukromá sestavení.|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|Získá nebo nastaví řetězcovou hodnotu, která zahrnutí nebo vyloučení <xref:System.AppDomainSetup.ApplicationBase%2A> z cesty pro hledání pro aplikaci.|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|Získá nebo nastaví názvy adresářů, které obsahují sestavení bude vytvořena stínová kopie.|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|Získá nebo nastaví řetězec, který označuje, zda stínové kopírování sestavení je zapnout nebo vypnout. Platné hodnoty jsou "true" nebo "false".|  
  
## <a name="remarks"></a>Poznámky  
 `IAppDomainSetup` Rozhraní odpovídá spravovanou <xref:System.IAppDomainSetup> rozhraní, které <xref:System.AppDomainSetup> typ implementuje. Zobrazit <xref:System.IAppDomainSetup?displayProperty=nameWithType> podrobný popis jeho vlastnosti.  
  
 `IAppDomainSetup` představuje informace o vazbu sestavení lze přidat do <xref:System.AppDomain> instance před její vytvoření. Například můžete nastavit hostitele <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost vytvořit kořenový adresář, který modul CLR (CLR) sondy pro spravovaná sestavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
