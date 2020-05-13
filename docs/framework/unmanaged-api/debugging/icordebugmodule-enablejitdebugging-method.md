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
ms.openlocfilehash: bdf027f94c8416d052cb807d04be76a39868ccf7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212929"
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
 pro Nastavte tuto hodnotu, chcete-li `true` Povolit kompilátoru JIT zachovat informace o mapování mezi verzí jazyka MSIL (Microsoft Intermediate Language) a verzí zkompilované kompilátorem JIT pro každou metodu v tomto modulu.  
  
 `bAllowJitOpts`  
 pro Nastavte tuto hodnotu na `true` , pokud chcete, aby kompilátor JIT vygeneroval kód s některými optimalizacemi specifickými pro JIT pro ladění.  
  
## <a name="remarks"></a>Poznámky  
 Ladění JIT je ve výchozím nastavení povoleno pro všechny moduly, které jsou načteny, když je ladicí program aktivní. Programové povolení nebo zakázání nastavení přepisuje globální nastavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
