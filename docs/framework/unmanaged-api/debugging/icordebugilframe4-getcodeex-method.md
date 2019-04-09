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
ms.openlocfilehash: 6d61981d26d21ec1e5e24093817586ebf45b129e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162329"
---
# <a name="icordebugilframe4getcodeex-method"></a>ICorDebugILFrame4::GetCodeEx – metoda
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Získá ukazatel na kód, který spouští tento rámec zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 [in] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) člen výčtu, který určuje, zda je v rámci zahrnuta (IL intermediate language) určené profileru ReJIT požadavku.  
  
 `ppCode`  
 [out] Ukazatel na adresu objektu "ICorDebugCode", který představuje kód, který spouští tento rámec zásobníku.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je podobný [icordebugframe::getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) metody, s tím rozdílem, že se volitelně přistupuje k určené požadavek ReJIT profileru kód. Volání této metody `flags` hodnotu `ILCODE_ORIGINAL_IL` je ekvivalentní volání [getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); Pokud je instrumentováno metodu, jeho IL nebude přístupná. `ILCODE_REJIT_IL` Umožňuje ladicího programu pro přístup k IL určené profileru ReJIT požadavku. Pokud není instrumentovaný IL, `ppCode` je **null**, a vrátí metodu `S_OK`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní ICorDebugILFrame4](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [Debugging – rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ReJIT: Nepředstavuje Průvodce](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
