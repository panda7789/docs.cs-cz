---
title: ICorDebugILFrame::EnumerateLocalVariables – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
ms.openlocfilehash: 07331a512dd513a94a7d8c3a8d8b0754d998b94b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131005"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a>ICorDebugILFrame::EnumerateLocalVariables – metoda
Získá enumerátor pro místní proměnné v tomto snímku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppValueEnum`  
 mimo Ukazatel na adresu objektu ICorDebugValueEnum, který je enumerátorem místních proměnných v tomto snímku.  
  
## <a name="remarks"></a>Poznámky  
 `EnumerateLocalVariables` získá enumerátor, který může zobrazit seznam místních proměnných dostupných v rámci volání, který je reprezentován tímto objektem ICorDebugILFrame. Seznam nesmí obsahovat všechny místní proměnné ve spuštěné funkci, protože některé z nich nemusí být aktivní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
