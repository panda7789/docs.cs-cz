---
title: ICorPublishAppDomainEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum
helpviewer_keywords:
- ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type:
- apiref
ms.openlocfilehash: a48e20413f466e25a9145e9dbf1ba93d90155770
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397030"
---
# <a name="icorpublishappdomainenum-interface"></a>ICorPublishAppDomainEnum – rozhraní
Podtřída rozhraní [ICorPublishEnum](icorpublishenum-interface.md) , která poskytuje metody pro procházení kolekce objektů [ICorPublishAppDomain](icorpublishappdomain-interface.md) , které aktuálně existují v rámci procesu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next – metoda](icorpublishappdomainenum-next-method.md)|Načte zadaný počet `ICorPublishAppDomain` instancí z kolekce počínaje aktuální pozicí.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorPublishAppDomainEnum`Rozhraní implementuje metody abstraktního rozhraní [ICorPublishEnum](icorpublishenum-interface.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorPub. idl, CorPub. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [CorpubPublish – třída typu coclass](corpubpublish-coclass.md)
