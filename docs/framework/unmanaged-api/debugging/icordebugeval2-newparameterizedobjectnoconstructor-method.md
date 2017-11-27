---
title: "ICorDebugEval2::NewParameterizedObjectNoConstructor – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 94cf9e0596e8e5cbd59da319247ced6780d0accb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a>ICorDebugEval2::NewParameterizedObjectNoConstructor – metoda
Vytvoří nový objekt parametrizované typ zadané třídy bez pokus o volání metody konstruktoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pClass`  
 [v] Ukazatel na ICorDebugClass objekt, který představuje třídu objekt, který má být vytvořena instance.  
  
 `nTypeArgs`  
 [v] Počet argumentů předaných.  
  
 `ppTypeArgs`  
 [v] Pole ukazatele, každý z nich odkazuje na objekt ICorDebugType, který reprezentuje typ argumentu pro objekt, který je vytvořena instance.  
  
## <a name="remarks"></a>Poznámky  
 `NewParameterizedObjectNoConstructor` Metoda se nezdaří, pokud nesprávný počet argumentů nebo jsou předány nesprávné typy argumenty typu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
