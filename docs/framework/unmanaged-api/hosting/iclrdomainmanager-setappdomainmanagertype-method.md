---
title: ICLRDomainManager::SetAppDomainManagerType – metoda
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47545d590682236d7a19813b15a144731b64c9e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555079"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType – metoda
Určuje typ odvozený od <xref:System.AppDomainManager?displayProperty=nameWithType> třídu správce domény aplikace, který se použije k inicializaci výchozí domény aplikace.  
  
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
 [in] Zobrazovaný název sestavení obsahující typ správce domény aplikace; Příklad: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".  
  
 `wszAppDomainManagerType`  
 [in] Název typu pro správce domény aplikace, včetně oboru názvů.  
  
 `dwInitializeDomainFlags`  
 [in] Kombinace [einitializenewdomainflags –](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) hodnot výčtu, která poskytují informace o Správci domény aplikace.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
  
## <a name="remarks"></a>Poznámky  
 V současné době pouze hodnota definovaná pro `dwInitializeDomainFlags` je `eInitializeNewDomainFlags_NoSecurityChanges`, který říká common language runtime (CLR), správce domény aplikace nebude během provádění měnit nastavení zabezpečení <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody. To umožňuje modulu CLR pro optimalizaci načítání sestavení, která mají podmíněnou <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut (APTCA). Pokud je velká přechodné uzavření tuto sadu sestavení, to může vést výrazné zlepšení času spuštění.  
  
> [!IMPORTANT]
>  Pokud hostitele Určuje `eInitializeNewDomainFlags_NoSecurityChanges` pro správce domény aplikace <xref:System.InvalidOperationException> je vyvolána, pokud žádné pokusu o změny zabezpečení domény aplikace.  
  
 Volání [iclrcontrol::setappdomainmanagertype –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)metoda je ekvivalentní volání `ICLRDomainManager::SetAppDomainManagerType` s `eInitializeNewDomainFlags_None`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRDomainManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [EInitializeNewDomainFlags – výčet](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
