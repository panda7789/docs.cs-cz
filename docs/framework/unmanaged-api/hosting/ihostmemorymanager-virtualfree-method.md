---
title: IHostMemoryManager::VirtualFree – metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualFree
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17673fb3684747f42556caef4ea54db050eef56e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696177"
---
# <a name="ihostmemorymanagervirtualfree-method"></a>IHostMemoryManager::VirtualFree – metoda
Slouží jako logické obálku pro odpovídající funkci Win32. Implementace Win32 `VirtualFree` uvolní, rozváže, uvolní nebo rozváže oblast stránky v rámci virtuálního adresového prostoru volajícího procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `lpAddress`  
 [in] Ukazatel na základní adresa stránky virtuální paměti k uvolnění.  
  
 `dwSize`  
 [in] Velikost v bajtech, oblasti, kterou chcete být uvolněna.  
  
 `dwFreeType`  
 [in] Typ operace uvolnění.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`VirtualFree` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_INVALIDOPERATION|Byl proveden pokus o uvolnění paměti, který nebyl přidělen prostřednictvím hostitele.|  
  
## <a name="remarks"></a>Poznámky  
 `VirtualFree` uvolní stránky virtuální paměti, které jsou spojené s `lpAddress` parametr prostřednictvím dřívějším volání [ihostmemorymanager::VirtualAlloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) funkce. Pokusy o uvolnění paměti, který nebyl přidělen prostřednictvím hostitele by měl vrátit HOST_E_INVALIDOPERATION.  
  
 Sémantika je stejné jako ty Win32 provádění `VirtualFree`. Další informace najdete v dokumentaci k platformě Windows.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [IHostMalloc – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
