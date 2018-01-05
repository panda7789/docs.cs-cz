---
title: "ICLRDomainManager::SetAppDomainManagerType – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager.SetAppDomainManagerType
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37c94da8295a0ebb96d45e3a8f122d96bc2126c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType – metoda
Určuje typ odvozený z <xref:System.AppDomainManager?displayProperty=nameWithType> třídu aplikace správce domény, který se použije k chybě při inicializaci výchozí doméně aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszAppDomainManagerAssembly`  
 [v] Zobrazovaný název sestavení, které obsahuje typ správce domény aplikace; například: "AdMgrExample, verze = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".  
  
 `wszAppDomainManagerType`  
 [v] Název typu správce domény aplikace, včetně oboru názvů.  
  
 `dwInitializeDomainFlags`  
 [v] Kombinace [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) hodnot výčtu, které poskytují informace o Správci domény aplikace.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
  
## <a name="remarks"></a>Poznámky  
 V současné době jediným definovaná hodnota `dwInitializeDomainFlags` je `eInitializeNewDomainFlags_NoSecurityChanges`, které informuje common language runtime (CLR), aby správce domény aplikace nezmění nastavení zabezpečení během provádění <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metoda. To umožňuje CLR za účelem optimalizace načítání sestavení, které mají podmíněného <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut (APTCA). To může způsobit přináší značné vylepšení v čase spuštění Pokud přechodné uzavření této sady sestavení velká.  
  
> [!IMPORTANT]
>  Pokud hostitel Určuje `eInitializeNewDomainFlags_NoSecurityChanges` pro správce domény aplikace <xref:System.InvalidOperationException> je vyvolána, pokud je všechny pokusu upravit zabezpečení domény aplikace.  
  
 Volání [iclrcontrol::setappdomainmanagertype –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)metoda je ekvivalentní volání `ICLRDomainManager::SetAppDomainManagerType` s `eInitializeNewDomainFlags_None`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [ICLRDomainManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 [EInitializeNewDomainFlags – výčet](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
