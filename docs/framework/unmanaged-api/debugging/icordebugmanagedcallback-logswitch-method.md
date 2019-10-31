---
title: ICorDebugManagedCallback::LogSwitch – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type:
- apiref
ms.openlocfilehash: a72eabb1b405c67f5603164e56a589a237603d2f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130698"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a>ICorDebugManagedCallback::LogSwitch – metoda
Oznamuje ladicímu programu, že spravované vlákno modulu CLR (Common Language Runtime) volalo metodu ve třídě <xref:System.Diagnostics.Switch> k vytvoření, úpravě nebo odstranění přepínače ladění/trasování.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a>Parametry  
 `PAppDomain`  
 pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující spravované vlákno, které vytvořil, upravil nebo odstranil přepínač ladění/trasování.  
  
 `pThread`  
 pro Ukazatel na objekt ICorDebugThread, který představuje spravované vlákno.  
  
 `lLevel`  
 pro Hodnota, která určuje úroveň závažnosti popisné zprávy, která byla zapsána do protokolu událostí.  
  
 `ulReason`  
 pro Hodnota výčtu [LogSwitchCallReason –](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) , která označuje operaci prováděnou na přepínači ladění/trasování.  
  
 `pLogSwitchName`  
 pro Ukazatel na název přepínače ladění/trasování.  
  
 `pParentName`  
 pro Ukazatel na název nadřazeného přepínače ladění/trasování.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
