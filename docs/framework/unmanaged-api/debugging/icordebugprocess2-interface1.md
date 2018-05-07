---
title: Icordebugprocess2 – Interface1
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
ms.openlocfilehash: 6a1588a37891d6a73c49cb1b9ccbc81d9dcdb7e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess2-interface1"></a>Icordebugprocess2 – Interface1
Logické rozšíření ICorDebugProcess rozhraní, která představuje proces spuštěním spravovaného kódu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ClearUnmanagedBreakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|Odebere zarážek na zadaném posunu nastavený starší voláním `ICorDebugProcess2::SetUnmanagedBreakpoint`.|  
|[GetDesiredNGENCompilerFlags – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|Získá příznaky, které musejí být nastaveny pro modul CLR (CLR) a načte bitovou kopii do procesu odkazuje toto `ICorDebugProcess2`.|  
|[GetReferenceValueFromGCHandle – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|Získá odkaz na ukazatel na zadaný spravovaný objekt, který je uvolnění paměti zpracovat.|  
|[GetThreadForTaskID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|Získá vláken, na kterém je prováděna úloha se zadaným identifikátorem.|  
|[GetVersion – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|Získá verzi modulu CLR, na kterém je spuštěn proces laděné.|  
|[SetDesiredNGENCompilerFlags – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|Nastaví příznaky, které jsou požadovány pro kompilátor za běhu (JIT) a načte bitovou kopii do procesu laděné.|  
|[SetUnmanagedBreakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|Nastaví nespravované zarážek na posunu zadaný nativních bitových kopií.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
