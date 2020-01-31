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
ms.openlocfilehash: 32774aacecf3e56510bc6f0670538a44fde794c9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792989"
---
# <a name="icordebugmodule2-interface"></a>ICorDebugModule2 – rozhraní

Slouží jako logické rozšíření rozhraní ICorDebugModule.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ApplyChanges – metoda](icordebugmodule2-applychanges-method.md)|Aplikuje změny v metadatech a změny v kódu jazyka MSIL (Microsoft Intermediate Language) na běžící proces.|  
|[GetJITCompilerFlags – metoda](icordebugmodule2-getjitcompilerflags-method.md)|Získá příznaky, které řídí kompilaci JIT (just-in-time) pro tento `ICorDebugModule2`.|  
|[ResolveAssembly – metoda](icordebugmodule2-resolveassembly-method.md)|Přeloží sestavení, na které odkazuje zadaný token metadat.|  
|[SetJITCompilerFlags – metoda](icordebugmodule2-setjitcompilerflags-method.md)|Nastaví příznaky, které řídí kompilaci JIT pro tento `ICorDebugModule2`.|  
|[SetJMCStatus – metoda](icordebugmodule2-setjmcstatus-method.md)|Nastaví Pouze můj kód (JMC) pro všechny metody všech tříd v tomto `ICorDebugModule2` na zadanou hodnotu, s výjimkou těch v poli `pTokens`, které se nastaví na opačnou hodnotu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
