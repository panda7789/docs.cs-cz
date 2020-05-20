---
title: EContextType – výčet
ms.date: 03/30/2017
api_name:
- EContextType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EContextType
helpviewer_keywords:
- EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type:
- apiref
ms.openlocfilehash: ceb68410e808bf7843149e3f05a39c7a98d0c000
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616291"
---
# <a name="econtexttype-enumeration"></a>EContextType – výčet
Popisuje kontext zabezpečení aktuálně zpracovávaného vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`eCurrentContext`|Určuje kontext v aktuálním vlákně v době, kdy modul CLR (Common Language Runtime) volá metodu [IHostSecurityManager:: GetSecurityContext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) , nebo kontext požadovaný modulem CLR ve volání metody [IHostSecurityManager:: SetSecurityContext –](ihostsecuritymanager-setsecuritycontext-method.md) .|  
|`eRestrictedContext`|Označuje kontext, přes který má hostitel nižší oprávnění, jako je uvolňování paměti nebo konstruktory třídy nebo modulu.|  
  
## <a name="remarks"></a>Poznámky  
 CLR poskytuje jednu z `EContextType` hodnot jako hodnotu parametru v volání `IHostSecurityManager::GetSecurityContext` `IHostSecurityManager::SetSecurityContext` metod a.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IHostSecurityContext – rozhraní](ihostsecuritycontext-interface.md)
- [IHostSecurityManager – rozhraní](ihostsecuritymanager-interface.md)
- [Výčty hostování](hosting-enumerations.md)
