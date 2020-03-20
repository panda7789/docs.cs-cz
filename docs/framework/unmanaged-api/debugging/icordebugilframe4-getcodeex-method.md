---
title: ICorDebugILFrame4::GetCodeEx – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
ms.openlocfilehash: ef2e4bc0caddd6b13c8dbe8edb59e0673519421b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178785"
---
# <a name="icordebugilframe4getcodeex-method"></a>ICorDebugILFrame4::GetCodeEx – metoda
[Podporováno v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Získá ukazatel na kód, který tento rámec zásobníku je provádění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 [v] Člen výčtu [ILCodeKind,](ilcodekind-enumeration.md) který určuje, zda je v rámci zahrnut zprostředkující jazyk (IL) definovaný požadavkem ReJIT profileru.  
  
 `ppCode`  
 [out] Ukazatel na adresu objektu "ICorDebugCode", který představuje kód, který tento rámec zásobníku je spuštěn.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je podobná [metodě ICorDebugFrame::GetCode](icordebugframe-getcode-method.md) s tím rozdílem, že volitelně přistupuje ke kódu definovanému požadavkem ReJIT profileru. Volání této metody `flags` s `ILCODE_ORIGINAL_IL` hodnotou je ekvivalentní volání [GetCode](icordebugframe-getcode-method.md); pokud je metoda instrumentována, její IL nebude přístupná. `ILCODE_REJIT_IL`umožňuje ladicímu programu přístup k IL definovanému požadavkem ReJIT profileru. Pokud IL není instrumentován, `ppCode` je **null** `S_OK`a metoda vrátí .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugILFrame4 – rozhraní](icordebugilframe4-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [ReJIT: Návod, jak](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
