---
title: EInitializeNewDomainFlags – výčet
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
ms.openlocfilehash: 3693285e13d0650f7662e2187471027cc4c40704
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129420"
---
# <a name="einitializenewdomainflags-enumeration"></a>EInitializeNewDomainFlags – výčet
Povolí hostiteli poskytovat modul runtime s informacemi o inicializaci domény aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|Žádné příznaky.|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|Informuje modul CLR (Common Language Runtime), který hostitel neprovede, aby v metodě <xref:System.AppDomainManager.InitializeNewDomain%2A> provedl změny stavu zabezpečení domény aplikace.|  
  
## <a name="remarks"></a>Poznámky  
 Metoda [ICLRDomainManager:: SetAppDomainManagerType –](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) přebírá parametr typu `EInitializeNewDomainFlags`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [SetAppDomainManagerType – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
