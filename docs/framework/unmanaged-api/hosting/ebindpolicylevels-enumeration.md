---
title: "EBindPolicyLevels – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EBindPolicyLevels
api_location: mscoree.dll
api_type: COM
f1_keywords: EBindPolicyLevels
helpviewer_keywords: EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e55fdb58129cd530bb63f26fab0be471b133d62f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Iclrassemblyidentitymanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [Výčty hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
