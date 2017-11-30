---
title: "ICorDebugProcess::ReadMemory – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.ReadMemory
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33345ada6606bc1a43a630340251d3ba1404b2f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessreadmemory-method"></a>ICorDebugProcess::ReadMemory – metoda
Přečte zadaný oblasti paměti pro tento proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [v] A `CORDB_ADDRESS` hodnotu, která určuje základní adresu paměti čtení.  
  
 `size`  
 [v] Počet bajtů ke čtení z paměti.  
  
 `buffer`  
 [out] Vyrovnávací paměť, která přijímá obsah paměti.  
  
 `read`  
 [out] Ukazatel na počet bajtů přenesených do zadané vyrovnávací paměti.  
  
## <a name="remarks"></a>Poznámky  
 `ReadMemory` Metoda je primárně určen pro použití pomocí zprostředkovatele komunikace s objekty ladění kontrola oblasti paměti, které jsou používány nespravované část ladění. Tuto metodu můžete také použít ke čtení kód Microsoft intermediate language (MSIL) a nativní kód kompilována.  
  
 Všechny spravované zarážky se odebere z data, která je vrácena v `buffer` parametr. Bez úprav budou provedeny pro nativní zarážky nastaven [icordebugprocess2::setunmanagedbreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).  
  
 Neprobíhá žádná ukládání do mezipaměti v paměti procesu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
