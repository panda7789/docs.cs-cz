---
title: "ICorDebug::Terminate – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebug.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e416f8ea20bde49a1c1cdb5d61bc4a6bfbce7913
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugterminate-method"></a>ICorDebug::Terminate – metoda
Ukončí `ICorDebug` objektu.  
  
> [!NOTE]
>  `Terminate`nelze volat až [icordebugmanagedcallback::exitprocess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) zpětného volání byla přijata pro všechny procesy laděné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a>Poznámky  
 `Terminate`musí být voláno, když `ICorDebug` objekt již není potřeba.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
