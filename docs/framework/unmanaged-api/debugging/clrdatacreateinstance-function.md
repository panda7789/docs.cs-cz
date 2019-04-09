---
title: CLRDataCreateInstance – funkce
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73a4a8a2fc737bbf4b49ca859f0549ca7efd54a2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089767"
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
  
## <a name="parameters"></a>Parametry  
 `iid`  
 [in] Identifikátor rozhraní má být vytvořena.  
  
 `target`  
 [in] Ukazatel na uživatelské implementované [iclrdatatarget –](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) objekt, který představuje cílovou položku, pro který chcete vytvořit objekt rozhraní.  
  
 `iface`  
 [out] Ukazatel na adresu objektu vrácené rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 `ICLRDataTarget` Objektu je implementováno tvůrci ladění aplikace. Implementace závisí na typu představované cílovou položku. Cílová položka může být proces, výpis paměti, vzdálený počítač a tak dále.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
