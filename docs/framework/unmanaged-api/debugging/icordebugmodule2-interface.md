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
ms.openlocfilehash: a3a1b658f4ab05c7029de907882fe5ab2513ccd8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127887"
---
# <a name="icordebugmodule2-interface"></a>ICorDebugModule2 – rozhraní

Slouží jako logické rozšíření rozhraní ICorDebugModule.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ApplyChanges – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|Aplikuje změny v metadatech a změny v kódu jazyka MSIL (Microsoft Intermediate Language) na běžící proces.|  
|[GetJITCompilerFlags – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|Získá příznaky, které řídí kompilaci JIT (just-in-time) pro tento `ICorDebugModule2`.|  
|[ResolveAssembly – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|Přeloží sestavení, na které odkazuje zadaný token metadat.|  
|[SetJITCompilerFlags – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|Nastaví příznaky, které řídí kompilaci JIT pro tento `ICorDebugModule2`.|  
|[SetJMCStatus – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|Nastaví Pouze můj kód (JMC) pro všechny metody všech tříd v tomto `ICorDebugModule2` na zadanou hodnotu, s výjimkou těch v poli `pTokens`, které se nastaví na opačnou hodnotu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
