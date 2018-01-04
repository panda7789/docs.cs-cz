---
title: "ICorDebugExceptionDebugEvent::GetNativeIP – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32e75a18645c000562cdd94478c6ef8db41a01a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a>ICorDebugExceptionDebugEvent::GetNativeIP – metoda
Získá ukazatel na nativní instrukce pro tuto událost výjimky ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pIP`  
 [out] Ukazatel na ukazatel instrukce pro tuto výjimku ladění událostí. Další informace naleznete v části Poznámky.  
  
## <a name="remarks"></a>Poznámky  
 Význam tento ukazatel instrukce závisí na typu události, jak je znázorněno v následující tabulce.  
  
|Typ události|Význam `pStackPointer` hodnota|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|Adresa chybující instrukcí.|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|Adresu kódu v rámci indikován [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) metoda, kde by provádění obnoveno, pokud měl byla vyvolána žádná výjimka. Výjimka může nebo nemusí způsobit jiný kód, jako je blok catch `try/catch/finally` klauzule spouštění této rámce.|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|Kód adres kde `catch` provádění obslužná rutina se spustí v rámci indikován [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) metoda.|  
|[MANAGED_EXCEPTION_UNHANDLED](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|`pIP`je 0.|  
  
 Typ události má k dispozici [icordebugdebugevent::geteventkind –](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metoda.  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugExceptionDebugEvent – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
