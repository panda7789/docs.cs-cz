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
ms.openlocfilehash: 30e0b0c4ed9bac4abd1dc185031e41c1e3ed014a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134664"
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="32aa6-102">ICorDebugAppDomain::IsAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="32aa6-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="32aa6-103">Získá hodnotu, která označuje, zda je ladicí program připojen k doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="32aa6-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32aa6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32aa6-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32aa6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32aa6-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="32aa6-106">[out] `true`, pokud je ladicí program připojen k doméně aplikace; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="32aa6-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32aa6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="32aa6-107">Remarks</span></span>  
 <span data-ttu-id="32aa6-108">Metody ICorDebugController nelze použít, dokud se ladicí program nepřipojí k doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="32aa6-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32aa6-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32aa6-109">Requirements</span></span>  
 <span data-ttu-id="32aa6-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32aa6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32aa6-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="32aa6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32aa6-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="32aa6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32aa6-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32aa6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
