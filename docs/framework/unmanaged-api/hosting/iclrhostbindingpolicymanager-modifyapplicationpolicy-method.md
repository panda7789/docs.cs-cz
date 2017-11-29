---
title: "ICLRHostBindingPolicyManager::ModifyApplicationPolicy – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 51775f52e34f35d8ef9f3a8533363be73e9bd7c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>ICLRHostBindingPolicyManager::ModifyApplicationPolicy – metoda
Změní zásadu vazby pro zadaného sestavení a vytvoří se nová verze zásad.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `pwzSourceAssemblyIdentity`  
 [v] Identita sestavení, které chcete upravit.  
  
 `pwzTargetAssemblyIdentity`  
 [v] Novou identitu upravené sestavení.  
  
 `pbApplicationPolicy`  
 [v] Ukazatel na vyrovnávací paměť, která obsahuje data zásad vazby pro sestavení, které chcete upravit.  
  
 `cbAppPolicySize`  
 [v] Velikost vazby zásady, které mají být nahrazeny.  
  
 `dwPolicyModifyFlags`  
 [v] Logická nebo kombinace [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) hodnoty, indikujících řízení přesměrování.  
  
 `pbNewApplicationPolicy`  
 [out] Ukazatel na vyrovnávací paměť, která obsahuje nové zásady data vazby.  
  
 `pcbNewAppPolicySize`  
 [ve out] Ukazatel na velikost vyrovnávací paměť nového zásad vazby.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Zásady byl úspěšně upraven.|  
|E_INVALIDARG|`pwzSourceAssemblyIdentity`nebo `pwzTargetAssemblyIdentity` byl odkaz s hodnotou null.|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy`je příliš malá.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `ModifyApplicationPolicy` Nelze volat metodu dvakrát. Prvním volání musí zadat hodnotu null pro `pbNewApplicationPolicy` parametr. Toto volání se vrátí hodnotou potřebné pro `pcbNewAppPolicySize`. Druhé volání musí zadat tuto hodnotu pro `pcbNewAppPolicySize`a přejděte do vyrovnávací paměti této velikosti pro `pbNewApplicationPolicy`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Iclrhostbindingpolicymanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
