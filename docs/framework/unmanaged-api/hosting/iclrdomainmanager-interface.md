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
ms.openlocfilehash: dda243ccbf18f396c1bcc03358997ea0f06c42a8
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615706"
---
# <a name="iclrdomainmanager-interface"></a>ICLRDomainManager – rozhraní
Umožňuje hostiteli zadat správce aplikační domény, který se použije k inicializaci výchozí domény aplikace, a zadat vlastnosti inicializace.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[SetAppDomainManagerType – metoda](iclrdomainmanager-setappdomainmanagertype-method.md)|Určuje typ odvozený od <xref:System.AppDomainManager?displayProperty=nameWithType> třídy správce aplikační domény, který se použije k inicializaci výchozí domény aplikace.|  
|[SetPropertiesForDefaultAppDomain – metoda](iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|Nastaví vlastnosti, které se použijí k inicializaci výchozí domény aplikace.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li získat instanci tohoto rozhraní, zavolejte metodu [ICLRControl:: GetCLRManager –](iclrcontrol-getclrmanager-method.md) s typem správce IID `IID_ICLRDomainManager` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní pro hostování](hosting-interfaces.md)
- [Hostování](index.md)
