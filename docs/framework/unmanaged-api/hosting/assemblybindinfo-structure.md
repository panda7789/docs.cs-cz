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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce79987c7fcf45b8d10dcc4613e053ee735941de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946823"
---
# <a name="assemblybindinfo-structure"></a>AssemblyBindInfo – struktura
Poskytuje podrobné informace o odkazovaném sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`dwAppDomainId`|Jedinečný identifikátor `IStream` vrácený voláním [ihostassemblystore::provideassembly –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), ze které má odkazované sestavení má být načten.|  
|`lpReferencedIdentity`|Jedinečný identifikátor odkazovaného sestavení.|  
|`lpPostPolicyIdentity`|Identifikátor odkazovaného sestavení po použití hodnoty zásad žádné vazby.|  
|`ePolicyLevel`|Jeden z [epolicyaction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, které označují, které zásady správy verzí, pokud existuje, bude použito k odkazovanému sestavení.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel poskytuje jedinečný identifikátor `dwAppDomainId` do common language runtime (CLR). Po volání `IHostAssemblyStore::ProvideAssembly` vrátí, modul runtime používá identifikátoru k určení, zda obsah `IStream` nebyly namapovány. Pokud ano, načte modul runtime stávající kopie spíše než přemapování datového proudu. Modul runtime také používá tento identifikátor jako vyhledávací klíč pro datové proudy vrácené z volání [ihostassemblystore::providemodule –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md). Proto musí být identifikátor jedinečný modul požadavky a požadavky na sestavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.idl  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [ICLRAssemblyIdentityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [ModuleBindInfo – struktura](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
