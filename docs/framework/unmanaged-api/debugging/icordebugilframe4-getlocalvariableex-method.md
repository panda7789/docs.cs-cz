---
title: ICorDebugILFrame4::GetLocalVariableEx – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetCodeEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type:
- apiref
ms.openlocfilehash: ee263e8c49cd6da7278bd2299557336629720d2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178769"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a>ICorDebugILFrame4::GetLocalVariableEx – metoda
[Podporováno v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Získá hodnotu zadané místní proměnné v tomto rámci zásobníku zprostředkující jazyk (IL) a volitelně přistupuje k proměnné přidané v profileru ReJIT instrumentace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,
   [in] DWORD dwIndex,
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 [v] Člen výčtu [ILCodeKind,](ilcodekind-enumeration.md) který určuje, zda je v rámci zahrnuta proměnná přidaná v instrumentaci ReJIT profileru.  
  
 `dwIndex`  
 [v] Index místní proměnné v rámci zásobníku IL.  
  
 `ppValue`  
 [out] Ukazatel na adresu objektu "ICorDebugValue", který představuje načtenou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je podobná [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) metoda, s tím rozdílem, že volitelně přistupuje k proměnné přidané v profileru ReJIT instrumentace. Volání této metody `flags` s `ILCODE_ORIGINAL_IL` hodnotou je ekvivalentní volání [GetLocalVariable](icordebugilframe-getlocalvariable-method.md); pokud je metoda instrumentována dalšími místními proměnnými, nelze k těmto proměnným získat přístup. `ILCODE_REJIT_IL`umožňuje ladicímu programu přístup k místním proměnným přidaným v instrumentaci ReJIT profileru. Pokud NENÍ vybavena nástrojem, metoda `E_INVALIDARG`vrátí .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugILFrame4 – rozhraní](icordebugilframe4-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [ReJIT: Návod, jak](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
