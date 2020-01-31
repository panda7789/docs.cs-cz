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
ms.openlocfilehash: e77344a99189ec8e234129262d45698c794dc249
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788516"
---
# <a name="icordebugilframe4getcodeex-method"></a>ICorDebugILFrame4::GetCodeEx – metoda
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Získá ukazatel na kód, který tento rámec zásobníku provádí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 pro Člen výčtu [ILCodeKind](ilcodekind-enumeration.md) , který určuje, zda je do rámce zahrnut převodní jazyk (IL) definovaný požadavkem ReJIT profileru.  
  
 `ppCode`  
 mimo Ukazatel na adresu objektu "ICorDebugCode", který představuje kód, který tento rámec zásobníku provádí.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je podobná metodě [ICorDebugFrame:: GetCode](icordebugframe-getcode-method.md) s tím rozdílem, že volitelně přistupuje k kódu definovanému požadavkem ReJIT profileru. Volání této metody s hodnotou `flags` `ILCODE_ORIGINAL_IL` je ekvivalentní volání metody [GetCode](icordebugframe-getcode-method.md); Pokud je metoda instrumentovaná, její IL nebude přístupná. `ILCODE_REJIT_IL` umožňuje ladicímu programu přístup k IL definovanému požadavkem ReJIT profileru. Pokud úroveň IL není instrumentovaná, `ppCode` je **null**a metoda vrátí `S_OK`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugILFrame4 – rozhraní](icordebugilframe4-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
- [ReJIT: Průvodce](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
