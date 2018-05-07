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
ms.openlocfilehash: 6da4c282c7f969a406a657d1e30dd6120a32b4e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocesswritememory-method"></a>ICorDebugProcess::WriteMemory – metoda
Zapisuje data do oblast paměti v tomto procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [v] A `CORDB_ADDRESS` hodnotu, která je základní adresa oblasti paměti pro data, která je zapsán. Předtím, než dojde k přenosu dat, systém ověřuje, že oblasti paměti zadané velikosti, začínající na základní adrese, je dostupná pro zápis. Pokud není dostupný, metoda se nezdaří.  
  
 `size`  
 [v] Počet bajtů, které mají být zapsána do oblasti paměti.  
  
 `buffer`  
 [v] Vyrovnávací paměť, která obsahuje data, která má být proveden zápis.  
  
 `written`  
 [out] Ukazatel na proměnnou, která přijímá počet bajtů zapsaných na oblast paměti v tomto procesu. Pokud `written` má hodnotu NULL, je tento parametr ignorován.  
  
## <a name="remarks"></a>Poznámky  
 Data se automaticky zapisuje za jakékoli zarážky. V rozhraní .NET Framework verze 2.0 nativní ladicí programy nepoužívejte tuto metodu vložení zarážky do datového proudu instrukcí. Použití [icordebugprocess2::setunmanagedbreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) místo.  
  
 `WriteMemory` Metoda má být použita pouze mimo spravovaný kód. Tato metoda může poškodit modul runtime, pokud používá nesprávně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
