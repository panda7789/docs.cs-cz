---
title: ICorDebugObjectValue2::GetVirtualMethodAndType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue2.GetVirtualMethodAndType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue2::GetVirtualMethodAndType
helpviewer_keywords:
- GetVirtualMethodAndType method [.NET Framework debugging]
- ICorDebugObjectValue2::GetVirtualMethodAndType method
ms.assetid: 621b4543-a8f7-4117-98e4-930992cd688a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 252a65c66764d60f5e307ba1eaad4ded34d9744d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162147"
---
# <a name="icordebugobjectvalue2getvirtualmethodandtype-method"></a>ICorDebugObjectValue2::GetVirtualMethodAndType – metoda
Tato metoda není dosud implementována.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetVirtualMethodAndType (  
    [in] mdMemberRef          memberRef,  
    [out] ICorDebugFunction   **ppFunction,  
    [out] ICorDebugType       **ppType  
);  
```  
  
## <a name="remarks"></a>Poznámky  
 Získá rozhraní ukazatelů "ICorDebugFunction" a "ICorDebugType" instancí, které představují nejvíce Odvozená metoda a typ odkazu zadaného člena.  
  
## <a name="see-also"></a>Viz také:
