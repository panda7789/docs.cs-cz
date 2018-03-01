---
title: "ICorDebugILFrame4::EnumerateLocalVariablesEx – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c82ecd9045deb772e31e549bf1050f85b148fd0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a>ICorDebugILFrame4::EnumerateLocalVariablesEx – metoda
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Získá enumerátor pro místní proměnné v rámečku a volitelně obsahuje proměnné přidali v ReJIT instrumentace profileru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `flags`  
 [v] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) člen výčtu, která určuje, zda proměnné přidali v ReJIT instrumentace profileru jsou zahrnuty do rámečku.  
  
 `ppValueEnum`  
 [out] Ukazatel na adresu "ICorDebugValueEnum" objekt, který je enumerátor pro místní proměnné do tohoto rámce.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je podobná [enumeratelocalvariables –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) metoda, s tím rozdílem, že IT oddělení volitelně přistupuje k proměnné přidali v ReJIT instrumentace profileru. Nastavení `flags` k `ILCODE_ORIGINAL_IL` je ekvivalentní volání [icordebugilframe::enumeratelocalvariables –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md). Nastavení `flags` k `ILCODE_REJIT_IL` umožňuje ladicího programu pro přístup k místní proměnné přidali v ReJIT instrumentace profileru. Pokud není instrumentována převodní jazyk (IL), je prázdný výčet a vrátí metoda `S_OK`.  
  
 Enumerátor nemusí zahrnovat všechny místní proměnné v metodě spuštěné, vzhledem k tomu, že některé z nich nemusí být aktivní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugILFrame4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT: Postupy: Průvodce](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
