---
title: "EInitializeNewDomainFlags – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EInitializeNewDomainFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: EInitializeNewDomainFlags
helpviewer_keywords: EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa5c9aa050e0f5e634c43080d9caa5011a126529
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="einitializenewdomainflags-enumeration"></a>EInitializeNewDomainFlags – výčet
Umožňuje hostitele modulu runtime poskytnout informace o inicializaci domény aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|Žádné příznaky.|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|Modul CLR (CLR) informuje, že hostitel nebude provádět změny stavu zabezpečení v doméně aplikace <xref:System.AppDomainManager.InitializeNewDomain%2A> metoda.|  
  
## <a name="remarks"></a>Poznámky  
 [Iclrdomainmanager::setappdomainmanagertype –](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) metoda přebírá parametr typu `EInitializeNewDomainFlags`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [SetAppDomainManagerType – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
