---
title: ICorDebugInternalFrame::GetFrameType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame.GetFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type:
- apiref
ms.openlocfilehash: b7a33fd6e2178e0e9188b81f516b231702fb6460
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122718"
---
# <a name="icordebuginternalframegetframetype-method"></a>ICorDebugInternalFrame::GetFrameType – metoda
Získá typ tohoto interního rámce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pType`  
 mimo Ukazatel na hodnotu výčtu CorDebugInternalFrameType –, která určuje typ vnitřního rámce reprezentovaného tímto objektem `ICorDebugInternalFrame`.  
  
## <a name="remarks"></a>Poznámky  
 Interní typ rámce nikdy nebude STUBFRAME_NONE. Ladicí programy by měly korektně ignorovat nerozpoznané typy vnitřních rámců.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
