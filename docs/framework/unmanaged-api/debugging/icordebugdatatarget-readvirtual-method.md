---
title: ICorDebugDataTarget::ReadVirtual – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.ReadVirtual Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d9e619e4176633074242521133d42f191f140ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugdatatargetreadvirtual-method"></a>ICorDebugDataTarget::ReadVirtual – metoda
Získá blok souvislé paměti začínající na zadanou adresu a vrátí ji v poskytnutá vyrovnávací paměť.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [v] Počáteční adresa požadovanou paměť.  
  
 `pbuffer`  
 [out] Vyrovnávací paměť, kde bude uložena paměti.  
  
 `bytesRequested`  
 [v] Počet bajtů, které mají získat z cílovou adresu.  
  
 `pBytesRead`  
 [out] Počet bajtů ve skutečnosti čtení z cílovou adresu. To může být méně než `bytesRequested`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud lze číst prvního bajtu (na adrese zadaným počátečním), by měla vrátit volání úspěšné (pro podporu efektivní čtení datových struktur s popisující samy sebe délka jako řetězce ukončené hodnotou null).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
