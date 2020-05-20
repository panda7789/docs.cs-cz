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
ms.openlocfilehash: 94d2ec12309249afbecdc4130f8fe20c927b0a9b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616369"
---
# <a name="ebindpolicylevels-enumeration"></a>EBindPolicyLevels – výčet
Poskytuje příznaky pro určení úrovně, na které se má použít nebo upravit zásady sestavení.  
  
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
|`ePolicyLevelAdmin`|Určuje, že zásada by se měla použít na úrovni správce.|  
|`ePolicyLevelApp`|Určuje, že zásada by se měla použít na úrovni aplikace.|  
|`ePolicyLevelHost`|Určuje, že zásada by se měla použít na úrovni hostitele.|  
|`ePolicyLevelNone`|Neurčuje žádné příznaky na úrovni zásad.|  
|`ePolicyLevelPublisher`|Určuje, že zásada by se měla použít na úrovni vydavatele.|  
|`ePolicyLevelRetargetable`|Určuje, že zásada by se měla použít na proměnlivých úrovních.|  
|`ePolicyPortability`|Určuje, že zásady by měly podporovat přenositelnost mezi implementacemi .NET Framework sestavení. Viz prvek [ \< značka supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) konfiguračního souboru.|  
|`ePolicyUnifiedToCLR`|Určuje, že zásady by měly být sjednoceny s modulem CLR (Common Language Runtime).|  
  
## <a name="remarks"></a>Poznámky  
 Tento výčet je předán metodám rozhraní [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) k určení změn v zásadách použití.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRAssemblyIdentityManager – rozhraní](iclrassemblyidentitymanager-interface.md)
- [Výčty hostování](hosting-enumerations.md)
