---
title: ICorDebugProcess::GetHandle – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
ms.openlocfilehash: e4061580d59b0cf2a6e6e481d5242005e9452caf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128876"
---
# <a name="icordebugprocessgethandle-method"></a>ICorDebugProcess::GetHandle – metoda
Získá popisovač procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a>Parametry  
 `phProcessHandle`  
 mimo Ukazatel na `HPROCESS`, který je popisovačem procesu.  
  
## <a name="remarks"></a>Poznámky  
 Načtený popisovač je vlastněn rozhraním pro ladění. Ladicí program by měl před použitím Duplikovat popisovač.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
