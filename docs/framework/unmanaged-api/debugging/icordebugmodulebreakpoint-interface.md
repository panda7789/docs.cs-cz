---
title: ICorDebugModuleBreakpoint – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint
helpviewer_keywords:
- ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6a43a264fcaa94ce4e629d8db504e9d416f6b89
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179709"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="c876b-102">ICorDebugModuleBreakpoint – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c876b-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="c876b-103">Poskytuje přístup k určitým modulům.</span><span class="sxs-lookup"><span data-stu-id="c876b-103">Provides access to specific modules.</span></span> <span data-ttu-id="c876b-104">Toto rozhraní je podtřídou třídy icordebugbreakpoint – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c876b-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c876b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c876b-105">Methods</span></span>  
  
|<span data-ttu-id="c876b-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c876b-106">Method</span></span>|<span data-ttu-id="c876b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c876b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c876b-108">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="c876b-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="c876b-109">Získá ukazatel rozhraní k ICorDebugModule, který odkazuje na modul, kde je zarážka nastavena.</span><span class="sxs-lookup"><span data-stu-id="c876b-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c876b-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c876b-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c876b-111">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="c876b-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c876b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c876b-112">Requirements</span></span>  
 <span data-ttu-id="c876b-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c876b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c876b-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c876b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c876b-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c876b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c876b-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c876b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c876b-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c876b-117">See also</span></span>

- [<span data-ttu-id="c876b-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c876b-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
