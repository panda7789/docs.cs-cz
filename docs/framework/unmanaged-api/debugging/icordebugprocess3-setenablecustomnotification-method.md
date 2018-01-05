---
title: "ICorDebugProcess3::SetEnableCustomNotification – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess3.SetEnableCustomNotification Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ccd1f4b6be56202d5efea1d2e38dce554835218
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a>ICorDebugProcess3::SetEnableCustomNotification – metoda
Povolí nebo zakáže oznámení vlastní ladicí program zadaného typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pClass`  
 [v] Typ, který určuje vlastní ladicí program oznámení.  
  
 `fEnable`  
 [v] `true` povolit vlastní ladicí program oznámení; `false` zakázat oznámení. Výchozí hodnota je `false`.  
  
## <a name="remarks"></a>Poznámky  
 Když `fEnable` je nastaven na `true`, volá, aby se <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> metoda aktivační událost [icordebugmanagedcallback3::customnotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) zpětného volání. Oznámení jsou zakázané ve výchozím nastavení; ladicí program proto musíte zadat všechny typy oznámení, že zná a chce zpracovat. Protože [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) třída má obor doménu aplikace, musí volat ladicího programu `SetEnableCustomNotification` pro každou doménu aplikace v procesu, pokud chcete dostávat oznámení napříč celý proces.  
  
 Od verze [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], jen podporované oznámení je závislost mezi vlákny oznámení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugProcess3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
