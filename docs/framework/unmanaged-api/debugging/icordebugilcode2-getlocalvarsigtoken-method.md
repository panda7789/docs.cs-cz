---
title: ICorDebugILCode2::GetLocalVarSigToken – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 17665b77-1342-4115-94fd-9f45b0ecfb0f
topic_type:
- apiref
ms.openlocfilehash: 3759cfa330ac37d2ed62a0b8bb70b5e10cd9d12e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782451"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a>ICorDebugILCode2::GetLocalVarSigToken – metoda
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Získá token metadat pro podpis místní proměnné pro funkci, která je reprezentovaná touto instancí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pmdSig`  
 mimo Ukazatel na token `mdSignature` pro podpis místní proměnné pro tuto funkci nebo `mdSignatureNil`, pokud není k dispozici podpis (tj., pokud funkce nemá žádné místní proměnné).  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugILCode2 – rozhraní](icordebugilcode2-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
