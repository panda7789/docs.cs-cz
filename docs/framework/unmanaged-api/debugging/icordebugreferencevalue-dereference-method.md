---
title: ICorDebugReferenceValue::Dereference – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b436fa14322d444a6c8b515ba8e50698eecb95ba
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487015"
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="e24e5-102">ICorDebugReferenceValue::Dereference – metoda</span><span class="sxs-lookup"><span data-stu-id="e24e5-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="e24e5-103">Získá objekt, na který odkazuje.</span><span class="sxs-lookup"><span data-stu-id="e24e5-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e24e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e24e5-104">Syntax</span></span>  
  
```  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e24e5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e24e5-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="e24e5-106">[out] Ukazatel na adresu ICorDebugValue, který představuje objekt, na kterou odkazuje tento objekt ICorDebugReferenceValue.</span><span class="sxs-lookup"><span data-stu-id="e24e5-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e24e5-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e24e5-107">Remarks</span></span>  
 <span data-ttu-id="e24e5-108">`ICorDebugValue` Objektu je platná pouze tehdy, když svůj odkaz nebyl dosud bylo zakázáno.</span><span class="sxs-lookup"><span data-stu-id="e24e5-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e24e5-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e24e5-109">Requirements</span></span>  
 <span data-ttu-id="e24e5-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e24e5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e24e5-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e24e5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e24e5-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e24e5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e24e5-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e24e5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
