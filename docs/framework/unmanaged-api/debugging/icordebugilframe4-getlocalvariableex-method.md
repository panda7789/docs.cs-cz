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
ms.openlocfilehash: 8d6ef550309ea7f8bae616a5f7e5c41b4f07374a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213722"
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
 Tato metoda je podobná metodě [GetLocalVariable –](icordebugilframe-getlocalvariable-method.md) , s tím rozdílem, že volitelně přistupuje k proměnné přidané v profileru ReJIT instrumentace. Volání této metody s `flags` hodnotou `ILCODE_ORIGINAL_IL` je ekvivalentní volání [GetLocalVariable –](icordebugilframe-getlocalvariable-method.md); Pokud je metoda instrumentovaná pomocí dalších místních proměnných, tyto proměnné nejsou k dispozici. `ILCODE_REJIT_IL`umožňuje ladicímu programu přístup k místním proměnným přidaným v profileru ReJIT instrumentace. Pokud úroveň IL není instrumentovaná, metoda se vrátí `E_INVALIDARG` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní ICorDebugILFrame4](icordebugilframe4-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [ReJIT: Průvodce](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
