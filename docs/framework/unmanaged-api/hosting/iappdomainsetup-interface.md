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
ms.openlocfilehash: 1726f8929404e0dde979972d7830a6951dd71891
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617058"
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup – rozhraní
Poskytne vlastnosti, které umožňují hostiteli nakonfigurovat <xref:System.AppDomain?displayProperty=nameWithType> typ před voláním metody [ICorRuntimeHost:: CreateDomainEx –](icorruntimehost-createdomainex-method.md) , aby ji bylo možné vytvořit.  
  
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
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|Získává nebo nastavuje řetězcovou hodnotu, která zahrnuje nebo vylučuje <xref:System.AppDomainSetup.ApplicationBase%2A> cestu pro hledání aplikace.|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|Získá nebo nastaví názvy adresářů, které obsahují sestavení pro vytváření stínových kopií.|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|Získá nebo nastaví řetězec, který označuje, zda je stínové kopírování zapnuto nebo vypnuto. Platné hodnoty jsou "true" nebo "false".|  
  
## <a name="remarks"></a>Poznámky  
 `IAppDomainSetup`Rozhraní odpovídá spravovanému <xref:System.IAppDomainSetup> rozhraní, které <xref:System.AppDomainSetup> typ implementuje. <xref:System.IAppDomainSetup?displayProperty=nameWithType>Podrobné popisy jeho vlastností najdete v tématu.  
  
 `IAppDomainSetup`představuje informace o vazbě sestavení, které mohou být přidány do <xref:System.AppDomain> instance před jeho vytvořením. Například hostitel může nastavit <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost tak, aby navázala kořenový adresář, který modul CLR (Common Language Runtime) pro spravovaná sestavení vyhledá.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [Rozhraní pro hostování](hosting-interfaces.md)
