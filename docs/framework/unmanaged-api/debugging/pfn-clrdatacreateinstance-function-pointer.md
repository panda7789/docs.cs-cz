---
title: "PFN_CLRDataCreateInstance – ukazatel na funkci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: PFN_CLRDataCreateInstance
api_location: mscordbi.dll
api_type: COM
f1_keywords: PFN_CLRDataCreateInstance
helpviewer_keywords: PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98a966434332549d9ceb7f29de81e19fa1b2108f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="pfnclrdatacreateinstance-function-pointer"></a>PFN_CLRDataCreateInstance – ukazatel na funkci
Odkazuje na funkci, která vytvoří objekt rozhraní pro zadanou cílovou položku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
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
