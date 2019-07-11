---
title: ICorDebugProcess::WriteMemory – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4599bf310a0b819bc662b90a5a86e87ac27c37b1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737017"
---
# <a name="icordebugprocesswritememory-method"></a>ICorDebugProcess::WriteMemory – metoda
Zapíše data do oblasti paměti v tomto procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 [in] A `CORDB_ADDRESS` zapsat hodnotu, která je základní adresa paměti oblasti, ke kterým datům. Předtím, než dojde k přenosu dat, systém ověří, zda oblasti paměti o zadané velikosti, začínající na základní adrese přístupné pro zápis. Pokud není dostupný, metoda se nezdaří.  
  
 `size`  
 [in] Počet bajtů, které mají být zapsána do oblasti paměti.  
  
 `buffer`  
 [in] Vyrovnávací paměť, která obsahuje data, která má být proveden zápis.  
  
 `written`  
 [out] Ukazovat na proměnnou, která přijímá počet bajtů zapsaný na oblast paměti v tomto procesu. Pokud `written` má hodnotu NULL, tento parametr je ignorován.  
  
## <a name="remarks"></a>Poznámky  
 Data je zapsána automaticky za všechny zarážky. V rozhraní .NET Framework verze 2.0 nativní ladicí programy nepoužívejte tuto metodu vkládat zarážky na datový proud instrukcí. Použití [icordebugprocess2::setunmanagedbreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) místo.  
  
 `WriteMemory` Metoda by měla sloužit pouze mimo spravovaný kód. Tato metoda můžou poškodit modul runtime, pokud používá nesprávně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
