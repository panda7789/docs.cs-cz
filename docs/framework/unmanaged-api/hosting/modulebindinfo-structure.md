---
title: ModuleBindInfo – struktura
ms.date: 03/30/2017
api_name:
- ModuleBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ModuleBindInfo
helpviewer_keywords:
- ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f14d3dcaad1cc8cac11599b1647d61df3a793301
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124446"
---
# <a name="modulebindinfo-structure"></a>ModuleBindInfo – struktura
Poskytuje podrobné informace o odkazovaného modulu a sestavení, který jej obsahuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`dwAppDomainId`|Jedinečný identifikátor `IStream` , který je vrácen voláním [ihostassemblystore::providemodule –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) metoda, ze kterého má být načten odkazovaného modulu.|  
|`lpAssemblyIdentity`|Jedinečný identifikátor pro sestavení, které obsahuje odkazovaného modulu.|  
|`lpModuleName`|Název odkazovaného modulu.|  
  
## <a name="remarks"></a>Poznámky  
 `ModuleBindInfo` je předán jako parametr `IHostAssemblyStore::ProvideModule`. Hostitel poskytuje jedinečný identifikátor `dwAppDomainId` do common language runtime (CLR). Po volání [ihostassemblystore::provideassembly –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) metoda vrací výsledek, modul runtime používá identifikátoru k určení, zda obsah `IStream` byly namapovány. Pokud ano, načte modul runtime stávající kopie spíše než přemapování datového proudu. Modul runtime také používá tento identifikátor jako vyhledávací klíč pro datové proudy, které jsou vráceny z volání `IHostAssemblyStore::ProvideAssembly` metody. Proto identifikátoru musí být jedinečný pro modul požadavky i jako u žádosti o sestavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.idl  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [AssemblyBindInfo – struktura](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [ICLRAssemblyIdentityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
