---
title: ICorDebugGenericValue – rozhraní 1
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
ms.openlocfilehash: ce4c1b73ab806958627bb68bfdcfcae890bc5e67
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709829"
---
# <a name="icordebuggenericvalue-interface1"></a>ICorDebugGenericValue – rozhraní 1
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
