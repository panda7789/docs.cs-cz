---
title: ICLRDataTarget::SetThreadContext – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type:
- apiref
ms.openlocfilehash: cceafc8358ce2b0eafa62a3855c4eb1e96adae11
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113318"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a>ICLRDataTarget::SetThreadContext – metoda
Nastaví aktuální kontext zadaného vlákna v cílovém procesu. Tato metoda je volána službou Common Language Runtime (CLR) pro přístup k datům.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]   
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 pro Identifikátor operačního systému vlákna v cílovém procesu.  
  
 `contextSize`  
 pro Velikost kontextu.  
  
 `context`  
 pro Ukazatel na vyrovnávací paměť obsahující kontext.  
  
 Data ve vyrovnávací paměti `context` budou ve formátu `CONTEXT` struktury Win32. Kontext určuje data registru pro konkrétní procesor, takže definice struktury `CONTEXT` Win32 závisí na architektuře procesoru. Definici struktury `CONTEXT` Win32 najdete v souboru hlaviček WinNT. h.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je implementována modulem pro ladění aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** ClrData. idl, ClrData. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
