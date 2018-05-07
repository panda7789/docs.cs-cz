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
ms.openlocfilehash: 68a9d6ad7470ffaf1143a4a8e3134f20edb9e3c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ihostmemorymanagervirtualquery-method"></a>IHostMemoryManager::VirtualQuery – metoda
Slouží jako logické obálku pro odpovídající funkci Win32. Implementace Win32 `VirtualQuery` načte informace o rozsahu stránek ve virtuálním adresním prostoru procesu volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `lpAddress`  
 [v] Ukazatel na adresu ve virtuální paměti, které má být dotazován.  
  
 `lpBuffer`  
 [out] Ukazatel na strukturu, která obsahuje informace o určenou oblast paměti.  
  
 `dwLength`  
 [v] Velikost v bajtech vyrovnávací paměti, `lpBuffer` odkazuje na.  
  
 `pResult`  
 [out] Ukazatel na počet bajtů vrácený informace vyrovnávací paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`VirtualQuery` úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `VirtualQuery` poskytuje informace o rozsahu stránek ve virtuálním adresním prostoru procesu volání. Tato implementace nastaví hodnotu `pResult` parametru počet bajtů ve vyrovnávací paměti informace vrátí a vrací hodnotu HRESULT. V Win32 `VirtualQuery` velikost vyrovnávací paměti je funkce, návratovou hodnotu. Další informace najdete v dokumentaci k platformě Windows.  
  
> [!IMPORTANT]
>  Operační systém implementace `VirtualQuery` nedojde zablokování a na dokončení můžete spustit s náhodných vláken pozastavenou uživatelského kódu. Použijte opatrní při implementaci hostované verze této metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
