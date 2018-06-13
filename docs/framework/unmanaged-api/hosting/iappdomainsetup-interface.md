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
ms.openlocfilehash: cbcbc446eabcfcbc28c830f8860bde726c8eb6e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434765"
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup – rozhraní
Poskytne vlastnosti, které jsou hostiteli umožní nakonfigurovat <xref:System.AppDomain?displayProperty=nameWithType> typ před voláním [icorruntimehost::createdomainex –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metoda k jeho vytvoření.  
  
## <a name="properties"></a>Vlastnosti  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|Získá nebo nastaví název adresáře, která obsahuje aplikaci.|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|Získá nebo nastaví název aplikace.|  
|<xref:System.AppDomainSetup.CachePath%2A>|Získá nebo nastaví název oblasti konkrétní aplikace vytvořena stínová kopie kde jsou soubory.|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|Získá nebo nastaví název konfiguračního souboru pro aplikaci.|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|Získá nebo nastaví název adresáře, kde jsou dynamicky generovaném soubory uložené a získat přístup.|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|Získá nebo nastaví cestu k souboru licence, která souvisí s touto doménou.|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|Získá nebo nastaví seznam adresářů v kombinaci s <xref:System.AppDomainSetup.ApplicationBase%2A> adresáře testu pro soukromá sestavení.|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|Získá nebo nastaví hodnotu řetězce, zahrnutí nebo vyloučení <xref:System.AppDomainSetup.ApplicationBase%2A> z cesty pro hledání pro aplikaci.|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|Získá nebo nastaví názvy adresářů, které obsahují sestavení, které může být vytvořena stínová kopie.|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|Získá nebo nastaví řetězec, který označuje, zda stínové kopírování sestavení je zapnuto nebo vypnuto. Platné hodnoty jsou "true" nebo "Nepravda".|  
  
## <a name="remarks"></a>Poznámky  
 `IAppDomainSetup` Rozhraní odpovídá spravovaný <xref:System.IAppDomainSetup> rozhraní, které <xref:System.AppDomainSetup> zadejte implementuje. V tématu <xref:System.IAppDomainSetup?displayProperty=nameWithType> podrobný popis jeho vlastnosti.  
  
 `IAppDomainSetup` představuje informace o vazbě sestavení, které mohou být přidány do <xref:System.AppDomain> instance před jeho vytvoření. Například můžete nastavit hostitele <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost k vytvoření kořenového adresáře, který modul CLR (CLR) sondy pro spravované sestavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup>  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
