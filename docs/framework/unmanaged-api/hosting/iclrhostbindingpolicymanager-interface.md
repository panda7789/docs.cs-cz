---
title: ICLRHostBindingPolicyManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager
helpviewer_keywords:
- ICLRHostBindingPolicyManager interface [.NET Framework hosting]
ms.assetid: f9da168b-366b-4b2b-bdb9-330b6bad5a6b
topic_type:
- apiref
ms.openlocfilehash: 3cf2a945607bf85a51dbec35342ff5ac46878bca
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703566"
---
# <a name="iclrhostbindingpolicymanager-interface"></a>ICLRHostBindingPolicyManager – rozhraní
Poskytuje metody pro hostitele k vyhodnocení aktuálních zásad vazby a oznamování změn zásad pro zadané sestavení.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EvaluatePolicy – metoda](iclrhostbindingpolicymanager-evaluatepolicy-method.md)|Vyhodnotí zásady vytváření vazeb jménem hostitele.|  
|[ModifyApplicationPolicy – metoda](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|Upraví zásadu vazby pro zadané sestavení a vytvoří novou verzi zásad.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRAssemblyIdentityManager – rozhraní](iclrassemblyidentitymanager-interface.md)
- [IHostAssemblyStore – rozhraní](ihostassemblystore-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
