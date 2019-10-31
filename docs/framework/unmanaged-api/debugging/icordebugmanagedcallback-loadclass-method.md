---
title: ICorDebugManagedCallback::LoadClass – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
ms.openlocfilehash: d23b695550c8444264934f7aca4fa185064e89c5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130731"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="bdc30-102">ICorDebugManagedCallback::LoadClass – metoda</span><span class="sxs-lookup"><span data-stu-id="bdc30-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="bdc30-103">Oznamuje ladicímu programu, že byla načtena třída.</span><span class="sxs-lookup"><span data-stu-id="bdc30-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdc30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdc30-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdc30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bdc30-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="bdc30-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, do které byla třída načtena.</span><span class="sxs-lookup"><span data-stu-id="bdc30-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="bdc30-107">pro Ukazatel na objekt ICorDebugClass, který představuje třídu.</span><span class="sxs-lookup"><span data-stu-id="bdc30-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdc30-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bdc30-108">Remarks</span></span>  
 <span data-ttu-id="bdc30-109">Toto zpětné volání nastane pouze v případě, že bylo povoleno načítání tříd pro modul, který obsahuje třídu.</span><span class="sxs-lookup"><span data-stu-id="bdc30-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="bdc30-110">Načítání tříd je vždy povoleno pro dynamické moduly.</span><span class="sxs-lookup"><span data-stu-id="bdc30-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="bdc30-111">Zpětné volání `LoadClass` poskytuje vhodný čas pro svázání zarážek s nově vygenerovanými třídami v dynamických modulech.</span><span class="sxs-lookup"><span data-stu-id="bdc30-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdc30-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bdc30-112">Requirements</span></span>  
 <span data-ttu-id="bdc30-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdc30-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdc30-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bdc30-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdc30-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bdc30-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdc30-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdc30-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdc30-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bdc30-117">See also</span></span>

- [<span data-ttu-id="bdc30-118">UnloadClass – metoda</span><span class="sxs-lookup"><span data-stu-id="bdc30-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="bdc30-119">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bdc30-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
