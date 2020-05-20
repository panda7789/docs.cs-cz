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
ms.openlocfilehash: 5b537d59014afa783d3f8c5046cc02dad7ea7740
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615992"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a>ICLRAssemblyIdentityManager::GetBindingIdentityFromFile – metoda
Získá datovou vazbu identity sestavení pro sestavení v zadané cestě k souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzFilePath`  
 pro Cesta k souboru, který má být vyhodnocen.  
  
 `dwFlags`  
 pro Hodnota výčtu [ECLRAssemblyIdentityFlags –](eclrassemblyidentityflags-enumeration.md) , která označuje typ identity sestavení. K dispozici pro budoucí rozšíření. CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je jediná hodnota, kterou podporuje modul CLR (Common Language Runtime) verze 2,0.  
  
 `pwzBuffer`  
 mimo Vyrovnávací paměť obsahující data identity neprůhledných sestavení  
  
 `pcchBufferSize`  
 [in, out] Ukazatel na velikost `pwzBuffer` .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně vrácena.|  
|E_INVALIDARG|Zadaná hodnota `pwzFilePath` je null.|  
|ERROR_INSUFFICIENT_BUFFER|Velikost `pwzBuffer` je příliš malá.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `GetBindingIdentityFromFile`se obvykle nazývá dvakrát. První volání dodá hodnotu null pro `pwzBuffer` a metoda vrátí odpovídající velikost v `pcchBufferSize` . Druhé volání dodá vhodně přidělenou vyrovnávací paměť a metoda se vrátí se skutečnými daty vyrovnávací paměti po dokončení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRAssemblyIdentityManager – rozhraní](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList – rozhraní](iclrassemblyreferencelist-interface.md)
- [ICLRHostBindingPolicyManager – rozhraní](iclrhostbindingpolicymanager-interface.md)
