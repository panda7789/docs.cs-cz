---
title: ICorDebugModule2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 192f2476aff91d3a8302d070852ab2a3722d137c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970126"
---
# <a name="icordebugmodule2-interface"></a>ICorDebugModule2 – rozhraní

Slouží jako logické rozšíření pro icordebugmodule – rozhraní  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ApplyChanges – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|Změny v metadatech a změny v kódu Microsoft intermediate language (MSIL) se vztahuje na běžící proces.|  
|[GetJITCompilerFlags – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|Získá příznaky, které řídí kompilace just-in-time (JIT) pro tuto `ICorDebugModule2`.|  
|[ResolveAssembly – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|Přeloží sestavení odkazuje token Zadaná metadata.|  
|[SetJITCompilerFlags – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|Nastaví příznaky, které řídí JIT kompilace `ICorDebugModule2`.|  
|[SetJMCStatus – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|Nastaví stav pouze můj kód (JMC) všech metod všechny třídy v tomto `ICorDebugModule2` se zadanou hodnotou, s výjimkou těch, `pTokens` pole, které se nastaví na opačnou hodnotu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
