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
ms.openlocfilehash: eaf5b9980d55b0efb473b4631a8c052b013d0796
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137260"
---
# <a name="icordebugprocesswritememory-method"></a>ICorDebugProcess::WriteMemory – metoda
Zapisuje data do oblasti paměti v tomto procesu.  
  
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
 pro Hodnota `CORDB_ADDRESS`, která je základní adresou oblasti paměti, do které se zapisují data. Než dojde k přenosu dat, systém ověří, že oblast paměti zadané velikosti, která začíná na základní adrese, je přístupná pro zápis. Pokud není k dispozici, metoda se nezdařila.  
  
 `size`  
 pro Počet bajtů, které mají být zapsány do oblasti paměti.  
  
 `buffer`  
 pro Vyrovnávací paměť obsahující data, která mají být zapsána.  
  
 `written`  
 mimo Ukazatel na proměnnou, která přijímá počet bajtů zapsaných do oblasti paměti v tomto procesu. Pokud je `written` NULL, tento parametr se ignoruje.  
  
## <a name="remarks"></a>Poznámky  
 Data se automaticky zapisují za všechny zarážky. V .NET Framework verze 2,0 by nativní ladicí program neměl tuto metodu použít pro vložení zarážek do datového proudu instrukcí. Místo toho použijte [ICorDebugProcess2:: SetUnmanagedBreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) .  
  
 Metoda `WriteMemory` by měla být použita pouze mimo spravovaný kód. Tato metoda může poškodit modul runtime, pokud je použit nesprávně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
