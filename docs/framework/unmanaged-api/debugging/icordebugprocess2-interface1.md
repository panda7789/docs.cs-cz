---
title: ICorDebugProcess2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3009ee6a2ba22771a2132032744f76ca527c422
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965680"
---
# <a name="icordebugprocess2-interface"></a>ICorDebugProcess2 – rozhraní
Logické rozšíření icordebugprocess – rozhraní, která představuje proces spuštění spravovaného kódu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ClearUnmanagedBreakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|Odstraní zarážku v zadaném posunu, který nastavil dřívějším volání `ICorDebugProcess2::SetUnmanagedBreakpoint`.|  
|[GetDesiredNGENCompilerFlags – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|Získá příznaky, které musí být nastavena pro modul common language runtime (CLR) pro načtení obrázku do procesu odkazovaná tímto objektem `ICorDebugProcess2`.|  
|[GetReferenceValueFromGCHandle – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|Získá odkaz na ukazatel na zadaný spravovaný objekt, který má uvolňování paměti zpracovávají.|  
|[GetThreadForTaskID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|Získá vlákno, na kterých je prováděna úloha se zadaným identifikátorem.|  
|[GetVersion – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|Získá verzi CLR, na kterém je spuštěna laděného procesu.|  
|[SetDesiredNGENCompilerFlags – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|Nastaví příznaky, které jsou požadovány pro kompilátor just-in-time (JIT) pro načtení obrázku do laděného procesu.|  
|[SetUnmanagedBreakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|Nastaví nespravované zarážku posunem zadaným nativních bitových kopií.|  
  
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
