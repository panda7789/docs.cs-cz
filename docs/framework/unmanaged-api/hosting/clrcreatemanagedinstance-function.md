---
title: "ClrCreateManagedInstance – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: ClrCreateManagedInstance
helpviewer_keywords: ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64a1bc6bbd89e3a36ac53b322bb246a7e61baa67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance – funkce
Vytvoří instanci je určeného spravovaného typu.  
  
 Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Použijte aktivace COM vytvořit instanci spravovaného typu, nebo použijte hostování (viz [CLR hostování rozhraní přidaná v rozhraní .NET Framework 4 a 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pTypeName`  
 [v] Ukazatel na název požadovaného typu instance.  
  
 `riid`  
 [v] `IID` Instance typu požadováno.  
  
 `ppObject`  
 [out] Ukazatel na ukazatel na instanci spravovaného typu, který byl vyžádán volajícího.  
  
## <a name="remarks"></a>Poznámky  
 Modul common language runtime by měl být již načtena do procesu. Například můžete načíst pomocí volání [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkce před `ClrCreateManagedInstance` funkce je volána. Pokud není načteno modul runtime, `ClrCreateManagedInstance` poprvé pokusí načíst v1.0.3705 modulu runtime. Pokud to nepomůže, pokusí se načíst nejnovější verzi modulu runtime.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
