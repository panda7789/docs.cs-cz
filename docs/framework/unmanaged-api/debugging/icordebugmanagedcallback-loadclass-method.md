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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 39ce3e8329c4ff32b55341127f68a800246677df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169946"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="862b8-102">ICorDebugManagedCallback::LoadClass – metoda</span><span class="sxs-lookup"><span data-stu-id="862b8-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="862b8-103">Načtení třídy upozorní ladicí program.</span><span class="sxs-lookup"><span data-stu-id="862b8-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="862b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="862b8-104">Syntax</span></span>  
  
```  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="862b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="862b8-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="862b8-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, do kterého se načetl třídy.</span><span class="sxs-lookup"><span data-stu-id="862b8-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="862b8-107">[in] Ukazatel na objekt ICorDebugClass, který představuje třídu.</span><span class="sxs-lookup"><span data-stu-id="862b8-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="862b8-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="862b8-108">Remarks</span></span>  
 <span data-ttu-id="862b8-109">Toto zpětné volání dojde pouze v případě, že se povolila načítání třídy pro modul, který obsahuje třídu.</span><span class="sxs-lookup"><span data-stu-id="862b8-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="862b8-110">Načtení třídy je vždy povolena pro dynamické moduly.</span><span class="sxs-lookup"><span data-stu-id="862b8-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="862b8-111">`LoadClass` Zpětného volání obsahuje správný čas vytvořit vazbu zarážky na nově vygenerované třídy v dynamických modulech.</span><span class="sxs-lookup"><span data-stu-id="862b8-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="862b8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="862b8-112">Requirements</span></span>  
 <span data-ttu-id="862b8-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="862b8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="862b8-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="862b8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="862b8-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="862b8-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="862b8-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="862b8-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="862b8-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="862b8-117">See also</span></span>

- [<span data-ttu-id="862b8-118">UnloadClass – metoda</span><span class="sxs-lookup"><span data-stu-id="862b8-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="862b8-119">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="862b8-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
