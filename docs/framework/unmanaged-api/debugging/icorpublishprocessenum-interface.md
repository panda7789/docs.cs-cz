---
title: ICorPublishProcessEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd71a2bd4a52da8fa77592363e2eb7c8f5101fd3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [CorpubPublish – třída typu coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
