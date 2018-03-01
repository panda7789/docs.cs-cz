---
title: ICorDebugReferenceValue Interface1
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
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ac6260a601f7fdacf84034a6ae83c9423fafa11
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugreferencevalue-interface1"></a>ICorDebugReferenceValue Interface1
Poskytuje metody, které spravují hodnotu, která je odkaz na objekt. (To znamená, toto rozhraní poskytuje metody, které spravují ukazatel.) Toto rozhraní implementuje "ICorDebugValue".  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Dereference – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|Získá objekt, který se odkazuje.|  
|[DereferenceStrong – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|Není implementováno. Tato metoda není volána.|  
|[GetValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|Získá aktuální adresa paměti odkazovaného objektu.|  
|[IsNull – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|Získá hodnotu, která určuje, jestli to `ICorDebugReferenceValue` v takovém případě je hodnota null, `ICorDebugReferenceValue` neukazuje na objekt.|  
|[SetValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|Nastaví aktuální adresa paměti. To znamená, tato metoda nastaví to `ICorDebugReferenceValue` tak, aby odkazoval na objekt.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR (CLR) může proveďte uvolňování u objektů, pokud proces vyladěnou pokračuje. Kolekce paměti může pohyb objektů v paměti. `ICorDebugReferenceValue` Budou buď spolupracovat s uvolnění paměti tak, aby se aktualizuje jeho informace po uvolnění paměti, nebo bude byla zneplatněna implicitně před uvolnění paměti.  
  
 `ICorDebugReferenceValue` Objektu může být implicitně zneplatněné, po vyladěnou proces pokračuje. Odvozené icordebughandlevalue "–" není zrušena, dokud nebude explicitně vydané nebo vystavené.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
    
    
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
