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
ms.openlocfilehash: 4d37b7d803509ebfa861b7502d419f868bd12e11
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804390"
---
# <a name="ihostmemorymanagervirtualfree-method"></a>IHostMemoryManager::VirtualFree – metoda
Slouží jako logická obálka odpovídající funkce Win32. Implementace Win32 `VirtualFree` vydaných verzí, zrušení potvrzení nebo uvolnění a zrušení potvrzení oblasti stránek v rámci virtuálního adresového prostoru volajícího procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `lpAddress`  
 pro Ukazatel na základní adresu stránky virtuální paměti, která se uvolní.  
  
 `dwSize`  
 pro Velikost oblasti, která se má uvolnit (v bajtech)  
  
 `dwFreeType`  
 pro Typ uvolnění operace.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`VirtualFree`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_INVALIDOPERATION|Byl proveden pokus o uvolnění paměti, která nebyla přidělena prostřednictvím hostitele.|  
  
## <a name="remarks"></a>Poznámky  
 `VirtualFree`uvolní stránky virtuální paměti přidružené k `lpAddress` parametru prostřednictvím dřívějšího volání funkce [IHostMemoryManager:: VirtualAlloc](ihostmemorymanager-virtualalloc-method.md) . Pokusy o volnou paměť, která nebyla přidělena prostřednictvím hostitele, by měly vracet HOST_E_INVALIDOPERATION.  
  
 Sémantika je stejná jako u implementace v systému Win32 `VirtualFree` . Další informace najdete v dokumentaci k platformě Windows.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IHostMemoryManager – rozhraní](ihostmemorymanager-interface.md)
- [IHostMalloc – rozhraní](ihostmalloc-interface.md)
