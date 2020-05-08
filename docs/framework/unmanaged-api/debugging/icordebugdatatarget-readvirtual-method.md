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
ms.openlocfilehash: 36a18d92f05db55957bba55de84490c0da1a1f86
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976509"
---
# <a name="icordebugdatatargetreadvirtual-method"></a>ICorDebugDataTarget::ReadVirtual – metoda
Načte blok souvislé paměti začínající na zadané adrese a vrátí ji do zadané vyrovnávací paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 pro Počáteční adresa požadované paměti.  
  
 `pbuffer`  
 mimo Vyrovnávací paměť, do které se uloží paměť.  
  
 `bytesRequested`  
 pro Počet bajtů, které mají být získány z cílové adresy.  
  
 `pBytesRead`  
 mimo Počet bajtů skutečně přečtených z cílové adresy. To může být méně než `bytesRequested`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je možné číst první bajt (na zadané počáteční adrese), volání by mělo vracet úspěch (pro podporu efektivního čtení datových struktur s délkou, jako jsou řetězce zakončené znakem null).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugDataTarget – rozhraní](icordebugdatatarget-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
