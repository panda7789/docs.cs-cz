---
title: "IGCHost2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost2
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCHost2
helpviewer_keywords: IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c6706696e3fd5158d2b49a4d114d978a26510b67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="igchost2-interface"></a>IGCHost2 – rozhraní
Poskytuje metody pro získání informací o systém kolekce paměti a řízení některých aspektů uvolňování paměti.  
  
> [!NOTE]
>  Pro nový vývoj, doporučujeme použít [iclrgcmanager2 –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) místo toho rozhraní.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Setgcstartuplimitsex – metoda](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|Nastaví velikost segmentu a maximální velikost pro generování 0. Umožňuje 0. generace a velikost segmentu větší než `DWORD`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** GCHost.idl, GCHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Rozhraní hostování CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [Corruntimehost – třída typu Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
