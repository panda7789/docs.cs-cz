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
ms.openlocfilehash: 7c5359ddf2c021f77ad1ea0a8579316c3c773fd5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209783"
---
# <a name="icordebuggenericvalue-interface"></a>ICorDebugGenericValue – rozhraní

Podtřída "ICorDebugValue", která se vztahuje na všechny hodnoty. Toto rozhraní poskytuje metody Get a Set pro hodnotu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetValue – metoda](icordebuggenericvalue-getvalue-method.md)|Zkopíruje hodnotu do zadané vyrovnávací paměti.|  
|[SetValue – metoda](icordebuggenericvalue-setvalue-method.md)|Zkopíruje novou hodnotu ze zadané vyrovnávací paměti.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugGenericValue`je dílčí rozhraní, protože se nejedná o nevzdáleněu.  
  
 U typů odkazů je hodnota odkaz spíše než obsah odkazu.  
  
 Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
