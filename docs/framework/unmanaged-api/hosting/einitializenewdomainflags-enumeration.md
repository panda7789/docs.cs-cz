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
ms.openlocfilehash: 7ff10f84d8d270d31c5d560fb3c9bd3c81cf3e24
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616226"
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
|`eInitializeNewDomainFlags_NoSecurityChanges`|Informuje modul CLR (Common Language Runtime), který hostitel neprovede, aby v metodě provedl změny stavu zabezpečení domény aplikace <xref:System.AppDomainManager.InitializeNewDomain%2A> .|  
  
## <a name="remarks"></a>Poznámky  
 Metoda [ICLRDomainManager:: SetAppDomainManagerType –](iclrdomainmanager-setappdomainmanagertype-method.md) přebírá parametr typu `EInitializeNewDomainFlags` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty hostování](hosting-enumerations.md)
- [SetAppDomainManagerType – metoda](iclrdomainmanager-setappdomainmanagertype-method.md)
