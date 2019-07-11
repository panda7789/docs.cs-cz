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
ms.openlocfilehash: e61acbb15844c5ddfc8b7aa98c41bb18c6e9ade5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769756"
---
# <a name="ebindpolicylevels-enumeration"></a>EBindPolicyLevels – výčet
Poskytuje příznaků, které určují úroveň, kde nastavení nebo změna zásady sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|`ePolicyLevelAdmin`|Určuje, že je použita zásada na úrovni správce.|  
|`ePolicyLevelApp`|Určuje, že je použita zásada na úrovni aplikace.|  
|`ePolicyLevelHost`|Určuje, že je použita zásada na úrovni hostitele.|  
|`ePolicyLevelNone`|Určuje příznaky žádná úroveň zásad.|  
|`ePolicyLevelPublisher`|Určuje, že je použita zásada na úrovni vydavatele.|  
|`ePolicyLevelRetargetable`|Určuje, že zásada by měla být použít proměnné na úrovni.|  
|`ePolicyPortability`|Určuje, že zásady by měly podporovat přenositelnost mezi implementacemi sestavení rozhraní .NET Framework. Zobrazit [ \<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) prvek souboru konfigurace.|  
|`ePolicyUnifiedToCLR`|Určuje, že zásady by měl unified, který modulu common language runtime (CLR).|  
  
## <a name="remarks"></a>Poznámky  
 Tento výčet je předán do metody [iclrhostbindingpolicymanager –](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) rozhraní a zadejte změny v zásadách aplikací.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRAssemblyIdentityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
