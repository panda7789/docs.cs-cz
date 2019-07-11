---
title: ICorDebugThread::CreateEval – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41bd4c0bb4e84b6d6f267e24808baafa57f71882
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771118"
---
# <a name="icordebugthreadcreateeval-method"></a>ICorDebugThread::CreateEval – metoda
Vytvoří objekt icordebugeval –, který shromažďuje a zveřejňuje funkce tento ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEval`  
 [out] Ukazatel na adresu `ICorDebugEval` objekt, který shromažďuje a zveřejňuje funkce pro toto vlákno.  
  
## <a name="remarks"></a>Poznámky  
 Objekt vyhodnocení zařadí nový řetězec ve vlákně než přistoupíte k jeho výpočtu. Přeruší se výpočet aktuálně se provést ve vlákně, dokud se nedokončí hodnocení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
