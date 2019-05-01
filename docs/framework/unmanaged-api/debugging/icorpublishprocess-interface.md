---
title: ICorPublishProcess – rozhraní
ms.date: 03/30/2017
api_name:
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08dfa3ddbfd9cffdb0cb88d0325e5703a854668a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993509"
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess – rozhraní
Poskytuje metody, které přistupují k zobrazit informace o procesu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumAppDomains – metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|Získá [icorpublishappdomainenum –](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance, která obsahuje domény aplikace v procesu odkazovaná tímto objektem `ICorPublishProcess`.|  
|[GetDisplayName – metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|Získá úplnou cestu ke spustitelnému souboru pro proces odkazuje toto `ICorPublishProcess`.|  
|[GetProcessID – metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|Získá identifikátor operačního systému pro proces odkazuje toto `ICorPublishProcess`.|  
|[IsManaged – metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|Získá hodnotu určující, zda proces odkazuje toto `ICorPublishProcess` známé spouštět spravovaný kód.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorPub.idl, CorPub.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [CorpubPublish – třída typu coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
