---
title: ICorDebugHeapValue2::CreateHandle – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da5c5a12df5689f113857045ba4bcda696bda8f5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756729"
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle – metoda
Vytvoří popisovač haldy hodnoty reprezentovaný tímto objektem icordebugheapvalue2 – zadaného typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `type`  
 [in] Hodnota cordebughandletype – výčet, který určuje typ popisovače, který se má vytvořit.  
  
 `ppHandle`  
 [out] Ukazatel na adresu icordebughandlevalue – objekt, který reprezentuje nový popisovač pro tuto hodnotu haldy.  
  
## <a name="remarks"></a>Poznámky  
 Popisovač se vytvoří v aplikační doméně, která souvisí s hodnotou haldy a už nebudou platné, pokud získá uvolněné doméně aplikace.  
  
 Více volání této funkce pro stejnou hodnotu haldy vytvoří více popisovačů. Protože popisovače vliv na výkon systému uvolňování paměti, ladicí program by měl omezit relativně malý počet popisovačů (přibližně 256), které jsou aktivní v čase.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
