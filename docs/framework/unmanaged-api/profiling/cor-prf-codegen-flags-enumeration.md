---
title: COR_PRF_CODEGEN_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_CODEGEN_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODEGEN_FLAGS
helpviewer_keywords:
- COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 321318b63368ed6e57d235cf97d94485352f8686
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211358"
---
# <a name="corprfcodegenflags-enumeration"></a><span data-ttu-id="4a302-102">COR_PRF_CODEGEN_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="4a302-102">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>
<span data-ttu-id="4a302-103">Definuje příznaky generování kódu, které lze nastavit [icorprofilerfunctioncontrol::setcodegenflags –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="4a302-103">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a302-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a302-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="4a302-105">Členové</span><span class="sxs-lookup"><span data-stu-id="4a302-105">Members</span></span>  
  
|<span data-ttu-id="4a302-106">Člen</span><span class="sxs-lookup"><span data-stu-id="4a302-106">Member</span></span>|<span data-ttu-id="4a302-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4a302-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="4a302-108">Žádné funkce nebude vložena do těla této funkce.</span><span class="sxs-lookup"><span data-stu-id="4a302-108">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="4a302-109">Však může být vloženy do jeho volající samotné funkce.</span><span class="sxs-lookup"><span data-stu-id="4a302-109">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="4a302-110">Tělo této funkce vypne všechny optimalizace.</span><span class="sxs-lookup"><span data-stu-id="4a302-110">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="4a302-111">Ale samotné funkce může být stále vloženy do jeho volající.</span><span class="sxs-lookup"><span data-stu-id="4a302-111">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a302-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a302-112">Remarks</span></span>  
 <span data-ttu-id="4a302-113">`COR_PRF_CODEGEN_FLAGS` Výčet je používán [icorprofilerfunctioncontrol::setcodegenflags –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) způsob povolení profileru, chcete-li řídit generování kódu pro funkci překompilován JIT.</span><span class="sxs-lookup"><span data-stu-id="4a302-113">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a302-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a302-114">Requirements</span></span>  
 <span data-ttu-id="4a302-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a302-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a302-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4a302-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4a302-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a302-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4a302-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="4a302-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4a302-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a302-119">See also</span></span>

- [<span data-ttu-id="4a302-120">Profilace výčtů</span><span class="sxs-lookup"><span data-stu-id="4a302-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
