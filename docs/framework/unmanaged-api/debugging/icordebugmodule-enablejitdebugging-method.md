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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8aeb6ed448539db2720fee0d42cfcc344fd3bbf7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762773"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>ICorDebugModule::EnableJITDebugging – metoda
Určuje, zda kompilátor just-in-time (JIT) uchovává informace o ladění pro metody v rámci tohoto modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bTrackJITInfo`  
 [in] Nastavte tuto hodnotu na `true` umožňující kompilátor JIT pro zachování informací o mapování mezi Microsoft intermediate language (MSIL) verze a verze zkompilovaný pomocí kompilátoru JIT jednotlivých metod v tomto modulu.  
  
 `bAllowJitOpts`  
 [in] Nastavte tuto hodnotu na `true` umožňující kompilátor JIT pro generování kódu pomocí některé optimalizace JIT specifické pro ladění.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení pro všechny moduly, které jsou načteny, když je aktivní ladicí program je povoleno ladění JIT. Programově povolení nebo zakázání nastavení přepíše globální nastavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
