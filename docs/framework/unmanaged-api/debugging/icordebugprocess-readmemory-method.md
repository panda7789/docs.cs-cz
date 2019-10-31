---
title: ICorDebugProcess::ReadMemory – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ReadMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type:
- apiref
ms.openlocfilehash: ef9e339c74b2d2785d758ed9c4adfc1901073253
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139357"
---
# <a name="icordebugprocessreadmemory-method"></a>ICorDebugProcess::ReadMemory – metoda
Přečte zadanou oblast paměti pro tento proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 pro Hodnota `CORDB_ADDRESS`, která určuje základní adresu paměti, která se má číst.  
  
 `size`  
 pro Počet bajtů, které mají být načteny z paměti.  
  
 `buffer`  
 mimo Vyrovnávací paměť, která přijímá obsah paměti.  
  
 `read`  
 mimo Ukazatel na počet bajtů přenesených do zadané vyrovnávací paměti.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `ReadMemory` je primárně určena pro účely ladění v oblasti paměti, které jsou používány nespravovanou částí laděného procesu. Tuto metodu lze také použít ke čtení kódu jazyka MSIL (Microsoft Intermediate Language) a nativního kódu kompilovaného JIT.  
  
 Všechny spravované zarážky budou odebrány z dat vrácených v parametru `buffer`. Pro nativní zarážky nastavené pomocí [ICorDebugProcess2:: SetUnmanagedBreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)se nevytvoří žádné úpravy.  
  
 Není provedeno ukládání paměti procesu do mezipaměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
