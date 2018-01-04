---
title: "ICorDebugEval2::NewParameterizedArray – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewParameterizedArray
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a605276fac66e395d5663bacff727c235981a868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2newparameterizedarray-method"></a>ICorDebugEval2::NewParameterizedArray – metoda
Přiděluje nový pole typu zadaného elementu a dimenze.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pElementType`  
 [v] Ukazatel na ICorDebugType objekt, který představuje typ elementu uložené v poli.  
  
 `rank`  
 [v] Počet rozměrů pole. V rozhraní .NET Framework verze 2.0 tato hodnota musí být 1.  
  
 `dims`  
 [v] Velikost v bajtech, každá dimenze pole.  
  
 `lowBounds`  
 [v] Volitelný parametr. Dolní mez Každá dimenze pole. Pokud tato hodnota je vynechán, předpokládá se, že dolní mez 0 je pro každou dimenzi.  
  
## <a name="remarks"></a>Poznámky  
 Elementy pole může být instance obecného typu. Toto pole je vytvořen vždy v doméně aplikace, ve které je aktuálně spuštěný vlákno. V rozhraní .NET Framework 2.0, hodnota `rank` musí být 1.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
