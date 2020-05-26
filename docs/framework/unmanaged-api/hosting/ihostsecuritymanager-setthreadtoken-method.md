---
title: IHostSecurityManager::SetThreadToken – metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetThreadToken
helpviewer_keywords:
- SetThreadToken method [.NET Framework hosting]
- IHostSecurityManager::SetThreadToken method [.NET Framework hosting]
ms.assetid: e951c345-8a86-4587-911b-a1a57bc6428a
topic_type:
- apiref
ms.openlocfilehash: 7891ddc5085eedd2a9010023f119d08f101e2fa3
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803778"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a>IHostSecurityManager::SetThreadToken – metoda
Nastaví popisovač pro aktuálně prováděné vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hToken`  
 pro Popisovač tokenu, který se má nastavit pro aktuálně spuštěné vlákno.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`SetThreadToken`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostSecurityManager::SetThreadToken`se chová podobně jako odpovídající funkce Win32 se stejným názvem, s tím rozdílem, že funkce Win32 umožňuje volajícímu předat popisovač do libovolného vlákna, zatímco `IHostSecurityManager::SetThreadToken` může přidružit token pouze k aktuálně zpracovávanému vláknu.  
  
 `HANDLE`Typ není kompatibilní s modelem COM; to znamená, že jeho velikost je specifická pro operační systém a vyžaduje vlastní zařazování. Proto je tento token určen pouze pro použití v rámci procesu, mezi CLR a hostitelem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IHostSecurityManager – rozhraní](ihostsecuritymanager-interface.md)
- [IHostThreadPoolManager – rozhraní](ihostthreadpoolmanager-interface.md)
