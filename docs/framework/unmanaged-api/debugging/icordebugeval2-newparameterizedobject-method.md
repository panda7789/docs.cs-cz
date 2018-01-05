---
title: "ICorDebugEval2::NewParameterizedObject – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewParameterizedObject
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 39b69a82f25ab6df5f2bd2f6dc70caf1bf13a0f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2newparameterizedobject-method"></a>ICorDebugEval2::NewParameterizedObject – metoda
Vytvoří nový objekt parametrizované typu a volá konstruktor metodu objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pConstructor`  
 [v] Ukazatel na ICorDebugFunction objekt, který reprezentuje konstruktoru objekt, který má být vytvořena instance.  
  
 `nTypeArgs`  
 [v] Počet argumentů předaných.  
  
 `ppTypeArgs`  
 [v] Pole ukazatele, každý z nich odkazuje na objekt ICorDebugType, který reprezentuje typ argumentu pro objekt, který je vytvořena instance.  
  
 `nArgs`  
 [v] Počet argumentů předaných konstruktoru.  
  
 `ppArgs`  
 [v] Pole ukazatele, každý z nich odkazuje na objekt ICorDebugValue, který představuje hodnota argumentu předaného konstruktoru.  
  
## <a name="remarks"></a>Poznámky  
 Může trvat objektu konstruktor <xref:System.Type> parametry.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
