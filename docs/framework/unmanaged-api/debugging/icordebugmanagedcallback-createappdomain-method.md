---
title: ICorDebugManagedCallback::CreateAppDomain – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateAppDomain
helpviewer_keywords:
- CreateAppDomain method [.NET Framework debugging]
- ICorDebugManagedCallback::CreateAppDomain method [.NET Framework debugging]
ms.assetid: 48d410d7-6749-4125-a8fd-f9562c7088e9
topic_type:
- apiref
ms.openlocfilehash: 35ea69d32ee9b994cc0bf91339c798edcd472f44
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788418"
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a><span data-ttu-id="29ec5-102">ICorDebugManagedCallback::CreateAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="29ec5-102">ICorDebugManagedCallback::CreateAppDomain Method</span></span>
<span data-ttu-id="29ec5-103">Oznamuje ladicímu programu, že byla vytvořena doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="29ec5-103">Notifies the debugger that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ec5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29ec5-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29ec5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29ec5-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="29ec5-106">pro Ukazatel na objekt ICorDebugProcess, který představuje proces, ve kterém byla vytvořena doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="29ec5-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the application domain was created.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="29ec5-107">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, která byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="29ec5-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has been created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29ec5-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29ec5-108">Requirements</span></span>  
 <span data-ttu-id="29ec5-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29ec5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29ec5-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="29ec5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29ec5-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="29ec5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29ec5-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29ec5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ec5-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29ec5-113">See also</span></span>

- [<span data-ttu-id="29ec5-114">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="29ec5-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
