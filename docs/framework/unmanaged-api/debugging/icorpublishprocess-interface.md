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
ms.openlocfilehash: 8d958e949612b502ab218f5c6b75779174d34e19
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421082"
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess – rozhraní
Poskytuje metody, které mají přístup k informacím, které se mají zobrazit o procesu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumAppDomains – metoda](icorpublishprocess-enumappdomains-method.md)|Získá instanci [ICorPublishAppDomainEnum –](icorpublishappdomainenum-interface.md) , která obsahuje domény aplikace v procesu, na který odkazuje `ICorPublishProcess` .|  
|[GetDisplayName – metoda](icorpublishprocess-getdisplayname-method.md)|Získá úplnou cestu ke spustitelnému souboru pro proces, na který odkazuje `ICorPublishProcess` .|  
|[GetProcessID – metoda](icorpublishprocess-getprocessid-method.md)|Načte identifikátor operačního systému pro proces, na který odkazuje tento `ICorPublishProcess` .|  
|[IsManaged – metoda](icorpublishprocess-ismanaged-method.md)|Získá hodnotu, která označuje, zda je známý proces, na který odkazuje tento `ICorPublishProcess` spravovaný kód.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorPub. idl, CorPub. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [CorpubPublish – třída typu coclass](corpubpublish-coclass.md)
