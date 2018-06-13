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
ms.openlocfilehash: c9a6978f35b5ea9fb71f8e933dbc7a08b1c390ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416498"
---
# <a name="icordebugobjectvalue2getvirtualmethodandtype-method"></a><span data-ttu-id="76593-102">ICorDebugObjectValue2::GetVirtualMethodAndType – metoda</span><span class="sxs-lookup"><span data-stu-id="76593-102">ICorDebugObjectValue2::GetVirtualMethodAndType Method</span></span>
<span data-ttu-id="76593-103">Tato metoda není dosud implementována.</span><span class="sxs-lookup"><span data-stu-id="76593-103">This method is not yet implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76593-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76593-104">Syntax</span></span>  
  
```  
HRESULT GetVirtualMethodAndType (  
    [in] mdMemberRef          memberRef,  
    [out] ICorDebugFunction   **ppFunction,  
    [out] ICorDebugType       **ppType  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="76593-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="76593-105">Remarks</span></span>  
 <span data-ttu-id="76593-106">Získá rozhraní ukazatele "ICorDebugFunction" a "ICorDebugType" instancí, které představují nejodvozenějších metoda a typ pro odkaz na zadaný člen.</span><span class="sxs-lookup"><span data-stu-id="76593-106">Gets interface pointers to the "ICorDebugFunction" and "ICorDebugType" instances that represent the most derived method and type for the specified member reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76593-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="76593-107">See Also</span></span>  
    
 
