---
title: EHostBindingPolicyModifyFlags – výčet
ms.date: 03/30/2017
api_name:
- EHostBindingPolicyModifyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EHostBindingPolicyModifyFlags
helpviewer_keywords:
- EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type:
- apiref
ms.openlocfilehash: 256c362ae0aea51fea16ce799db243b105dee81a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616239"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a>EHostBindingPolicyModifyFlags – výčet
Umožňuje hostiteli určit typ přesměrování, který modul CLR (Common Language Runtime) by měl provést při použití změn zásad ze zdrojového sestavení na cílové sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|Určuje, že CLR bude řetězit hodnoty zásad zdrojového sestavení do cílových sestavení.|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|Určuje, že modul CLR provede výchozí akci.|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|Určuje, že CLR nastaví hodnoty zásad cílového sestavení na maximální hodnoty.|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|Určuje, že CLR nahradí hodnoty zásad cílového sestavení prvky zdrojového sestavení.|  
  
## <a name="remarks"></a>Poznámky  
 Metoda [ICLRHostBindingPolicyManager:: ModifyApplicationPolicy –](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) přebírá parametr typu `EHostBindingPolicyModifyFlags` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRHostBindingPolicyManager – rozhraní](iclrhostbindingpolicymanager-interface.md)
- [Výčty hostování](hosting-enumerations.md)
