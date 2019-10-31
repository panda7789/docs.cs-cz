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
ms.openlocfilehash: 26de2ebf1364981d8b8f1fb38c8fa1045191114f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126629"
---
# <a name="iclrassemblyidentitymanager-interface"></a>ICLRAssemblyIdentityManager – rozhraní
Poskytuje metody, které podporují komunikaci mezi hostitelem a modulem CLR (Common Language Runtime) o sestaveních.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetBindingIdentityFromFile – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|Získá datovou vazbu identity sestavení pro sestavení v zadané cestě k souboru.|  
|[GetBindingIdentityFromStream – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|Získá kanonická data identity sestavení pro sestavení v zadaném datovém proudu.|  
|[GetCLRAssemblyReferenceList – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|Načte instanci [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) ze zadaného seznamu částečných identit sestavení.|  
|[GetProbingAssembliesFromReference – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|Získá enumerátor [ICLRProbingAssemblyEnum –](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) pro identity sestavení odkazované sestavením se zadanou identitou.|  
|[GetReferencedAssembliesFromFile – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|Získá instanci [ICLRReferenceAssemblyEnum –](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) , která obsahuje seznam sestavení, na která odkazuje sestavení v zadané cestě k souboru.|  
|[GetReferencedAssembliesFromStream – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|Získá ukazatel na objekt `ICLRReferenceAssemblyEnum`, který obsahuje data identity sestavení pro sestavení, na která odkazuje sestavení v zadaném datovém proudu.|  
|[IsStronglyNamed – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|Získá hodnotu, která označuje, zda je zadané sestavení silně pojmenované.|  
  
## <a name="remarks"></a>Poznámky  
 Pomocí `ICLRAssemblyIdentityManager` získat instance `ICLRAssemblyReferenceList` a vytvořit výčet identit sestavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRAssemblyReferenceList – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [ICLRProbingAssemblyEnum – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
