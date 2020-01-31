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
ms.openlocfilehash: 3ae48df9e66890161c1aef944d37b0a279939d56
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790545"
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess – rozhraní
Poskytuje metody, které mají přístup k informacím, které se mají zobrazit o procesu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumAppDomains – metoda](icorpublishprocess-enumappdomains-method.md)|Získá instanci [ICorPublishAppDomainEnum –](icorpublishappdomainenum-interface.md) , která obsahuje domény aplikace v procesu, na který odkazuje tento `ICorPublishProcess`.|  
|[GetDisplayName – metoda](icorpublishprocess-getdisplayname-method.md)|Získá úplnou cestu ke spustitelnému souboru pro proces, na který odkazuje tento `ICorPublishProcess`.|  
|[GetProcessID – metoda](icorpublishprocess-getprocessid-method.md)|Získá identifikátor operačního systému pro proces, na který odkazuje tento `ICorPublishProcess`.|  
|[IsManaged – metoda](icorpublishprocess-ismanaged-method.md)|Získá hodnotu, která označuje, zda je v procesu odkazovaném tímto `ICorPublishProcess` spuštěn spravovaný kód.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorPub. idl, CorPub. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
- [CorpubPublish – třída typu coclass](corpubpublish-coclass.md)
