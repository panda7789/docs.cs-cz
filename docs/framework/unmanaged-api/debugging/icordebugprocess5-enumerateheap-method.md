---
title: ICorDebugProcess5::EnumerateHeap – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6dbae1abefd3959c629031f23419d0c93721c322
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678301"
---
# <a name="icordebugprocess5enumerateheap-method"></a>ICorDebugProcess5::EnumerateHeap – metoda
Získá enumerátor pro objekty na spravované haldě.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppObject`  
 [out] Ukazatel na adresu [icordebugheapenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) rozhraní objektu, který je enumerátor pro objekty, které jsou umístěny na spravované haldě.  
  
## <a name="remarks"></a>Poznámky  
 Před voláním `ICorDebugProcess5::EnumerateHeap` metoda, měli byste zavolat [icordebugprocess5::getgcheapinformation –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metoda a zkoumat hodnoty `areGCStructuresValid` pole vráceného [cor_heapinfo –](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Ujistěte se, že haldě uvolňování paměti v jejím aktuálním stavu vyčíslitelný objekt. Kromě toho `ICorDebugProcess5::EnumerateHeap` vrátí `E_FAIL` Pokud připojíte příliš brzy během životnosti procesu před paměť, pro je přidělena spravované haldě.  
  
 [Icordebugheapenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objektu rozhraní je standardní výčet odvozený od icordebugenum – rozhraní, která umožňuje vytvořit výčet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objekty. Naplní tuto metodu [icordebugheapenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objektu kolekce s [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instancí, které poskytují informace o všech objektech. Kolekce může zahrnovat také [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instancí, které poskytují informace o objektech, které nejsou žádné kořenem objektu, ale nebyla ještě shromažďuje systému uvolňování paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugProcess5 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
