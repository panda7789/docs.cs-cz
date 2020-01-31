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
ms.openlocfilehash: 017c14e9170087f3c3c9de64f50d165fc91aa297
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782407"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a>ICorDebugILFrame4::GetLocalVariableEx – metoda
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Získá hodnotu zadané místní proměnné v rámci tohoto bloku zásobníku pro mezilehlé jazyky (IL) a volitelně přistupuje k proměnné přidané v profileru ReJIT instrumentace.  
  
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
 pro Člen výčtu [ILCodeKind](ilcodekind-enumeration.md) , který určuje, jestli je do tohoto rámce zahrnutá proměnná přidaná v profileru ReJIT instrumentace.  
  
 `dwIndex`  
 pro Index místní proměnné v rámci bloku IL.  
  
 `ppValue`  
 mimo Ukazatel na adresu objektu "ICorDebugValue", který představuje načtenou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je podobná metodě [GetLocalVariable –](icordebugilframe-getlocalvariable-method.md) , s tím rozdílem, že volitelně přistupuje k proměnné přidané v profileru ReJIT instrumentace. Volání této metody s hodnotou `flags` `ILCODE_ORIGINAL_IL` je ekvivalentní volání [GetLocalVariable –](icordebugilframe-getlocalvariable-method.md); Pokud je metoda instrumentovaná pomocí dalších místních proměnných, k těmto proměnným nelze přidružit. `ILCODE_REJIT_IL` umožňuje ladicímu programu přístup k místním proměnným přidaným v profileru ReJIT instrumentace. Pokud není IL instrumentovat, metoda vrátí `E_INVALIDARG`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugILFrame4 – rozhraní](icordebugilframe4-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
- [ReJIT: Průvodce](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
