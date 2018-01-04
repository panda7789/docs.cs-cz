---
title: "ICLRAssemblyReferenceList – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyReferenceList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyReferenceList
helpviewer_keywords: ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eeef0e7f825f4a6ad907d6b17b92afe1807bad12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyreferencelist-interface"></a>ICLRAssemblyReferenceList – rozhraní
Spravuje seznam sestavení, která jsou načtena common language runtime (CLR) a ne hostitele.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IsAssemblyReferenceInList – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|Získá hodnotu, která určuje, zda je zadaný ukazatel odkazuje na sestavení v seznamu.|  
|[IsStringAssemblyReferenceInList – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|Získá hodnotu, která určuje, zda zadaný název odpovídá názvu sestavení v seznamu.|  
  
## <a name="remarks"></a>Poznámky  
 Volání [iclrassemblyidentitymanager::getclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) metodu za účelem získání ukazatele na instanci `ICLRAssemblyReferenceList`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRAssemblyIdentityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [IHostAssemblyStore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
