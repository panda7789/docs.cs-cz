---
title: ICorDebugComObjectValue::GetCachedInterfaceTypes – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
helpviewer_keywords:
- GetCachedInterface method, ICorDebugComObjectValue interface [.NET Framework debugging]
- ICorDebugComObjectValue::GetCachedInterface method [.NET Framework debugging]
ms.assetid: d492284f-d3c5-4614-adb8-d718d5042500
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db1de215eaa0c0cc7021a119e54591caede76d3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugComObjectValue – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
