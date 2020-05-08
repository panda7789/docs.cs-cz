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
ms.openlocfilehash: 3df35d52a4e5209b282ccef653b065bdcf1f8fe4
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976535"
---
# <a name="icordebugdatatargetgetplatform-method"></a>ICorDebugDataTarget::GetPlatform – metoda
Obsahuje informace o platformě, včetně architektury procesoru a operačního systému, na kterých je spuštěn cílový proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a>Parametry  
 `pTargetPlatform`  
 mimo Ukazatel na výčet [CorDebugPlatformEnum –](cordebugplatform-enumeration.md) , který popisuje cílovou platformu.  
  
## <a name="remarks"></a>Poznámky  
 Návratová hodnota `CorDebugPlatformEnum` výčtu je používána rozhraním [ICorDebug](icordebug-interface.md) k určení podrobností o cílovém procesu, jako je jeho velikost ukazatele, rozložení adresního prostoru, sada registrů, formát instrukcí, rozložení kontextu a konvence volání.  
  
 `pTargetPlatform` Hodnota se může vztahovat na platformu, která je emulovaná pro cíl, a ne zadání samotného používaného hardwaru. Například proces, který je spuštěný v prostředí Windows on Windows (WOW) na 64 edici operačního systému Windows, by měl používat `CORDB_PLATFORM_WINDOWS_X86` hodnotu výčtu [CorDebugPlatformEnum –](cordebugplatform-enumeration.md) .  
  
 Tato metoda musí být úspěšná. Pokud dojde k chybě, cílová platforma nebude použitelná. Tato metoda může selhat z následujících důvodů:  
  
- Platforma, která je emulovana pro cíl, je nepoužitelná.  
  
- Skutečný hardware na cílové platformě je nepoužitelný.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugDataTarget – rozhraní](icordebugdatatarget-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
