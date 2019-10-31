---
title: ICorDebugChain::EnumerateFrames – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
ms.openlocfilehash: 0b024d3396dfe1796fcb18afa122d4aee39c4ccc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132726"
---
# <a name="icordebugchainenumerateframes-method"></a>ICorDebugChain::EnumerateFrames – metoda
Získá enumerátor, který obsahuje všechny spravované rámce zásobníku v řetězci počínaje posledním rámcem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppFrames`  
 mimo Ukazatel na adresu objektu ICorDebugFrameEnum, který je enumerátorem pro rámce zásobníku.  
  
## <a name="remarks"></a>Poznámky  
 Řetěz představuje fyzický zásobník volání pro vlákno.  
  
 Metoda `EnumerateFrames` by měla být volána pouze pro spravované řetězy. Rozhraní API pro ladění neposkytuje metody pro získání rámců obsažených v nespravovaných řetězcích. K získání těchto informací musí ladicí program použít jiný způsob.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
