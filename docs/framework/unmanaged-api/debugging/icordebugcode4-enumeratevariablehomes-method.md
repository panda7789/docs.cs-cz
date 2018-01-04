---
title: "ICorDebugCode4::EnumerateVariableHomes – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugCode4.EnumerateVariableHomes
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1478ed89c216f9cd520bf1122571f09024283ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
 Ukazatel na adresu [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) rozhraní objekt, který je enumerátor pro místní proměnné a argumenty ve funkci.  
  
## <a name="remarks"></a>Poznámky  
 [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) objekt rozhraní je standardní enumerátor odvozen z rozhraní "ICorDebugEnum", který umožňuje vytvořit výčet [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objekty. Kolekce může obsahovat více [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objekty pro stejný index slotu nebo argument, pokud mají různé domácnostech v různých fázích funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugCode4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
