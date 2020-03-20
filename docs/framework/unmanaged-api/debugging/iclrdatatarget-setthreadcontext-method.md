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
ms.openlocfilehash: d76a907434b12b85aaedeef169390ec6f0df724a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179130"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a>ICLRDataTarget::SetThreadContext – metoda
Nastaví aktuální kontext zadaného vlákna v cílovém procesu. Tato metoda je volána služby přístupu k datům CLR (COMMON Language runtime).  
  
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
 [v] Identifikátor operačního systému podprocesu v cílovém procesu.  
  
 `contextSize`  
 [v] Velikost kontextu.  
  
 `context`  
 [v] Ukazatel na vyrovnávací paměť obsahující kontext.  
  
 Data ve `context` vyrovnávací paměti budou ve formátu win32 `CONTEXT` struktury. Kontext určuje data registru specifické pro procesor, takže definice `CONTEXT` win32 struktury závisí na architektuře procesoru. Definice struktury Win32 `CONTEXT` naleznete v souboru záhlaví winnt.h.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je implementována zapisovače ladicí aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRDataTarget – rozhraní](iclrdatatarget-interface.md)
