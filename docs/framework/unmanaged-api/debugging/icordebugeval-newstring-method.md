---
title: ICorDebugEval::NewString – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5eb86bb80aea5fc65a7362467b78b16a59794d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugevalnewstring-method"></a>ICorDebugEval::NewString – metoda
Přiděluje do nové instance řetězec s zadaný obsah.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `string`  
 [v] Ukazatel na obsah pro řetězec.  
  
## <a name="remarks"></a>Poznámky  
 Řetězec se vždy vytvoří v doméně aplikace, ve kterém je aktuálně spuštěných vlákno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
