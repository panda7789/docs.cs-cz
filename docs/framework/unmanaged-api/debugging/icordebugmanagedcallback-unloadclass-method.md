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
ms.openlocfilehash: a7b71170f58ddfe0295da28b8c9fc73286b074e6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212266"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="6c9d7-102">ICorDebugManagedCallback::UnloadClass – metoda</span><span class="sxs-lookup"><span data-stu-id="6c9d7-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="6c9d7-103">Oznamuje ladicímu programu, že je třída uvolňována.</span><span class="sxs-lookup"><span data-stu-id="6c9d7-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c9d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c9d7-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c9d7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c9d7-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="6c9d7-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující třídu.</span><span class="sxs-lookup"><span data-stu-id="6c9d7-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="6c9d7-107">pro Ukazatel na objekt ICorDebugClass, který představuje třídu.</span><span class="sxs-lookup"><span data-stu-id="6c9d7-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c9d7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c9d7-108">Remarks</span></span>  
 <span data-ttu-id="6c9d7-109">Po tomto volání by neměl být odkazováno na třídu.</span><span class="sxs-lookup"><span data-stu-id="6c9d7-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c9d7-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6c9d7-110">Requirements</span></span>  
 <span data-ttu-id="6c9d7-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c9d7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c9d7-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6c9d7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c9d7-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6c9d7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c9d7-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c9d7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c9d7-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c9d7-115">See also</span></span>

- [<span data-ttu-id="6c9d7-116">LoadClass – metoda</span><span class="sxs-lookup"><span data-stu-id="6c9d7-116">LoadClass Method</span></span>](icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="6c9d7-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c9d7-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
