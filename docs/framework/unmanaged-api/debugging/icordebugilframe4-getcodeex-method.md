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
ms.openlocfilehash: 582e28c18f36b253425b1e0a2034cdd262fddd57
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213735"
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
 Tato metoda je podobná metodě [ICorDebugFrame:: GetCode](icordebugframe-getcode-method.md) s tím rozdílem, že volitelně přistupuje k kódu definovanému požadavkem ReJIT profileru. Volání této metody s `flags` hodnotou `ILCODE_ORIGINAL_IL` je ekvivalentní volání metody [GetCode](icordebugframe-getcode-method.md); Pokud je metoda instrumentovaná, její Il nebude přístupná. `ILCODE_REJIT_IL`umožňuje ladicímu programu přístup k IL definovanému požadavkem ReJIT profileru. Pokud není IL instrumentovaná, `ppCode` má **hodnotu null**a metoda se vrátí `S_OK` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní ICorDebugILFrame4](icordebugilframe4-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [ReJIT: Průvodce](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
