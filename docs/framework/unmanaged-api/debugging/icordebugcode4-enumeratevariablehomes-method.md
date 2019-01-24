---
title: ICorDebugCode4::EnumerateVariableHomes – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c765cb2e0e59fe2fcac562fdb2e926e878298c1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530275"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a>ICorDebugCode4::EnumerateVariableHomes – metoda
Získá enumerátor pro místní proměnné a argumenty ve funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 Ukazatel na adresu [icordebugvariablehomeenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) rozhraní objektu, který je enumerátor pro místní proměnné a argumenty ve funkci.  
  
## <a name="remarks"></a>Poznámky  
 [Icordebugvariablehomeenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) objektu rozhraní je standardní enumerátor odvozen z rozhraní "ICorDebugEnum", který umožňuje vytvořit výčet [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objekty. Kolekce může zahrnovat více [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objekty pro stejný index pozice nebo argument, pokud mají různé domovů v různých fázích funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugCode4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
