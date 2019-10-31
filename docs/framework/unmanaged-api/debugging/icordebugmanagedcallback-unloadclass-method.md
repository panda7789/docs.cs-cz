---
title: ICorDebugManagedCallback::UnloadClass – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
ms.openlocfilehash: e2550320494b9ba43947c3176788042f5c2e6ad5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130621"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="ac228-102">ICorDebugManagedCallback::UnloadClass – metoda</span><span class="sxs-lookup"><span data-stu-id="ac228-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="ac228-103">Oznamuje ladicímu programu, že je třída uvolňována.</span><span class="sxs-lookup"><span data-stu-id="ac228-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac228-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac228-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac228-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac228-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="ac228-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující třídu.</span><span class="sxs-lookup"><span data-stu-id="ac228-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="ac228-107">pro Ukazatel na objekt ICorDebugClass, který představuje třídu.</span><span class="sxs-lookup"><span data-stu-id="ac228-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac228-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ac228-108">Remarks</span></span>  
 <span data-ttu-id="ac228-109">Po tomto volání by neměl být odkazováno na třídu.</span><span class="sxs-lookup"><span data-stu-id="ac228-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac228-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac228-110">Requirements</span></span>  
 <span data-ttu-id="ac228-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac228-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac228-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ac228-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac228-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ac228-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac228-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac228-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac228-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac228-115">See also</span></span>

- [<span data-ttu-id="ac228-116">LoadClass – metoda</span><span class="sxs-lookup"><span data-stu-id="ac228-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="ac228-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac228-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
