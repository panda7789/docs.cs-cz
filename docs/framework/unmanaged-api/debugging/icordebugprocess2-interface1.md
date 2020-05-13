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
ms.openlocfilehash: 1a57b7ceb6da961fba1f0d6e8e0ba1aa88ca0541
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213488"
---
# <a name="icordebugprocess2-interface"></a>ICorDebugProcess2 – rozhraní
Logické rozšíření rozhraní ICorDebugProcess, které představuje proces spouštějící spravovaný kód.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ClearUnmanagedBreakpoint – metoda](icordebugprocess2-clearunmanagedbreakpoint-method.md)|Odstraní zarážku na zadaném posunu, který byl nastaven dřívějším voláním metody `ICorDebugProcess2::SetUnmanagedBreakpoint` .|  
|[GetDesiredNGENCompilerFlags – metoda](icordebugprocess2-getdesiredngencompilerflags-method.md)|Získá příznaky, které musí být nastaveny pro modul CLR (Common Language Runtime) k načtení obrázku do procesu, na který odkazuje `ICorDebugProcess2` .|  
|[GetReferenceValueFromGCHandle – metoda](icordebugprocess2-getreferencevaluefromgchandle-method.md)|Získá ukazatel odkazu na zadaný spravovaný objekt, který má popisovač uvolňování paměti.|  
|[GetThreadForTaskID – metoda](icordebugprocess2-getthreadfortaskid-method.md)|Získá vlákno, na kterém je spuštěn úkol se zadaným identifikátorem.|  
|[GetVersion – metoda](icordebugprocess2-getversion-method.md)|Získá verzi modulu CLR, na které je spuštěn proces ladění.|  
|[SetDesiredNGENCompilerFlags – metoda](icordebugprocess2-setdesiredngencompilerflags-method.md)|Nastaví příznaky, které jsou požadovány pro kompilátor JIT (just-in-time) k načtení obrázku do laděného procesu.|  
|[SetUnmanagedBreakpoint – metoda](icordebugprocess2-setunmanagedbreakpoint-method.md)|Nastaví nespravovanou zarážku na zadaném posunu nativní bitové kopie.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
