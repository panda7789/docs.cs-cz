---
title: ICorDebugILFrame4::EnumerateLocalVariablesEx – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ba61a91f2296d6e5cc795c3775bb72247e34a56
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43453099"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a>ICorDebugILFrame4::EnumerateLocalVariablesEx – metoda
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Získá enumerátor pro místní proměnné v rámci a volitelně obsahuje proměnné, které jsou přidány v profileru instrumentace ReJIT.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `flags`  
 [in] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) člen výčtu, která určuje, zda proměnné přidány v profileru instrumentace ReJIT jsou zahrnuty v rámci.  
  
 `ppValueEnum`  
 [out] Ukazatel na adresu "Icordebugvalueenum –" objekt enumerátoru pro místní proměnné v tomto snímku.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je podobný [enumeratelocalvariables –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) metody, s tím rozdílem, že se volitelně přistupuje k proměnné přidány v profileru instrumentace ReJIT. Nastavení `flags` k `ILCODE_ORIGINAL_IL` je ekvivalentní volání [icordebugilframe::enumeratelocalvariables –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md). Nastavení `flags` k `ILCODE_REJIT_IL` umožňuje přistupovat k místním proměnným přidán v profileru instrumentace ReJIT ladicí program. Pokud není instrumentovaný převodní jazyk (IL), je prázdný výčet a metoda vrátí `S_OK`.  
  
 Enumerátor nemusí zahrnovat všechny místní proměnné v metodě spuštěné, protože některé z nich nesmí být aktivní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugILFrame4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT: Nepředstavuje Průvodce](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
