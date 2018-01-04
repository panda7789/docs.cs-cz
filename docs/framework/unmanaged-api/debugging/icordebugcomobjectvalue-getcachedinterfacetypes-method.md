---
title: "ICorDebugComObjectValue::GetCachedInterfaceTypes – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugComObjectValue::GetCachedInterfaceTypes
api_location: mscordbi.dll
f1_keywords: ICorDebugComObjectValue::GetCachedInterfaceTypes
helpviewer_keywords:
- GetCachedInterface method, ICorDebugComObjectValue interface [.NET Framework debugging]
- ICorDebugComObjectValue::GetCachedInterface method [.NET Framework debugging]
ms.assetid: d492284f-d3c5-4614-adb8-d718d5042500
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e99054b32deb6b2e4b621ea4c193e416220f8f6f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a>ICorDebugComObjectValue::GetCachedInterfaceTypes – metoda
Poskytuje enumerátor pro typy rozhraní, že byla přetypovat nebo použít jako aktuální objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bIInspectableOnly`  
 [v] Hodnotu, která určuje, zda metoda vrátí pouze [!INCLUDE[wrt](../../../../includes/wrt-md.md)] rozhraní (`IInspectable` rozhraní) nebo všech rozhraní COM mezipaměti obálka volatelná za běhu (RCW).  
  
 `ppInterfacesEnum`  
 [out] Ukazatel na adresu enumerátor ICorDebugTypeEnum, který poskytuje přístup k objektům ICorDebugType, které reprezentují typy v mezipaměti rozhraní filtrovaná podle `bIInspectableOnly`.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugComObjectValue – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
