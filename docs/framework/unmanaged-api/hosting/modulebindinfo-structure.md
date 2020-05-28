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
ms.openlocfilehash: 31be0525c637e50c1161129277d651b56dadfaa3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006750"
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
  
|Člen|Description|  
|------------|-----------------|  
|`dwAppDomainId`|Jedinečný identifikátor `IStream` , který je vrácen voláním metody [IHostAssemblyStore::P rovidemodule](ihostassemblystore-providemodule-method.md) , ze které má být načten odkazovaný modul.|  
|`lpAssemblyIdentity`|Jedinečný identifikátor pro sestavení, které obsahuje odkazovaný modul.|  
|`lpModuleName`|Název odkazovaného modulu|  
  
## <a name="remarks"></a>Poznámky  
 `ModuleBindInfo`je předán jako parametr do `IHostAssemblyStore::ProvideModule` . Hostitel dodá jedinečný identifikátor modulu `dwAppDomainId` CLR (Common Language Runtime). Po volání metody [IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md) , modul runtime používá identifikátor k určení, zda `IStream` byl obsah namapovaný. V takovém případě modul runtime načte existující kopii místo přemapování datového proudu. Modul runtime používá tento identifikátor také jako vyhledávací klíč pro datové proudy, které jsou vráceny z volání `IHostAssemblyStore::ProvideAssembly` metody. Proto musí být identifikátor jedinečný pro požadavky modulů i pro požadavky na sestavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. idl  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Struktury pro hostování](hosting-structures.md)
- [AssemblyBindInfo – struktura](assemblybindinfo-structure.md)
- [ICLRAssemblyIdentityManager – rozhraní](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList – rozhraní](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager – rozhraní](ihostassemblymanager-interface.md)
