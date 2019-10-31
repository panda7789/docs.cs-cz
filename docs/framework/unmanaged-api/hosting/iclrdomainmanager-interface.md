---
title: ICLRDomainManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager
helpviewer_keywords:
- ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
ms.openlocfilehash: aa874205cf14232e7a69ed2215086e33c0beab4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129345"
---
# <a name="iclrdomainmanager-interface"></a>ICLRDomainManager – rozhraní
Umožňuje hostiteli zadat správce aplikační domény, který se použije k inicializaci výchozí domény aplikace, a zadat vlastnosti inicializace.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[SetAppDomainManagerType – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|Určuje typ odvozený od <xref:System.AppDomainManager?displayProperty=nameWithType> třídy správce aplikační domény, který se použije k inicializaci výchozí domény aplikace.|  
|[SetPropertiesForDefaultAppDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|Nastaví vlastnosti, které se použijí k inicializaci výchozí domény aplikace.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li získat instanci tohoto rozhraní, zavolejte metodu [ICLRControl:: GetCLRManager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) s typem správce IID `IID_ICLRDomainManager`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
