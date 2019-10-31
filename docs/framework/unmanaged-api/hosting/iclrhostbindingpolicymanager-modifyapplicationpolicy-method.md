---
title: ICLRHostBindingPolicyManager::ModifyApplicationPolicy – metoda
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
ms.openlocfilehash: d5323538447e083a0c727e43261dd68337182b9b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141075"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>ICLRHostBindingPolicyManager::ModifyApplicationPolicy – metoda
Upraví zásadu vazby pro zadané sestavení a vytvoří novou verzi zásad.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,   
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,   
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzSourceAssemblyIdentity`  
 pro Identita sestavení, které má být upraveno.  
  
 `pwzTargetAssemblyIdentity`  
 pro Nová identita upraveného sestavení.  
  
 `pbApplicationPolicy`  
 pro Ukazatel na vyrovnávací paměť, která obsahuje data zásad vazby pro sestavení, které chcete upravit.  
  
 `cbAppPolicySize`  
 pro Velikost zásady vazby, která má být nahrazena.  
  
 `dwPolicyModifyFlags`  
 pro Logická nebo kombinovaná hodnota [EHostBindingPolicyModifyFlags –](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) , která označuje řízení přesměrování.  
  
 `pbNewApplicationPolicy`  
 mimo Ukazatel na vyrovnávací paměť, která obsahuje nová data zásad vazby.  
  
 `pcbNewAppPolicySize`  
 [in, out] Ukazatel na velikost nové vyrovnávací paměti zásad vazby.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Zásady se úspěšně změnily.|  
|E_INVALIDARG|`pwzSourceAssemblyIdentity` nebo `pwzTargetAssemblyIdentity` byl odkaz s hodnotou null.|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy` je příliš malý.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Metodu `ModifyApplicationPolicy` lze volat dvakrát. První volání by mělo pro parametr `pbNewApplicationPolicy` dodat hodnotu null. Toto volání se vrátí s potřebnou hodnotou pro `pcbNewAppPolicySize`. Druhé volání by mělo uvést tuto hodnotu pro `pcbNewAppPolicySize`a odkazovat na vyrovnávací paměť této velikosti pro `pbNewApplicationPolicy`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRHostBindingPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
