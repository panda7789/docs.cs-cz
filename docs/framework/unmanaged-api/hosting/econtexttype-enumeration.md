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
ms.openlocfilehash: b93b27957cc715a5b4718dd9ef61cd11f4a39914
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493384"
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
  
|Člen|Description|  
|------------|-----------------|  
|`eCurrentContext`|Určuje kontext v aktuálním vlákně v době, kdy modul CLR (Common Language Runtime) volá metodu [IHostSecurityManager:: GetSecurityContext –](ihostsecuritymanager-getsecuritycontext-method.md) , nebo kontext požadovaný modulem CLR ve volání metody [IHostSecurityManager:: SetSecurityContext –](ihostsecuritymanager-setsecuritycontext-method.md) .|  
|`eRestrictedContext`|Označuje kontext, přes který má hostitel nižší oprávnění, jako je uvolňování paměti nebo konstruktory třídy nebo modulu.|  
  
## <a name="remarks"></a>Poznámky  
 CLR poskytuje jednu z `EContextType` hodnot jako hodnotu parametru v volání `IHostSecurityManager::GetSecurityContext` `IHostSecurityManager::SetSecurityContext` metod a.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IHostSecurityContext – rozhraní](ihostsecuritycontext-interface.md)
- [IHostSecurityManager – rozhraní](ihostsecuritymanager-interface.md)
- [Výčty hostování](hosting-enumerations.md)
