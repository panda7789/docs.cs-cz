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
ms.openlocfilehash: 16d146766786f129d6da38bde1126ce8afe5e70f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963693"
---
# <a name="ihostmemorymanagervirtualquery-method"></a>IHostMemoryManager::VirtualQuery – metoda
Slouží jako logická obálka odpovídající funkce Win32. Implementace `VirtualQuery` Win32 načte informace o rozsahu stránek ve virtuálním adresním prostoru volajícího procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `lpAddress`  
 pro Ukazatel na adresu ve virtuální paměti, která se má dotazovat.  
  
 `lpBuffer`  
 mimo Ukazatel na strukturu, která obsahuje informace o zadané oblasti paměti.  
  
 `dwLength`  
 pro Velikost vyrovnávací paměti (v bajtech), na `lpBuffer` kterou odkazuje.  
  
 `pResult`  
 mimo Ukazatel na počet bajtů vrácených vyrovnávací pamětí informací.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`VirtualQuery`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `VirtualQuery`poskytuje informace o rozsahu stránek ve virtuálním adresním prostoru volajícího procesu. Tato implementace nastaví hodnotu `pResult` parametru na počet bajtů vrácených v zásobníku informací a vrátí hodnotu HRESULT. Ve funkci Win32 `VirtualQuery` je návratovou hodnotou velikost vyrovnávací paměti. Další informace najdete v dokumentaci k platformě Windows.  
  
> [!IMPORTANT]
> Implementace `VirtualQuery` operačního systému nenese zablokování a může běžet k dokončení náhodných vláken pozastavených v uživatelském kódu. Při implementaci hostované verze této metody používejte skvělou opatrnost.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** MSCorEE. h  
  
 **Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
