---
title: "CLRDataCreateInstance – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- COM
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0740e80732e03ac6c1e7cf974d258113a181ea9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="clrdatacreateinstance-function"></a>CLRDataCreateInstance – funkce
Vytvoří objekt rozhraní pro zadanou cílovou položku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Identifikátor rozhraní, které má být vytvořena instance.  
  
 `target`  
 [v] Ukazatel na uživatele implementované [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) objekt, který reprezentuje cílová položka pro který chcete vytvořit objekt rozhraní.  
  
 `iface`  
 [out] Ukazatel na adresu objekt vrácený rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 `ICLRDataTarget` Objektu je implementováno modulem zapisovač ladění aplikace. Implementace závisí na typu položky cíl reprezentované. Cílová položka může být proces, výpis stavu paměti, vzdálený počítač a tak dále.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Globální statické funkce pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
