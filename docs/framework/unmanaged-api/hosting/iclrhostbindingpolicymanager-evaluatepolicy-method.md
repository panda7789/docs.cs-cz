---
title: ICLRHostBindingPolicyManager::EvaluatePolicy – metoda
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.EvaluatePolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy method [.NET Framework hosting]
- EvaluatePolicy method [.NET Framework hosting]
ms.assetid: 3a3a9446-7a4e-4836-9b27-5c536c15993d
topic_type:
- apiref
ms.openlocfilehash: f72a66354bfc907dab7ebc24de515bdfb20ddfb2
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703594"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a>ICLRHostBindingPolicyManager::EvaluatePolicy – metoda
Vyhodnotí zásady vytváření vazeb jménem hostitele.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzReferenceIdentity`  
 pro Odkaz na sestavení před vyhodnocením zásad.  
  
 `pbApplicationPolicy`  
 pro Ukazatel na vyrovnávací paměť, která obsahuje data zásad.  
  
 `cbAppPolicySize`  
 pro Velikost `pbApplicationPolicy` vyrovnávací paměti.  
  
 `pwzPostPolicyReferenceIdentity`  
 mimo Odkaz na sestavení po vyhodnocení nových dat zásad  
  
 `pcchPostPolicyReferenceIdentity`  
 [in, out] Ukazatel na velikost vyrovnávací paměti odkazu identity sestavení po vyhodnocení nových dat zásad.  
  
 `pdwPoliciesApplied`  
 mimo Ukazatel na logickou nebo kombinaci hodnot [EBindPolicyLevels –](ebindpolicylevels-enumeration.md) , které označují, které zásady byly aplikovány.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Vyhodnocení bylo úspěšně dokončeno.|  
|E_INVALIDARG|Buď `pwzReferenceIdentity` nebo `pbApplicationPolicy` je odkaz s hodnotou null.|  
|ERROR_INSUFFICIENT_BUFFER|`cbAppPolicySize`je příliš malá.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `EvaluatePolicy`Metoda umožňuje hostiteli ovlivnit zásady vazeb pro zachování požadavků na správu verzí sestavení specifických pro hostitele. Samotný modul zásad zůstává v rámci CLR.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRHostBindingPolicyManager – rozhraní](iclrhostbindingpolicymanager-interface.md)
