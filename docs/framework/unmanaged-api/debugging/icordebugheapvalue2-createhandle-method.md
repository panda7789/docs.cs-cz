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
ms.openlocfilehash: c69d1f83a4591df4d2dcb7fb9724fa582ea28387
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle – metoda
Vytvoří zadaného typu pro hodnotu halda představuje tento objekt icordebugheapvalue2 – popisovač.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 [v] Hodnota CorDebugHandleType – výčet, který určuje typ popisovače, který se má vytvořit.  
  
 `ppHandle`  
 [out] Ukazatel na adresu icordebughandlevalue – objekt, který představuje nový popisovač pro tuto hodnotu haldy.  
  
## <a name="remarks"></a>Poznámky  
 Popisovač budou vytvořeny v doméně aplikace, která je přidružená hodnota haldy a se zneplatní. Pokud doménu aplikace získá odpojen.  
  
 Více volání této funkce pro stejnou hodnotu haldy vytvoří více obslužných rutin. Protože popisovače vliv na výkon systému uvolňování paměti, měli omezit ladicího programu samotné relativně malý počet popisovače (o 256), které jsou aktivní v čase.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
