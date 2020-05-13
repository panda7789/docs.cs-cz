---
title: ICorDebugInternalFrame2::GetFrameAddress – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.GetFrameAddress Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type:
- apiref
ms.openlocfilehash: 51c8f9a2b66d7b2553949056f7cdbedcf5ea37d6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209913"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a>ICorDebugInternalFrame2::GetFrameAddress – metoda
Vrátí adresu zásobníku interního rámce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAddress`  
 mimo Ukazatel na `CORDB_ADDRESS` vnitřní rámec.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Adresa interního rámce byla úspěšně vrácena.|  
|E_FAIL|Adresa interního rámce nemohla být vrácena.|  
|E_INVALIDARG|`pAddress` je `null`.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnota vrácená v rámci `pAddress` lze použít k určení umístění vnitřního rámce relativně k ostatním snímkům v zásobníku. I na počítačích založených na platformě IA-64, interním rámcům v zásobníku a neexistuje žádný odpovídající ukazatel na záložní úložiště.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugInternalFrame2 – rozhraní](icordebuginternalframe2-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
