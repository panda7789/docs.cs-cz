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
ms.openlocfilehash: dca2a4e5ee869346108137a8ba01ab8855756725
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792561"
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
  
 Všechny spravované zarážky budou odebrány z dat vrácených v parametru `buffer`. Pro nativní zarážky nastavené pomocí [ICorDebugProcess2:: SetUnmanagedBreakpoint –](icordebugprocess2-setunmanagedbreakpoint-method.md)se nevytvoří žádné úpravy.  
  
 Není provedeno ukládání paměti procesu do mezipaměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
