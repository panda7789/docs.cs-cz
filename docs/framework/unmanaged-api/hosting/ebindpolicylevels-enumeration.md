---
title: EBindPolicyLevels – výčet
ms.date: 03/30/2017
api_name:
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1da1d368725ab0a2334080c1caa7d4e25f5f3bab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431120"
---
# <a name="ebindpolicylevels-enumeration"></a>EBindPolicyLevels – výčet
Poskytuje příznaky k určení úrovně, kdy má nastavení nebo změna zásad sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|Určuje, že by měl být zásada na úrovni správce.|  
|`ePolicyLevelApp`|Určuje, že by měl být zásada na úrovni aplikace.|  
|`ePolicyLevelHost`|Určuje, že by měl být zásada na úrovni hostitele.|  
|`ePolicyLevelNone`|Určuje příznaky žádné zásady úrovni.|  
|`ePolicyLevelPublisher`|Určuje, že je použita zásada na úrovni vydavatele.|  
|`ePolicyLevelRetargetable`|Určuje, že zásady by měl být použít proměnné na úrovni.|  
|`ePolicyPortability`|Určuje, že zásady by měly podporovat přenositelnost mezi implementací sestavení rozhraní .NET Framework. Najdete v článku [ \<supportPortability – >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) konfigurační soubor prvek.|  
|`ePolicyUnifiedToCLR`|Určuje, že zásady by měl být unified na který common language runtime (CLR).|  
  
## <a name="remarks"></a>Poznámky  
 Tento výčet je předán metody [iclrhostbindingpolicymanager –](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) rozhraní k zadání změny v zásadách aplikací.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRAssemblyIdentityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
