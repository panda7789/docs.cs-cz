---
title: ICorDebugAppDomain::IsAttached – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.IsAttached
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a3f01edcd6ce1d16ab2c651a66d2fd9cd2eb0ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737819"
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="e0f6e-102">ICorDebugAppDomain::IsAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="e0f6e-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="e0f6e-103">Získá hodnotu, která označuje, zda ladicí program je připojen k doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="e0f6e-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0f6e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0f6e-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0f6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0f6e-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="e0f6e-106">[out] `true` Pokud je ladicí program připojený do domény aplikace; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="e0f6e-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0f6e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0f6e-107">Remarks</span></span>  
 <span data-ttu-id="e0f6e-108">Icordebugcontroller – metody nelze použít, dokud ladicí program připojí k doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="e0f6e-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0f6e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0f6e-109">Requirements</span></span>  
 <span data-ttu-id="e0f6e-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0f6e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0f6e-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0f6e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0f6e-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0f6e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0f6e-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0f6e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
