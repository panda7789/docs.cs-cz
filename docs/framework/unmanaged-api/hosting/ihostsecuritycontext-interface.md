---
title: IHostSecurityContext – rozhraní
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
ms.openlocfilehash: 993d16818b25dfefe1f53c7afd06bc9857d9eb24
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121524"
---
# <a name="ihostsecuritycontext-interface"></a>IHostSecurityContext – rozhraní
Umožňuje modulu CLR (Common Language Runtime) zachovat informace o kontextu zabezpečení implementované hostitelem.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Capture – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|Získá klon instance `IHostSecurityContext` vrácenou voláním metody [IHostSecurityManager:: GetSecurityContext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel může řídit veškerý přístup kódu k tokenům vláken jak CLR, tak i uživatelský kód. Může také zajistit, aby byly kompletní informace o kontextu zabezpečení předány přes asynchronní operace nebo body kódu s omezeným přístupem ke kódu. `IHostSecurityContext` zapouzdřuje tyto informace kontextu zabezpečení, které jsou neprůhledné pro modul runtime. Modul runtime zachytí tyto informace pomocí `Capture`a přesune je mezi procesy odeslání položky pracovního procesu, provedení finalizační metody a konstruktory modulu a třídy pracovních procesů.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRHostProtectionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [IHostSecurityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
