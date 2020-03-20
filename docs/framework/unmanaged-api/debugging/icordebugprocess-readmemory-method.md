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
ms.openlocfilehash: 383e3f8990a1f355c94ff5e9f9daa69bdbdd97bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178654"
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
 [v] Hodnota, `CORDB_ADDRESS` která určuje základní adresu paměti, která má být přečtena.  
  
 `size`  
 [v] Počet bajtů, které mají být přečteny z paměti.  
  
 `buffer`  
 [out] Vyrovnávací paměť, která přijímá obsah paměti.  
  
 `read`  
 [out] Ukazatel na počet bajtů přenesených do zadané vyrovnávací paměti.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `ReadMemory` je primárně určena pro použití interop ladění ke kontrole oblastí paměti, které jsou používány nespravované části ladicí. Tuto metodu lze také ke čtení kódu zprostředkujícíjazyk společnosti Microsoft (MSIL) a nativní jit kompilovaný kód.  
  
 Všechny spravované zarážky budou odebrány z dat, která je vrácena v parametru. `buffer` Nebudou provedeny žádné úpravy pro nativní zarážky nastavené [iCorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).  
  
 Není prováděno ukládání paměti procesu do mezipaměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
