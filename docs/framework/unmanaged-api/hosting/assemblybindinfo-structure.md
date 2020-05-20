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
ms.openlocfilehash: 615637813b08629aaea74b23fa2737f52d61bafb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616915"
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
|`dwAppDomainId`|Jedinečný identifikátor `IStream` vrácený voláním [IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md), ze kterého má být načteno odkazované sestavení.|  
|`lpReferencedIdentity`|Jedinečný identifikátor odkazovaného sestavení.|  
|`lpPostPolicyIdentity`|Identifikátor odkazovaného sestavení po použití všech hodnot zásad vazby|  
|`ePolicyLevel`|Jedna z hodnot [EPolicyAction –](epolicyaction-enumeration.md) určujících, které zásady správy verzí (pokud existují) by měly být aplikovány na odkazované sestavení.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel dodá jedinečný identifikátor modulu `dwAppDomainId` CLR (Common Language Runtime). Po volání `IHostAssemblyStore::ProvideAssembly` vrátí modul runtime identifikátor, který určí, zda `IStream` byl obsah namapovaný. V takovém případě modul runtime načte existující kopii místo přemapování datového proudu. Modul runtime používá tento identifikátor také jako vyhledávací klíč pro proudy vracené z volání do [IHostAssemblyStore::P rovidemodule](ihostassemblystore-providemodule-method.md). Proto musí být identifikátor jedinečný pro požadavky na modul a požadavky na sestavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. idl  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Struktury pro hostování](hosting-structures.md)
- [ICLRAssemblyIdentityManager – rozhraní](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList – rozhraní](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager – rozhraní](ihostassemblymanager-interface.md)
- [IHostAssemblyStore – rozhraní](ihostassemblystore-interface.md)
- [ModuleBindInfo – struktura](modulebindinfo-structure.md)
