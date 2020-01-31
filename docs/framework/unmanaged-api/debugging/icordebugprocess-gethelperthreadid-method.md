---
title: ICorDebugProcess::GetHelperThreadID – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
ms.openlocfilehash: d0dc301c67d09ebb15bf47cef15e642fb7c78fb9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792610"
---
# <a name="icordebugprocessgethelperthreadid-method"></a>ICorDebugProcess::GetHelperThreadID – metoda
Získá ID vlákna operačního systému (OS) vnitřního pomocného vlákna ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pThreadID`  
 mimo Ukazatel na ID vlákna operačního systému interní pomocné vlákno ladicího programu.  
  
## <a name="remarks"></a>Poznámky  
 Během spravovaného a nespravovaného ladění se jedná o zodpovědnost ladicího programu, aby se zajistilo, že vlákno se zadaným ID zůstává spuštěné, pokud narazí na zarážku umístěnou ladicím programem. Ladicí program může také skrýt toto vlákno od uživatele. Pokud v procesu ještě neexistuje žádný pomocný podproces, metoda `GetHelperThreadID` vrátí nulu ve *`pThreadID`.  
  
 Nemůžete ukládat do mezipaměti ID vlákna pomocných vláken, protože se může v průběhu času měnit. Při každé události zastavení musíte znovu zadat dotaz na ID vlákna.  
  
 ID vlákna pomocného vlákna ladicího programu bude v každé nespravované události [ICorDebugManagedCallback:: CreateThread](icordebugmanagedcallback-createthread-method.md) správné, což umožňuje ladicímu programu určit ID vlákna jeho pomocného vlákna a skrýt ho od uživatele. Vlákno, které je identifikováno jako pomocné vlákno během nespravované události `ICorDebugManagedCallback::CreateThread`, nikdy nespustí spravovaný kód uživatele.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl. CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
