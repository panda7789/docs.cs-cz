---
title: IHostMemoryManager::VirtualProtect – metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualProtect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualProtect
helpviewer_keywords:
- IHostMemoryManager::VirtualProtect method [.NET Framework hosting]
- VirtualProtect method [.NET Framework hosting]
ms.assetid: 13be0299-df0d-4951-aabf-0676a30b385f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b712b7e88e6cb5693c0823799e0980d90e34ff0a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492605"
---
# <a name="ihostmemorymanagervirtualprotect-method"></a>IHostMemoryManager::VirtualProtect – metoda
Slouží jako logické obálku pro odpovídající funkci Win32. Implementace Win32 `VirtualProtect` změní ochrany v oblasti potvrzené stránek v virtuálního adresového prostoru volajícího procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `lpAddress`  
 [in] Ukazatel na základní adresu virtuální paměti, jejichž atributy ochrany se změnit.  
  
 `dwSize`  
 [in] Velikost v bajtech, oblasti paměťových stránek změnit.  
  
 `flNewProtect`  
 [in] Typ ochrany paměti, aby mohli použít.  
  
 `pflOldProtect`  
 [out] Ukazatel na hodnotu předchozí ochrana paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`VirtualProtect` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Tato implementace `VirtualProtect` vrací hodnotu HRESULT, zatímco implementace Win32 vrací nenulovou hodnotu, čímž indikuje úspěšné provedení a hodnotu 0 označující selhání. Další informace najdete v dokumentaci k platformě Windows.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
