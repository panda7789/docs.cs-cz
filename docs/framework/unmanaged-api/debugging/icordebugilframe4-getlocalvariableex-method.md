---
title: "ICorDebugILFrame4::GetLocalVariableEx – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILFrame4.GetCodeEx
api_location: mscordbi.dll
api_type: COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 968e504eadb5f7444095a6a98dea414aa4486dce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe4getlocalvariableex-method"></a>ICorDebugILFrame4::GetLocalVariableEx – metoda
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Získá hodnotu zadaného místní proměnné v této rámce zásobníku převodní jazyk (IL) a volitelně přistupuje k proměnné přidali v ReJIT instrumentace profileru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `flags`  
 [v] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) člen výčtu, která určuje, zda proměnné přidali v ReJIT instrumentace profileru je součástí rámečku.  
  
 `dwIndex`  
 [v] Index místní proměnné v rámci zásobníku IL.  
  
 `ppValue`  
 [out] Ukazatel na adresu "ICorDebugValue" objekt, který reprezentuje načtené hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je podobná [getlocalvariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) metoda, s tím rozdílem, že IT oddělení volitelně přistupuje k proměnné přidali v ReJIT instrumentace profileru. Voláním této metody se `flags` hodnotu `ILCODE_ORIGINAL_IL` je ekvivalentní volání [getlocalvariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); Pokud je metoda instrumentovány s další místní proměnné, tyto proměnné nelze získat přístup. `ILCODE_REJIT_IL`Umožňuje pro přístup k místní proměnné přidali v ReJIT instrumentace profileru ladicího programu. Pokud není instrumentována IL, vrátí metoda `E_INVALIDARG`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugILFrame4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT: Postupy: Průvodce](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
