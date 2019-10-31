---
title: ICorDebugThread::GetHandle – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
ms.openlocfilehash: 33219d9a67379244e23da49c13617a4c4a2fa66d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133455"
---
# <a name="icordebugthreadgethandle-method"></a>ICorDebugThread::GetHandle – metoda
Získá aktuální popisovač pro aktivní část tohoto ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phThreadHandle`  
 mimo Ukazatel na HTHREAD, který je popisovačem aktivní části tohoto vlákna.  
  
## <a name="remarks"></a>Poznámky  
 Popisovač se může změnit, protože se spustí proces a může se lišit pro různé části vlákna.  
  
 Tento popisovač je vlastněn rozhraním API pro ladění. Ladicí program by ho měl před použitím duplikovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
