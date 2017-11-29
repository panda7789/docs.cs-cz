---
title: "ICLRHostProtectionManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostProtectionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostProtectionManager
helpviewer_keywords: ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c88279eb26b819adaaaf86dcf59105c6ac728017
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrhostprotectionmanager-interface"></a>ICLRHostProtectionManager – rozhraní
Umožňuje hostiteli blokovat konkrétní spravované třídy, metody, vlastnosti a pole ve spuštění v částečně důvěryhodným kódem.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Seteagerserializegrantsets –](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|Poskytuje záruku, že se nikdy vynoří určité výjimečných časování, které mohou způsobit závažné common language runtime (CLR) chyby.|  
|[Setprotectedcategories – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|Určuje kategorie spravované typy a členy, kteří mají blokovat spuštění v částečně důvěryhodným kódem.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [EApiCategories – výčet](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 [Iclrcontrol – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
