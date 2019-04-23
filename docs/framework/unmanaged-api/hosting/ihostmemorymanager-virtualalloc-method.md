---
title: IHostMemoryManager::VirtualAlloc – metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5407a9d23833d73b2d6ef0038454f56f01d56867
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087648"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a>IHostMemoryManager::VirtualAlloc – metoda
Slouží jako logické obálku pro odpovídající funkci Win32. Implementace Win32 `VirtualAlloc` rezervuje nebo potvrdí změny v oblasti stránek v virtuálního adresového prostoru volajícího procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAddress`  
 [in] Ukazatel na počáteční adresu oblasti, kterou chcete přidělit.  
  
 `dwSize`  
 [in] Velikost v bajtech, oblasti.  
  
 `flAllocationType`  
 [in] Typ přidělení paměti.  
  
 `flProtect`  
 [in] Ochrana paměti pro oblasti stránek, které mají být přiděleny.  
  
 `dwCriticalLevel`  
 [in] [Ememorycriticallevel –](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) hodnotu, která určuje dopad selhání přidělení.  
  
 `ppMem`  
 [out] Ukazatel na počáteční adresu přidělené paměti nebo hodnota null, pokud požadavek se nepodařilo vyřídit.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`VirtualAlloc` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Nedostatek paměti nebyl k dispozici k dokončení žádosti o přidělení|  
  
## <a name="remarks"></a>Poznámky  
 Rezervovat oblast v adresním prostoru procesu voláním `VirtualAlloc`. `pAddress` Parametr obsahuje počáteční adresu bloku paměti, který chcete. Tento parametr je obvykle nastavena na hodnotu null. Operační systém se zaznamenávají rozsahy adres zdarma, které jsou k dispozici pro váš proces. A `pAddress` hodnotu null nastaví systém pro rezervaci oblast, bez ohledu na to považuje za vhodné. Alternativně můžete zadat konkrétní počáteční adresu bloku paměti. V obou případech se výstupní parametr `ppMem` se vrátí jako ukazatel do přidělené paměti. Samotné funkce vrací hodnotu HRESULT.  
  
 Win32 `VirtualAlloc` funkce nemá `ppMem` parametr a místo toho vrátí ukazatel do přidělené paměti. Další informace najdete v dokumentaci k platformě Windows.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
