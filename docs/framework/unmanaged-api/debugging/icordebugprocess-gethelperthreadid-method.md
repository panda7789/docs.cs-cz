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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd5e30d08e667dcd5a8be1f9502462f28290068e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494217"
---
# <a name="icordebugprocessgethelperthreadid-method"></a>ICorDebugProcess::GetHelperThreadID – metoda
Získá ID vlákna operačního systému (OS) interní pomocné vlákno ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pThreadID`  
 [out] Ukazatel na operační systém vlákna ID interní pomocné vlákno ladicího programu.  
  
## <a name="remarks"></a>Poznámky  
 Při ladění spravované a nespravované, zodpovídá za ladicího programu k zajištění, že vlákno se zadaným ID zůstane spuštěný, pokud ho narazí na zarážku, umístí ladicím programem. Ladicí program může také chtít skrýt toto vlákno od uživatele. Pokud neexistuje žádný pomocné vlákno v procesu ještě, `GetHelperThreadID` metoda vrátí nulu v *`pThreadID`.  
  
 ID vlákna pomocné vlákno nemůže mezipaměti, protože to může v průběhu času měnit. ID vlákna v každé události zastavení musíte znovu odeslán dotaz.  
  
 ID vlákna pomocné vlákno ladicího programu bude správné na každý nespravované [icordebugmanagedcallback::CreateThread –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) událostí, což umožní ladicí program k určení ID vlákna z jeho pomocné vlákno a skryjte ji pro uživatele. Podproces, který je označen jako pomocné vlákno během nespravované `ICorDebugManagedCallback::CreateThread` událostí bude nespouštět spravovaného uživatelského kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl. CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
