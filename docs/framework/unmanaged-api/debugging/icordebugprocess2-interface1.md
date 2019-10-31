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
ms.openlocfilehash: 213eb86c36225a6194af83c04c469fbe0cc51b63
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137151"
---
# <a name="icordebugprocess2-interface"></a>ICorDebugProcess2 – rozhraní
Logické rozšíření rozhraní ICorDebugProcess, které představuje proces spouštějící spravovaný kód.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ClearUnmanagedBreakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|Odstraní zarážku na zadaném posunu, který byl nastaven dřívějším voláním `ICorDebugProcess2::SetUnmanagedBreakpoint`.|  
|[GetDesiredNGENCompilerFlags – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|Získá příznaky, které musí být nastaveny pro modul CLR (Common Language Runtime) pro načtení obrázku do procesu, na který odkazuje tento `ICorDebugProcess2`.|  
|[GetReferenceValueFromGCHandle – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|Získá ukazatel odkazu na zadaný spravovaný objekt, který má popisovač uvolňování paměti.|  
|[GetThreadForTaskID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|Získá vlákno, na kterém je spuštěn úkol se zadaným identifikátorem.|  
|[GetVersion – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|Získá verzi modulu CLR, na které je spuštěn proces ladění.|  
|[SetDesiredNGENCompilerFlags – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|Nastaví příznaky, které jsou požadovány pro kompilátor JIT (just-in-time) k načtení obrázku do laděného procesu.|  
|[SetUnmanagedBreakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|Nastaví nespravovanou zarážku na zadaném posunu nativní bitové kopie.|  
  
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
