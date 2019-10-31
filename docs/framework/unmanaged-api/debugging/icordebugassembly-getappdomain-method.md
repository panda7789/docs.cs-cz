---
title: ICorDebugAssembly::GetAppDomain – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type:
- apiref
ms.openlocfilehash: 53042e722809a6574396648529c677d749154716
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132729"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="b1ea5-102">ICorDebugAssembly::GetAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="b1ea5-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="b1ea5-103">Získá ukazatel rozhraní na doménu aplikace, která obsahuje tuto instanci `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="b1ea5-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1ea5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1ea5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1ea5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1ea5-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="b1ea5-106">mimo Ukazatel na adresu rozhraní ICorDebugAppDomain, které představuje doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="b1ea5-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1ea5-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1ea5-107">Remarks</span></span>  
 <span data-ttu-id="b1ea5-108">Pokud je toto sestavení systémové sestavení, `GetAppDomain` vrátí hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b1ea5-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1ea5-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1ea5-109">Requirements</span></span>  
 <span data-ttu-id="b1ea5-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1ea5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1ea5-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b1ea5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1ea5-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b1ea5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1ea5-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1ea5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
