---
title: "ICorPublishProcessEnum – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcessEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcessEnum
helpviewer_keywords: ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 66e31911289d1ef8b590a0b7e7896adfa4998adc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublishprocessenum-interface"></a>ICorPublishProcessEnum – rozhraní
Podtřídou třídy [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) rozhraní, které poskytuje metody k procházení kolekce [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objekty.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|Získá zadaný počet `ICorPublishProcess` instancí z kolekce, počínaje na aktuální pozici.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorPublishProcessEnum` Rozhraní implementuje metody rozhraní abstraktní [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).  
  
 `ICorPublishProcessEnum` Je instance vytvořené [icorpublish::enumprocesses –](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) metoda. Přechod kolekce `ICorPublishProcess` objekty podle kritéria filtru, která je zadána v době `ICorPublishProcessEnum` instance byla vytvořena.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorPub.idl, CorPub.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Corpubpublish – třída typu Coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
