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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3b8dd67cb7dff4bec5bab192a08461ef13fcbd9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdomainmanager-interface"></a>ICLRDomainManager – rozhraní
Umožňuje na hostiteli a poté zadejte správce domény aplikace, který se použije k chybě při inicializaci výchozí doméně aplikace a k určení inicializační vlastnosti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[SetAppDomainManagerType – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|Určuje typ odvozený z <xref:System.AppDomainManager?displayProperty=nameWithType> třídu aplikace správce domény, který se použije k chybě při inicializaci výchozí doméně aplikace.|  
|[SetPropertiesForDefaultAppDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|Nastaví vlastnosti, které se použijí k chybě při inicializaci výchozí doméně aplikace.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li získat instanci tohoto rozhraní, zavolejte [iclrcontrol::getclrmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metoda s typem manager IID `IID_ICLRDomainManager`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
