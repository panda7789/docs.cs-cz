---
title: ICorPublish – rozhraní
ms.date: 03/30/2017
api_name:
- ICorPublish
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish
helpviewer_keywords:
- ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type:
- apiref
ms.openlocfilehash: c4a24d879ebd9e8813ea0ac4597818569f4ae6fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790729"
---
# <a name="icorpublish-interface"></a>ICorPublish – rozhraní
Slouží jako obecné rozhraní pro publikování informací o procesech a informacích o doménách aplikace v těchto procesech.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumProcesses – metoda](icorpublish-enumprocesses-method.md)|Získá instanci [ICorPublishProcessEnum –](icorpublishprocessenum-interface.md) , která obsahuje spravované procesy spuštěné v tomto počítači.|  
|[GetProcess – metoda](icorpublish-getprocess-method.md)|Získá instanci [ICorPublishProcess](icorpublishprocess-interface.md) , která představuje proces se zadaným identifikátorem.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorPub. idl, CorPub. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
- [CorpubPublish – třída typu coclass](corpubpublish-coclass.md)
