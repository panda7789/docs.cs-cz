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
ms.openlocfilehash: 5e82f542bdc364a52fc558e582134a7d8d554ec3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131148"
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
|`eCurrentContext`|Označuje kontext v aktuálním vlákně v době, kdy modul CLR (Common Language Runtime) volá metodu [IHostSecurityManager:: GetSecurityContext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) , nebo kontext požadovaný modulem CLR ve volání metody [IHostSecurityManager:: SetSecurityContext –. ](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)metoda.|  
|`eRestrictedContext`|Označuje kontext, přes který má hostitel nižší oprávnění, jako je uvolňování paměti nebo konstruktory třídy nebo modulu.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR poskytuje jednu z hodnot `EContextType` jako hodnotu parametru v volání metody `IHostSecurityManager::GetSecurityContext` a `IHostSecurityManager::SetSecurityContext`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IHostSecurityContext – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
