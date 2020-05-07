---
title: ICorDebugChain::GetCaller – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
ms.openlocfilehash: a6d26924773e6ad505975402ec3ace150d02cc3a
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894619"
---
# <a name="icordebugchaingetcaller-method"></a>ICorDebugChain::GetCaller – metoda
Získá řetězec, který se nazývá tento řetězec.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppChain`  
 mimo Ukazatel na adresu objektu ICorDebugChain, který představuje volající řetězec.  
  
 Pokud byl tento řetěz spontánním způsobem volán (jako by se jednalo o případ, kdy tento řetěz nebo ladicí program inicializoval zásobník `ppChain` volání), bude mít hodnotu null.  
  
## <a name="remarks"></a>Poznámky  
 Volající řetěz může být v jiném vlákně, pokud bylo volání zařazeno mezi vlákny.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
