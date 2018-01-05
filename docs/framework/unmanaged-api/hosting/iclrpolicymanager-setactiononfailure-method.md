---
title: "ICLRPolicyManager::SetActionOnFailure – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetActionOnFailure
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4440b36485ed900b5e64adcead2525dbb7d5206e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a>ICLRPolicyManager::SetActionOnFailure – metoda
Určuje akci zásady, které modul CLR (CLR) má provést, pokud dojde k selhání zadané.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `failure`  
 [v] Jeden z [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) hodnoty, která určuje typ selhání, pro které chcete provést akci.  
  
 `action`  
 [v] Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, který udává akci, která mají být provedeny, když dojde k chybě. Seznam podporovaných hodnot najdete v části poznámky.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`SetActionOnFailure`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Akce zásad nelze nastavit pro zadanou operaci, nebo pro operaci byla zadána neplatná zásada akce.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím modulu CLR vyvolá výjimku, když se nepodaří přidělení prostředků, třeba paměť. `SetActionOnFailure`umožňuje hostiteli, aby toto chování potlačit zadáním zásad akce provést při selhání. V následující tabulce jsou uvedeny kombinace [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) a [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, které jsou podporovány. (Je vynechaný předponu FAIL_ [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) hodnoty.)  
  
||NonCriticalResource|CriticalResource|FatalRuntime|OrphanedLock|StackOverflow|AccessViolation|CodeContract|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|X|X||||Není k dispozici||  
|eThrowException|X|X||||Není k dispozici||  
|`eAbortThread`|X|X||||Není k dispozici|X|  
|`eRudeAbortThread`|X|X||||Není k dispozici|X|  
|`eUnloadAppDomain`|X|X||X||Není k dispozici|X|  
|`eRudeUnloadAppDomain`|X|X||X|X|Není k dispozici|X|  
|`eExitProcess`|X|X||X|X|Není k dispozici|X|  
|eFastExitProcess|X|X||X|X|Není k dispozici||  
|`eRudeExitProcess`|X|X|X|X|X|Není k dispozici||  
|`eDisableRuntime`|X|X|X|X|X|Není k dispozici||  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [EClrFailure – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [EPolicyAction – výčet](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [ICLRPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
