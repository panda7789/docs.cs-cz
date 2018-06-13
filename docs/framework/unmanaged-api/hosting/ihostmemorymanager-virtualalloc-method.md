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
ms.openlocfilehash: fe54aed47d240be37ab9dbc5381235c4e962f1f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440311"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a>IHostMemoryManager::VirtualAlloc – metoda
Slouží jako logické obálku pro odpovídající funkci Win32. Implementace Win32 `VirtualAlloc` si vyhrazuje nebo potvrdí oblast stránek ve virtuálním adresním prostoru procesu volání.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `pAddress`  
 [v] Ukazatel na počáteční adresa oblasti přidělit.  
  
 `dwSize`  
 [v] Velikost v bajtech, oblasti.  
  
 `flAllocationType`  
 [v] Typ přidělení paměti.  
  
 `flProtect`  
 [v] Ochrana paměti pro oblast stránek má být přidělen.  
  
 `dwCriticalLevel`  
 [v] [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) hodnotu, která určuje dopad došlo k chybě přidělení.  
  
 `ppMem`  
 [out] Ukazatel na počáteční adresa přidělené paměti, nebo hodnota null, pokud požadavek nelze uspokojit.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`VirtualAlloc` úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Není dostatek paměti k dispozici bylo možné dokončit požadavek na přidělení|  
  
## <a name="remarks"></a>Poznámky  
 Rezervovat oblast v adresním prostoru procesu voláním `VirtualAlloc`. `pAddress` Parametr obsahuje počáteční adresa paměti bloku chcete. Tento parametr je obvykle nastaven na hodnotu null. Operační systém obsahuje záznamy o volnou adresu rozsahy, které jsou k dispozici pro váš proces. A `pAddress` systému tak, aby vyhradil oblast, bez ohledu na považuje za vhodné dá pokyn, hodnotu null. Alternativně můžete zadat konkrétní počáteční adresa bloku paměti. V obou případech výstupního parametru `ppMem` se vrátí jako ukazatel přidělenou paměť. Samotná funkce vrátí hodnotu HRESULT.  
  
 Win32 `VirtualAlloc` funkce nemá `ppMem` parametr a vrátí ukazatele do paměti přidělené místo. Další informace najdete v dokumentaci k platformě Windows.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
