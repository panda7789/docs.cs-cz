---
title: ICorDebugModule::EnableJITDebugging – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
ms.openlocfilehash: da532ee1b5909a68bedbb9e6f6c96333e88002a8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109730"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>ICorDebugModule::EnableJITDebugging – metoda
Určuje, zda kompilátor JIT (just-in-time) zachovává ladicí informace pro metody v rámci tohoto modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bTrackJITInfo`  
 pro Nastavte tuto hodnotu na `true`, pokud chcete, aby kompilátor JIT zachoval informace o mapování mezi verzí jazyka MSIL (Microsoft Intermediate Language) a verzí kompilovánou JIT pro všechny metody v tomto modulu.  
  
 `bAllowJitOpts`  
 pro Nastavte tuto hodnotu na `true`, pokud chcete, aby kompilátor JIT vygeneroval kód s některými optimalizacemi specifickými pro JIT pro ladění.  
  
## <a name="remarks"></a>Poznámky  
 Ladění JIT je ve výchozím nastavení povoleno pro všechny moduly, které jsou načteny, když je ladicí program aktivní. Programové povolení nebo zakázání nastavení přepisuje globální nastavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
