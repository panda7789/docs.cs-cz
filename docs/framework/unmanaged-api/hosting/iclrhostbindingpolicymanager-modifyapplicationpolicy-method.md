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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a9e438e6dd436303cd6f7aa60c779179b5d3c04
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779674"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>ICLRHostBindingPolicyManager::ModifyApplicationPolicy – metoda
Změní zásady vazeb pro zadané sestavení a vytvoří se nová verze zásad.  
  
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
 [in] Identita sestavení změnit.  
  
 `pwzTargetAssemblyIdentity`  
 [in] Nové identity upravené sestavení.  
  
 `pbApplicationPolicy`  
 [in] Ukazatel do vyrovnávací paměti, která obsahuje data zásad vazby pro sestavení, které chcete upravit.  
  
 `cbAppPolicySize`  
 [in] Velikost zásady vazeb, které mají být nahrazeny.  
  
 `dwPolicyModifyFlags`  
 [in] Logický OR kombinaci [ehostbindingpolicymodifyflags –](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) hodnoty určující kontrolu nad přesměrování.  
  
 `pbNewApplicationPolicy`  
 [out] Ukazatel do vyrovnávací paměti, který obsahuje data nové zásady vazby.  
  
 `pcbNewAppPolicySize`  
 [out v] Ukazatel na velikost vyrovnávací paměť nového zásady vazby.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Tyto zásady se úspěšně změnily.|  
|E_INVALIDARG|`pwzSourceAssemblyIdentity` nebo `pwzTargetAssemblyIdentity` byl odkaz s hodnotou null.|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy` je příliš malá.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `ModifyApplicationPolicy` Metodu lze volat dvakrát. První volání by mělo nabízet pro hodnotu null `pbNewApplicationPolicy` parametru. Toto volání vrátí hodnotou nezbytné pro `pcbNewAppPolicySize`. Druhé volání by mělo nabízet tuto hodnotu pro `pcbNewAppPolicySize`a přejděte do vyrovnávací paměti, že velikosti pro `pbNewApplicationPolicy`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRHostBindingPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
