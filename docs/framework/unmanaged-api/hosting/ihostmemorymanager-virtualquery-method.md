---
title: IHostMemoryManager::VirtualQuery – metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualQuery
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 028ca0b9cb917d3e6cc0242cbc8c3f4a5a19ab39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760100"
---
# <a name="ihostmemorymanagervirtualquery-method"></a>IHostMemoryManager::VirtualQuery – metoda
Slouží jako logické obálku pro odpovídající funkci Win32. Implementace Win32 `VirtualQuery` načte informace o rozsahu stránek v virtuálního adresového prostoru volajícího procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `lpAddress`  
 [in] Ukazatel na adresu ve virtuální paměti, aby se dalo dotazovat.  
  
 `lpBuffer`  
 [out] Ukazatel na strukturu, která obsahuje informace o zadané paměťové oblasti.  
  
 `dwLength`  
 [in] Velikost v bajtech, vyrovnávací paměti, která `lpBuffer` odkazuje na.  
  
 `pResult`  
 [out] Ukazatel na počet bajtů vrácených informace vyrovnávací paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`VirtualQuery` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `VirtualQuery` poskytuje informace o rozsahu stránek v virtuálního adresového prostoru volajícího procesu. Tato implementace nastaví hodnotu vlastnosti `pResult` parametr počet bajtů, vrátí ve vyrovnávací paměti informace a vrací hodnotu HRESULT. V rozhraní Win32 `VirtualQuery` funkce, vrácená hodnota je velikost vyrovnávací paměti. Další informace najdete v dokumentaci k platformě Windows.  
  
> [!IMPORTANT]
>  Operační systém provádění `VirtualQuery` nesnižuje zablokování a můžete spustit až do ukončení se náhodný vlákna pozastaveno v uživatelském kódu. Používejte opatrní při implementaci verze prostředí této metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
