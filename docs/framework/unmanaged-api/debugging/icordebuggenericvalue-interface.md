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
ms.openlocfilehash: 312b8b005998da44feb5ae24ab4a0a17bb948a3f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138573"
---
# <a name="icordebuggenericvalue-interface"></a>ICorDebugGenericValue – rozhraní

Podtřída "ICorDebugValue", která se vztahuje na všechny hodnoty. Toto rozhraní poskytuje metody Get a Set pro hodnotu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|Zkopíruje hodnotu do zadané vyrovnávací paměti.|  
|[SetValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|Zkopíruje novou hodnotu ze zadané vyrovnávací paměti.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugGenericValue` je dílčí rozhraní, protože se nejedná o nevzdáleněu.  
  
 U typů odkazů je hodnota odkaz spíše než obsah odkazu.  
  
 Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
