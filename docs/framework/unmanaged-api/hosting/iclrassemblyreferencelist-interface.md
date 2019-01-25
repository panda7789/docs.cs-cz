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
ms.openlocfilehash: 1c2b383abdc67546749867de154a00fda244b3ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660018"
---
# <a name="iclrassemblyreferencelist-interface"></a>ICLRAssemblyReferenceList – rozhraní
Spravuje seznam sestavení, která jsou načtena modulem common language runtime (CLR) a není hostitelem.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IsAssemblyReferenceInList – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|Získá hodnotu určující, zda zadaný ukazatel odkazuje na sestavení v seznamu.|  
|[IsStringAssemblyReferenceInList – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|Získá hodnotu určující, zda zadaný název odpovídá názvu sestavení v seznamu.|  
  
## <a name="remarks"></a>Poznámky  
 Volání [iclrassemblyidentitymanager::getclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) metodu k získání ukazatele na instanci `ICLRAssemblyReferenceList`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICLRAssemblyIdentityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [IHostAssemblyStore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
