---
title: ICorDebugProcess6::GetCode – metoda
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 810590f0d1f7f74b778d73d98a9f7f9b1988b75f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736450"
---
# <a name="icordebugprocess6getcode-method"></a>ICorDebugProcess6::GetCode – metoda
Získá informace o spravovaném kódu na adrese konkrétního kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a>Parametry  
 `codeAddress`  
 [in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) hodnotu, která určuje počáteční adresu segment spravovaného kódu.  
  
 `ppCode`  
 [out] Ukazatel na adresu "ICorDebugCode" objekt, který reprezentuje segment, který spravovaného kódu.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda je pouze k dispozici s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugProcess6 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
