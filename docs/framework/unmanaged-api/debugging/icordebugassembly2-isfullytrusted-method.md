---
title: ICorDebugAssembly2::IsFullyTrusted – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2.IsFullyTrusted
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type:
- apiref
ms.openlocfilehash: bef51fe9df0f85659603c637f11ed4e856c8e01a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133956"
---
# <a name="icordebugassembly2isfullytrusted-method"></a>ICorDebugAssembly2::IsFullyTrusted – metoda
Získá hodnotu, která označuje, zda bylo sestavení uděleno úplnému vztahu důvěryhodnosti systémem zabezpečení modulu runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbFullyTrusted`  
 [out] `true`, pokud je sestavení uděleno úplnému vztahu důvěryhodnosti systémem zabezpečení modulu runtime; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí hodnotu HRESULT prvku CORDBG_E_NOTREADY, pokud zásady zabezpečení pro sestavení ještě nebyly přeloženy, to znamená, pokud dosud nebyl spuštěn žádný kód v sestavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
