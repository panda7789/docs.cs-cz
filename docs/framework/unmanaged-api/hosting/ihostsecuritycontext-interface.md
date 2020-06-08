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
ms.openlocfilehash: f6e25bfe11880730f6f447ccc0406d716d185624
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501492"
---
# <a name="ihostsecuritycontext-interface"></a>IHostSecurityContext – rozhraní
Umožňuje modulu CLR (Common Language Runtime) zachovat informace o kontextu zabezpečení implementované hostitelem.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[Capture – metoda](ihostsecuritycontext-capture-method.md)|Získá klon `IHostSecurityContext` instance vrácený voláním metody [IHostSecurityManager:: GetSecurityContext –](ihostsecuritymanager-getsecuritycontext-method.md).|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel může řídit veškerý přístup kódu k tokenům vláken jak CLR, tak i uživatelský kód. Může také zajistit, aby byly kompletní informace o kontextu zabezpečení předány přes asynchronní operace nebo body kódu s omezeným přístupem ke kódu. `IHostSecurityContext`Zapouzdřuje tyto informace kontextu zabezpečení, které jsou neprůhledné pro modul runtime. Modul runtime tyto informace zachytí pomocí `Capture` a přesune je mezi pracovními procesy odeslání položky pracovního procesu, provedení finalizační metody a konstruktory modulu a třídy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRHostProtectionManager – rozhraní](iclrhostprotectionmanager-interface.md)
- [IHostSecurityManager – rozhraní](ihostsecuritymanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
