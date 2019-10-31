---
title: ICorDebugDataTarget::GetPlatform – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetPlatform Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type:
- apiref
ms.openlocfilehash: 5715f0634346dd0c6591cfe5687690aa0fba95f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125321"
---
# <a name="icordebugdatatargetgetplatform-method"></a>ICorDebugDataTarget::GetPlatform – metoda
Obsahuje informace o platformě, včetně architektury procesoru a operačního systému, na kterých je spuštěn cílový proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a>Parametry  
 `pTargetPlatform`  
 mimo Ukazatel na výčet [CorDebugPlatformEnum –](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) , který popisuje cílovou platformu.  
  
## <a name="remarks"></a>Poznámky  
 Návratovou hodnotu výčtu `CorDebugPlatformEnum` používá rozhraní [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) k určení podrobností o cílovém procesu, jako je jeho velikost ukazatele, rozložení adresního prostoru, sada registrů, formát instrukcí, rozložení kontextu a konvence volání.  
  
 Hodnota `pTargetPlatform` může odkazovat na platformu, která je emulovana pro cíl, a nikoli určit skutečný hardware, který se používá. Například proces, který je spuštěný v prostředí Windows on Windows (WOW), v 64ové edici operačního systému Windows by měl používat `CORDB_PLATFORM_WINDOWS_X86` hodnotu výčtu [CorDebugPlatformEnum –](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) .  
  
 Tato metoda musí být úspěšná. Pokud dojde k chybě, cílová platforma nebude použitelná. Tato metoda může selhat z následujících důvodů:  
  
- Platforma, která je emulovana pro cíl, je nepoužitelná.  
  
- Skutečný hardware na cílové platformě je nepoužitelný.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
