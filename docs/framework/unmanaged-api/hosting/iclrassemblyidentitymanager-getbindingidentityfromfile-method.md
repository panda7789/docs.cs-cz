---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromFile – metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28e97289eda5949e6d124426eb58105e2e3ad33e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435039"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a>ICLRAssemblyIdentityManager::GetBindingIdentityFromFile – metoda
Získá identitu sestavení vazba dat pro sestavení v zadaná cesta k souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwzFilePath`  
 [v] Cesta k souboru, který se vyhodnotí.  
  
 `dwFlags`  
 [v] Hodnota [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) výčtu, která určuje typ identity sestavení. K dispozici pro budoucí rozšíření. CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je jediná hodnota, která podporuje modul CLR (CLR) verze 2.0.  
  
 `pwzBuffer`  
 [out] Vyrovnávací paměť obsahující data identit neprůhledného sestavení.  
  
 `pcchBufferSize`  
 [ve out] Ukazatel na velikost `pwzBuffer`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda úspěšně vrácena.|  
|E_INVALIDARG|Zadaných `pwzFilePath` má hodnotu null.|  
|ERROR_INSUFFICIENT_BUFFER|Velikost `pwzBuffer` je příliš malá.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `GetBindingIdentityFromFile` obvykle nazývá dvakrát. První volání poskytuje hodnotu null pro `pwzBuffer`, a vrátí metoda odpovídající velikost v `pcchBufferSize`. Druhé volání poskytuje správně přidělené vyrovnávací paměti, a vrátí metodu s skutečné vyrovnávací paměť dat po dokončení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRAssemblyIdentityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [ICLRAssemblyReferenceList – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [ICLRHostBindingPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
