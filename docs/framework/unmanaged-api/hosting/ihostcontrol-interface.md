---
title: IHostControl – rozhraní
ms.date: 03/30/2017
api_name:
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
ms.openlocfilehash: 9dd89abb332853b966aa81dc506099b7af6ca3b2
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804937"
---
# <a name="ihostcontrol-interface"></a>IHostControl – rozhraní
Poskytuje metody pro konfiguraci načítání sestavení a pro určení, která hostující rozhraní hostitel podporuje.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetHostManager – metoda](ihostcontrol-gethostmanager-method.md)|Získá ukazatel rozhraní na implementaci rozhraní se zadaným hostitelem `IID` .|  
|[SetAppDomainManager – metoda](ihostcontrol-setappdomainmanager-method.md)|Upozorňuje hostitele, že byla vytvořena doména aplikace.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.AppDomainManager>
- [ICLRRuntimeHost – rozhraní](iclrruntimehost-interface.md)
- [ICLRControl – rozhraní](iclrcontrol-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
