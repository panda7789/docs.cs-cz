---
title: ICLRDataTarget::GetThreadContext – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type:
- apiref
ms.openlocfilehash: 3777ad4b12c7d0593c095c470aba81088137a859
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179182"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a>ICLRDataTarget::GetThreadContext – metoda
Získá aktuální kontext spuštění pro dané vlákno v cílovém procesu. Tato metoda je volána služby přístupu k datům za běhu běžného jazyka.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 [v] Identifikátor operačního systému podprocesu v cílovém procesu.  
  
 `contextFlags`  
 [v] Příznaky, které určují, které části kontextu vrátit. Implementace vrátí alespoň tyto části kontextu.  
  
 `contextSize`  
 [v] Velikost kontextu.  
  
 `context`  
 [out] Ukazatel na vyrovnávací paměť, do které chcete umístit kontext.  
  
 Data ve `context` vyrovnávací paměti musí být ve formátu `CONTEXT` Win32 struktury. Kontext určuje data registru specifické pro procesor, takže definice `CONTEXT` win32 struktury závisí na architektuře procesoru. Definice struktury Win32 `CONTEXT` naleznete v souboru záhlaví winnt.h.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je implementována zapisovače ladicí aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRDataTarget – rozhraní](iclrdatatarget-interface.md)
