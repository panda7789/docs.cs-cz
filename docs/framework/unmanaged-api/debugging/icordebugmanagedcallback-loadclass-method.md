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
ms.openlocfilehash: cc5a2e1de79d6ba04ff3bf2bf86e0cb7ce9a5c0b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788381"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="5fcbe-102">ICorDebugManagedCallback::LoadClass – metoda</span><span class="sxs-lookup"><span data-stu-id="5fcbe-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="5fcbe-103">Oznamuje ladicímu programu, že byla načtena třída.</span><span class="sxs-lookup"><span data-stu-id="5fcbe-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fcbe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fcbe-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fcbe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5fcbe-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5fcbe-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, do které byla třída načtena.</span><span class="sxs-lookup"><span data-stu-id="5fcbe-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="5fcbe-107">pro Ukazatel na objekt ICorDebugClass, který představuje třídu.</span><span class="sxs-lookup"><span data-stu-id="5fcbe-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fcbe-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5fcbe-108">Remarks</span></span>  
 <span data-ttu-id="5fcbe-109">Toto zpětné volání nastane pouze v případě, že bylo povoleno načítání tříd pro modul, který obsahuje třídu.</span><span class="sxs-lookup"><span data-stu-id="5fcbe-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="5fcbe-110">Načítání tříd je vždy povoleno pro dynamické moduly.</span><span class="sxs-lookup"><span data-stu-id="5fcbe-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="5fcbe-111">Zpětné volání `LoadClass` poskytuje vhodný čas pro svázání zarážek s nově vygenerovanými třídami v dynamických modulech.</span><span class="sxs-lookup"><span data-stu-id="5fcbe-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fcbe-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5fcbe-112">Requirements</span></span>  
 <span data-ttu-id="5fcbe-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fcbe-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fcbe-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5fcbe-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fcbe-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5fcbe-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fcbe-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fcbe-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fcbe-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5fcbe-117">See also</span></span>

- [<span data-ttu-id="5fcbe-118">UnloadClass – metoda</span><span class="sxs-lookup"><span data-stu-id="5fcbe-118">UnloadClass Method</span></span>](icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="5fcbe-119">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5fcbe-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
