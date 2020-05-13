---
title: ICorDebugManagedCallback::NameChange – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
ms.openlocfilehash: 48bfce9966ff12fe1b425fbcd9a81860628a54e6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212669"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="3a9aa-102">ICorDebugManagedCallback::NameChange – metoda</span><span class="sxs-lookup"><span data-stu-id="3a9aa-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="3a9aa-103">Oznamuje ladicímu programu, že došlo ke změně názvu domény aplikace nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="3a9aa-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a9aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a9aa-104">Syntax</span></span>  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a9aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a9aa-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="3a9aa-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, která buď změnila název, nebo obsahuje vlákno, které má změnu názvu.</span><span class="sxs-lookup"><span data-stu-id="3a9aa-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="3a9aa-107">pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, které má změnu názvu.</span><span class="sxs-lookup"><span data-stu-id="3a9aa-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a9aa-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a9aa-108">Requirements</span></span>  
 <span data-ttu-id="3a9aa-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a9aa-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a9aa-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3a9aa-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a9aa-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3a9aa-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a9aa-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a9aa-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a9aa-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a9aa-113">See also</span></span>

- [<span data-ttu-id="3a9aa-114">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a9aa-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
