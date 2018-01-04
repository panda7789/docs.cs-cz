---
title: "ICorPublish – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublish
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublish
helpviewer_keywords: ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7769d26d65a97ea8d1b109e0098eae7e7d51ed10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublish-interface"></a>ICorPublish – rozhraní
Slouží jako obecné rozhraní pro publikování informací o procesech a informace o doménách aplikace v těchto procesů.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumProcesses – metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|Získá [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instanci, která obsahuje spravované procesy v tomto počítači spuštěna.|  
|[GetProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|Získá [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instanci, která představuje proces se zadaným identifikátorem.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorPub.idl, CorPub.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [CorpubPublish – třída typu coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
