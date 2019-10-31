---
title: AssemblyBindInfo – struktura
ms.date: 03/30/2017
api_name:
- AssemblyBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyBindInfo
helpviewer_keywords:
- AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type:
- apiref
ms.openlocfilehash: 8764a3d665c997460419561eb168f92ca769c30c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192115"
---
# <a name="assemblybindinfo-structure"></a>AssemblyBindInfo – struktura
Poskytuje podrobné informace o odkazovaném sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`dwAppDomainId`|Jedinečný identifikátor `IStream` vrácen voláním [IHostAssemblyStore::P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), ze kterého má být načteno odkazované sestavení.|  
|`lpReferencedIdentity`|Jedinečný identifikátor odkazovaného sestavení.|  
|`lpPostPolicyIdentity`|Identifikátor odkazovaného sestavení po použití všech hodnot zásad vazby|  
|`ePolicyLevel`|Jedna z hodnot [EPolicyAction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) určujících, které zásady správy verzí (pokud existují) by měly být aplikovány na odkazované sestavení.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel dodá jedinečný identifikátor `dwAppDomainId` modulu CLR (Common Language Runtime). Po volání funkce `IHostAssemblyStore::ProvideAssembly` vrátí modul runtime identifikátor k určení, zda byl obsah `IStream` namapován. V takovém případě modul runtime načte existující kopii místo přemapování datového proudu. Modul runtime používá tento identifikátor také jako vyhledávací klíč pro proudy vracené z volání do [IHostAssemblyStore::P rovidemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md). Proto musí být identifikátor jedinečný pro požadavky na modul a požadavky na sestavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. idl  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [ICLRAssemblyIdentityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [ModuleBindInfo – struktura](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
