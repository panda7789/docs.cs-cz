---
title: ICorDebugReferenceValue – rozhraní
ms.date: 03/30/2017
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
ms.openlocfilehash: 2efba22b4ec372c5ddedd4982a29d66945d3511c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792130"
---
# <a name="icordebugreferencevalue-interface"></a>ICorDebugReferenceValue – rozhraní
Poskytuje metody, které spravují hodnotu, která je odkazem na objekt. (To znamená, že toto rozhraní poskytuje metody, které spravují ukazatel.) Toto rozhraní implementuje "ICorDebugValue".  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Dereference – metoda](icordebugreferencevalue-dereference-method.md)|Načte objekt, na který je odkazováno.|  
|[DereferenceStrong – metoda](icordebugreferencevalue-dereferencestrong-method.md)|Není implementováno. Nevolejte tuto metodu.|  
|[GetValue – metoda](icordebugreferencevalue-getvalue-method.md)|Získá aktuální adresu paměti odkazovaného objektu.|  
|[IsNull – metoda](icordebugreferencevalue-isnull-method.md)|Získá hodnotu, která označuje, zda je tato `ICorDebugReferenceValue` hodnotou null. v takovém případě `ICorDebugReferenceValue` neodkazuje na objekt.|  
|[SetValue – metoda](icordebugreferencevalue-setvalue-method.md)|Nastaví aktuální adresu paměti. To znamená, že tato metoda nastaví tuto `ICorDebugReferenceValue` tak, aby odkazovala na objekt.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR (Common Language Runtime) může provést uvolňování paměti objektů, když probíhá laděný proces. Uvolňování paměti může přesunout objekty kolem paměti. `ICorDebugReferenceValue` bude spolupracovat s uvolňováním paměti, takže jeho informace budou aktualizovány po uvolnění paměti nebo implicitně neověřeny před uvolňováním paměti.  
  
 Po pokračování procesu ladění může být objekt `ICorDebugReferenceValue` implicitně neověřený. Odvozená "ICorDebugHandleValue" není neověřená, dokud není explicitně uvolněna nebo vystavena.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
