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
ms.openlocfilehash: d8df78e3d5cebe5378dfba11dc0ea93cc8e346eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178105"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>ICLRHostBindingPolicyManager::ModifyApplicationPolicy – metoda
Upraví zásady vazby pro zadané sestavení a vytvoří novou verzi zásady.  
  
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
 [v] Identita sestavení upravit.  
  
 `pwzTargetAssemblyIdentity`  
 [v] Nová identita upravenésestavení.  
  
 `pbApplicationPolicy`  
 [v] Ukazatel na vyrovnávací paměť, která obsahuje data zásad vazby pro sestavení upravit.  
  
 `cbAppPolicySize`  
 [v] Velikost zásady vazby, které mají být nahrazeny.  
  
 `dwPolicyModifyFlags`  
 [v] Logická kombinace nebo hodnot [EHostBindingPolicyModifyFlags,](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) označující řízení přesměrování.  
  
 `pbNewApplicationPolicy`  
 [out] Ukazatel na vyrovnávací paměť, která obsahuje nová data zásad vazby.  
  
 `pcbNewAppPolicySize`  
 [dovnitř, ven] Ukazatel na velikost vyrovnávací paměti zásad y nové vazby.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Zásada byla úspěšně změněna.|  
|E_invalidarg|`pwzSourceAssemblyIdentity`nebo `pwzTargetAssemblyIdentity` byl nulový odkaz.|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy`je příliš malý.|  
|HOST_E_CLRNOTAVAILABLE|Běžný jazyk runtime (CLR) nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Časový čas hovoru byl vypován.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.|  
|E_fail|Došlo k neznámému katastrofickému selhání. Po metoda vrátí E_FAIL CLR již není použitelný v rámci procesu. Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Metoda `ModifyApplicationPolicy` může být volána dvakrát. První volání by mělo poskytnout `pbNewApplicationPolicy` hodnotu null pro parametr. Toto volání se vrátí `pcbNewAppPolicySize`s potřebnou hodnotou pro . Druhé volání by mělo `pcbNewAppPolicySize`zadat tuto hodnotu pro a `pbNewApplicationPolicy`přejděte na vyrovnávací paměť této velikosti pro .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRHostBindingPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
