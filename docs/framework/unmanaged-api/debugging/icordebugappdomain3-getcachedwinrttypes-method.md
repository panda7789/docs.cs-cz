---
title: "ICorDebugAppDomain3::GetCachedWinRTTypes – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain3.GetCachedWinRTTypes
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain3::GetCachedWinRTTypes
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes method [.NET Framework debugging]
- GetCachedWinRTTypes method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 9afd0e04-a403-41e2-9528-a6dcbcdcbd4d
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 49b36b907df514873815ac28565c5796d997c191
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypes – metoda
Získá enumerátor pro všechny uložené v mezipaměti [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppGuidToTypeEnum`  
 [out] Ukazatel na [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) rozhraní objekt, který můžete vytvořit výčet spravovaných reprezentace [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy momentálně načtených v doméně aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugAppDomain3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
