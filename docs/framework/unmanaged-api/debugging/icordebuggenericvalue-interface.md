---
title: ICorDebugGenericValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad2209c6e28c7749bd149902e5b696955ee7f13f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981982"
---
# <a name="icordebuggenericvalue-interface"></a>ICorDebugGenericValue – rozhraní

Podtřída ICorDebugValue"", která se vztahuje na všechny hodnoty. Toto rozhraní poskytuje metody Get a Set pro hodnotu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|Hodnota se zkopíruje do zadané vyrovnávací paměti.|  
|[SetValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|Zkopíruje nové hodnoty ze zadané vyrovnávací paměti.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugGenericValue` je dílčí rozhraní, protože je bez podpory vzdáleného přístupu.  
  
 Pro typy odkazů hodnota je odkaz, nikoli obsah odkazu.  
  
 Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
