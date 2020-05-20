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
ms.openlocfilehash: 657d2d638a419ba88d4cf7152f4505de1bd23706
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421069"
---
# <a name="icorpublishprocessenum-interface"></a>ICorPublishProcessEnum – rozhraní
Podtřída rozhraní [ICorPublishEnum](icorpublishenum-interface.md) , která poskytuje metody pro procházení kolekce objektů [ICorPublishProcess](icorpublishprocess-interface.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next – metoda](icorpublishprocessenum-next-method.md)|Načte zadaný počet `ICorPublishProcess` instancí z kolekce počínaje aktuální pozicí.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorPublishProcessEnum`Rozhraní implementuje metody abstraktního rozhraní [ICorPublishEnum](icorpublishenum-interface.md).  
  
 `ICorPublishProcessEnum`Instance je vytvořena metodou [ICorPublish –:: EnumProcesses –](icorpublish-enumprocesses-method.md) . Průchod kolekce `ICorPublishProcess` objektů je založen na kritériích filtru uvedených v době, kdy `ICorPublishProcessEnum` byla vytvořena instance.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorPub. idl, CorPub. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [CorpubPublish – třída typu coclass](corpubpublish-coclass.md)
