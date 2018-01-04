---
title: "IHostSecurityContext – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityContext
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityContext
helpviewer_keywords: IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ee464e47ad6e333b507c199e1857309f640a37b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritycontext-interface"></a>IHostSecurityContext – rozhraní
Umožňuje modul CLR (CLR) k udržování informace kontextu zabezpečení implementované hostitele.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Capture – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|Získá klon `IHostSecurityContext` instance vrácená z volání [ihostsecuritymanager::getsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel můžou řídit všechny kódu přístup k vlákno tokeny kódem CLR i uživateli. Ho můžete také zajistit, že dokončení zabezpečení informace o kontextu je předán přes asynchronních operací nebo body kódu s přístupem kód s omezeným přístupem. `IHostSecurityContext`zapouzdří tato informace kontextu zabezpečení, která je plné krytí modulu runtime. Modul runtime zaznamená tato informace pomocí `Capture`, a přesouvá ji napříč vlákno fondu pracovní položka odesílání, provádění finalizační metodu a modul a třída konstruktory.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRHostProtectionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [IHostSecurityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
