---
title: ICLRAssemblyReferenceList – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 388b26a5559435ea57300751987d14bc5cb9d50c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435294"
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
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRAssemblyIdentityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [IHostAssemblyStore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
