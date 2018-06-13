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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3536184fa7798ac8eabe851221ec692c126460b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424011"
---
# <a name="icorpublishenum-interface"></a>ICorPublishEnum – rozhraní
Slouží jako abstraktní základní rozhraní pro výčty, které se používají v publikování informací o procesy a aplikační domény.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Clone – metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|Vytvoří kopii tohoto `ICorPublishEnum` objektu.|  
|[GetCount – metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|Získá počet položek ve výčtu.|  
|[Reset – metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|Posune kurzor z na začátek výčtu.|  
|[Skip – metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|Přesune kurzor dál o zadaný počet položek ve výčtu.|  
  
## <a name="remarks"></a>Poznámky  
 Následující výčty odvozena od `ICorPublishEnum`:  
  
-   [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
-   [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorPub.idl, CorPub.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [CorpubPublish – třída typu coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
