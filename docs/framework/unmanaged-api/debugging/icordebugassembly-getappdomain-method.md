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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9ba09b80d7118b0ccd9b1647011a7fc7cd74e22
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485106"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="30038-102">ICorDebugAssembly::GetAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="30038-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="30038-103">Získá ukazatel rozhraní k doméně aplikace, která obsahuje tato `ICorDebugAssembly` instance.</span><span class="sxs-lookup"><span data-stu-id="30038-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30038-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30038-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30038-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="30038-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="30038-106">[out] Ukazatel na adresu icordebugappdomain – rozhraní, která představuje doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="30038-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30038-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30038-107">Remarks</span></span>  
 <span data-ttu-id="30038-108">Pokud toto sestavení je sestavení systému `GetAppDomain` , vrátí hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="30038-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30038-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30038-109">Requirements</span></span>  
 <span data-ttu-id="30038-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30038-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30038-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30038-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30038-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30038-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30038-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30038-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
