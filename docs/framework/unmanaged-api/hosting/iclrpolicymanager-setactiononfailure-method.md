---
title: ICLRPolicyManager::SetActionOnFailure – metoda
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34d9e1a3747ecf3dffc925d7883599b773dd51f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638967"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a>ICLRPolicyManager::SetActionOnFailure – metoda
Určuje akci zásad by měl trvat common language runtime (CLR), když dojde k selhání zadané.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `failure`  
 [in] Jeden z [eclrfailure –](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) hodnoty určující typ selhání, pro které chcete provést akci.  
  
 `action`  
 [in] Jeden z [epolicyaction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty indikující akce, která má být provedeny, když dojde k chybě. Seznam podporovaných hodnot naleznete v části poznámky.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`SetActionOnFailure` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Akce zásad nelze nastavit pro zadanou operaci, nebo byla zadána neplatná zásada akci pro tuto operaci.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení CLR vyvolá výjimku, pokud se nezdaří pro přidělení prostředků, jako je paměť. `SetActionOnFailure` umožňuje hostiteli toto chování lze přepsat zadáním zásad akce má být provedena po selhání. V následující tabulce jsou uvedeny kombinace [eclrfailure –](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) a [epolicyaction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, které jsou podporovány. (Předpona FAIL_ je vynecháno z [eclrfailure –](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) hodnoty.)  
  
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
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [EClrFailure – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EPolicyAction – výčet](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
