---
title: ICLRAssemblyIdentityManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager
helpviewer_keywords:
- ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3a58a9ec4ed9514e748ed6c8c21a404feed9560
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="iclrassemblyidentitymanager-interface"></a>ICLRAssemblyIdentityManager – rozhraní
Poskytuje metody, které podporují komunikaci mezi hostitelem a common language runtime (CLR) o sestavení.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetBindingIdentityFromFile – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|Získá identitu sestavení vazba dat pro sestavení v zadaná cesta k souboru.|  
|[GetBindingIdentityFromStream – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|Získá data identit kanonický sestavení pro sestavení v zadaného datového proudu.|  
|[GetCLRAssemblyReferenceList – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|Získá [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instanci ze seznamu zadaný částečného sestavení identit.|  
|[GetProbingAssembliesFromReference – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|Získá [iclrprobingassemblyenum –](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerátor pro identity sestavení odkazuje sestavení se zadanou identitou.|  
|[GetReferencedAssembliesFromFile – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|Získá [iclrreferenceassemblyenum –](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instanci, která obsahuje seznam sestavení odkazuje sestavení v zadaná cesta k souboru.|  
|[GetReferencedAssembliesFromStream – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|Získá odkazy `ICLRReferenceAssemblyEnum` objekt, který obsahuje data identit sestavení pro sestavení odkazuje sestavení v zadaného datového proudu.|  
|[IsStronglyNamed – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|Získá hodnotu, která určuje, zda zadané sestavení silným názvem.|  
  
## <a name="remarks"></a>Poznámky  
 Použití `ICLRAssemblyIdentityManager` získat instancí `ICLRAssemblyReferenceList` a chcete získat výčet identit sestavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRAssemblyReferenceList – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [ICLRProbingAssemblyEnum – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
