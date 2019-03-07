---
title: ICLRRuntimeHost::ExecuteInAppDomain – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4d59b3857b9c23ccb61e22319ffd2b3129bd26a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474845"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a>ICLRRuntimeHost::ExecuteInAppDomain – metoda
Určuje, <xref:System.AppDomain> v, který se má spustit zadaný spravovaný kód.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `AppDomainId`  
 [in] Číselné ID <xref:System.AppDomain> ve kterém chcete provést zadanou metodu.  
  
 `pCallback`  
 [in] Ukazatele na funkce pro spuštění v rámci zadaného <xref:System.AppDomain>.  
  
 `cookie`  
 [in] Ukazatel na neprůhledné paměť přidělenou volajícímu. Tento parametr je předáván modulem common language runtime (CLR) pro zpětné volání domény. Není runtime spravované haldy paměti. přidělování a životnosti tato paměť se řídí volající.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`ExecuteInAppDomain` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `ExecuteInAppDomain` umožňuje hostiteli pro kontrolu využití selhání, který spravuje <xref:System.AppDomain> zadané spravované metody by měly být provedeny v. Hodnota identifikátoru doménu aplikace, která odpovídá hodnotě lze získat <xref:System.AppDomain.Id%2A> vlastnost voláním [getcurrentappdomainid – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICLRRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
