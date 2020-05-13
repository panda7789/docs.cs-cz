---
title: ICorDebugObjectValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
ms.openlocfilehash: 603ab20b57dc4ba736b0342797d0be649a5bebc4
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207482"
---
# <a name="icordebugobjectvalue-interface"></a>ICorDebugObjectValue – rozhraní

Podtřída "ICorDebugValue", která představuje hodnotu, která obsahuje objekt.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetClass – metoda](icordebugobjectvalue-getclass-method.md)|Získá ukazatel rozhraní modulu CLR (Common Language Runtime) <xref:System.Type> objektu, na který `ICorDebugObjectValue` odkazují.|  
|[GetContext – metoda](icordebugobjectvalue-getcontext-method.md)|Není implementováno.|  
|[GetFieldValue – metoda](icordebugobjectvalue-getfieldvalue-method.md)|Získá ukazatel rozhraní na [ICorDebugValue](icordebugvalue-interface.md) , který představuje hodnotu zadaného pole zadané třídy.|  
|[GetManagedCopy – metoda](icordebugobjectvalue-getmanagedcopy-method.md)|Zastaralé. Nevolejte tuto metodu.|  
|[GetVirtualMethod – metoda](icordebugobjectvalue-getvirtualmethod-method.md)|Není implementováno.|  
|[IsValueClass – metoda](icordebugobjectvalue-isvalueclass-method.md)|Získá hodnotu, která označuje, zda je objekt, na který odkazuje, `ICorDebugObjectValue` typ hodnoty.|  
|[SetFromManagedCopy – metoda](icordebugobjectvalue-setfrommanagedcopy-method.md)|Zastaralé. Nevolejte tuto metodu.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugObjectValue`Zůstane platná, dokud se proces, který se právě ladí, nepokračuje.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
