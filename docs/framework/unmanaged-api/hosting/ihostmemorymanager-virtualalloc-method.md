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
ms.openlocfilehash: de41b5e0aaf835ee2d4e4f32696fe104d5830b57
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804453"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a>IHostMemoryManager::VirtualAlloc – metoda
Slouží jako logická obálka odpovídající funkce Win32. Implementace v systému Win32 `VirtualAlloc` rezervuje nebo potvrdí oblast stránek ve virtuálním adresním prostoru volajícího procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 pro Ukazatel na počáteční adresu oblasti, která se má přidělit  
  
 `dwSize`  
 pro Velikost oblasti v bajtech  
  
 `flAllocationType`  
 pro Typ přidělení paměti.  
  
 `flProtect`  
 pro Ochrana paměti pro oblast stránek, která se má přidělit  
  
 `dwCriticalLevel`  
 pro Hodnota [EMemoryCriticalLevel –](ememorycriticallevel-enumeration.md) , která označuje dopad selhání přidělení.  
  
 `ppMem`  
 mimo Ukazatel na počáteční adresu přidělené paměti nebo hodnotu null, pokud požadavek nebylo možné splnit.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`VirtualAlloc`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|K dokončení žádosti o přidělení není k dispozici dostatek paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Oblast se vyhrazuje v adresním prostoru procesu voláním `VirtualAlloc` . `pAddress`Parametr obsahuje počáteční adresu bloku paměti, kterou chcete. Tento parametr je obvykle nastaven na hodnotu null. Operační systém uchovává záznam bezplatných rozsahů adres pro váš proces. `pAddress`Hodnota null dává systému pokyn, aby vyhradí oblast všude, kde se bude přizpůsobená. Alternativně můžete zadat konkrétní počáteční adresu pro blok paměti. V obou případech se výstupní parametr `ppMem` vrátí jako ukazatel na přidělenou paměť. Funkce sama vrací hodnotu HRESULT.  
  
 Funkce Win32 neobsahuje `VirtualAlloc` `ppMem` parametr a místo toho vrátí ukazatel na přidělenou paměť. Další informace najdete v dokumentaci k platformě Windows.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IHostMemoryManager – rozhraní](ihostmemorymanager-interface.md)
