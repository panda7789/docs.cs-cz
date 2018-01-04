---
title: "ICorDebugProcess::WriteMemory – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.WriteMemory
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a1a12d1393d1db69ea47833958fdf828b552064
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
