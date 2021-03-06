---
title: ICorPublishEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
ms.openlocfilehash: acbc37d0f49af21c60ff6989932c5d341673512b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421173"
---
# <a name="icorpublishenum-interface"></a>ICorPublishEnum – rozhraní
Slouží jako abstraktní základní rozhraní pro enumerátory používané při publikování informací o procesech a doménách aplikace.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Clone – metoda](icorpublishenum-clone-method.md)|Vytvoří kopii tohoto `ICorPublishEnum` objektu.|  
|[GetCount – metoda](icorpublishenum-getcount-method.md)|Získá počet položek ve výčtu.|  
|[Reset – metoda](icorpublishenum-reset-method.md)|Přesune kurzor na začátek výčtu.|  
|[Skip – metoda](icorpublishenum-skip-method.md)|Přesune kurzor do výčtu směrem nahoru podle zadaného počtu položek.|  
  
## <a name="remarks"></a>Poznámky  
 Následující enumerátory jsou odvozeny z `ICorPublishEnum` :  
  
- [ICorPublishAppDomainEnum –](icorpublishappdomainenum-interface.md)  
  
- [ICorPublishProcessEnum –](icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorPub. idl, CorPub. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [CorpubPublish – třída typu coclass](corpubpublish-coclass.md)
- [Debugging – rozhraní](debugging-interfaces.md)
