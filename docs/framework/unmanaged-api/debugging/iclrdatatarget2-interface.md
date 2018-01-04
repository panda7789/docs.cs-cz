---
title: "ICLRDataTarget2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget2
helpviewer_keywords: ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8d8dc7aad35e38b2f9d3b5fb48dacbe1d22bd34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget2-interface"></a>ICLRDataTarget2 – rozhraní
Podtřídou třídy [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) vrstvy služby přístupu k datům jsou používány k manipulaci s oblastí virtuální paměti v tento cílový proces.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[AllocVirtual – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|Přidělí paměť v adresním prostoru procesu cíl.|  
|[FreeVirtual – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|Uvolní paměť, která byla dříve přidělena v adresním prostoru tento cílový proces.|  
  
## <a name="remarks"></a>Poznámky  
 Klient API (tzn. ladicí program) musí implementovat toto rozhraní v závislosti na konkrétním cílovém procesu. Například živý proces bude mít jinou implementaci než výpis paměti. Cíl nemusí podporovat změny jeho oblastí paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
