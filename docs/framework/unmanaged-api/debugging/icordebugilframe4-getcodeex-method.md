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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb50459e36cfeb76a0c9a1e1cd4544260d484f45
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926800"
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
 pro Člen výčtu [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) , který určuje, zda je do rámce zahrnut převodní jazyk (IL) definovaný požadavkem ReJIT profileru.  
  
 `ppCode`  
 mimo Ukazatel na adresu objektu "ICorDebugCode", který představuje kód, který tento rámec zásobníku provádí.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je podobná metodě [ICorDebugFrame:: GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) s tím rozdílem, že volitelně přistupuje k kódu definovanému požadavkem ReJIT profileru. Volání této metody s `flags` `ILCODE_ORIGINAL_IL` hodnotou je ekvivalentní volání metody [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); Pokud je metoda instrumentovaná, její Il nebude přístupná. `ILCODE_REJIT_IL`umožňuje ladicímu programu přístup k IL definovanému požadavkem ReJIT profileru. Pokud není Il instrumentovaná, `ppCode` má **hodnotu null**a metoda se vrátí. `S_OK`  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugILFrame4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ReJIT: Průvodce postupy](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
