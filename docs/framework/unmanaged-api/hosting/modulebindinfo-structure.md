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
ms.openlocfilehash: ae40d8adaae70ccff6e8058858a506267d58873f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133751"
---
# <a name="modulebindinfo-structure"></a>ModuleBindInfo – struktura
Obsahuje podrobné informace o odkazovaném modulu a sestavení, které ho obsahuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`dwAppDomainId`|Jedinečný identifikátor pro `IStream`, který je vrácen voláním metody [IHostAssemblyStore::P rovidemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) , ze které má být načten odkazovaný modul.|  
|`lpAssemblyIdentity`|Jedinečný identifikátor pro sestavení, které obsahuje odkazovaný modul.|  
|`lpModuleName`|Název odkazovaného modulu|  
  
## <a name="remarks"></a>Poznámky  
 `ModuleBindInfo` se předává jako parametr pro `IHostAssemblyStore::ProvideModule`. Hostitel dodá jedinečný identifikátor `dwAppDomainId` modulu CLR (Common Language Runtime). Po volání metody [IHostAssemblyStore::P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) , modul runtime používá identifikátor k určení, zda byl obsah `IStream` namapován. V takovém případě modul runtime načte existující kopii místo přemapování datového proudu. Modul runtime používá tento identifikátor také jako vyhledávací klíč pro datové proudy, které jsou vráceny z volání metody `IHostAssemblyStore::ProvideAssembly`. Proto musí být identifikátor jedinečný pro požadavky modulů i pro požadavky na sestavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. idl  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [AssemblyBindInfo – struktura](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [ICLRAssemblyIdentityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
