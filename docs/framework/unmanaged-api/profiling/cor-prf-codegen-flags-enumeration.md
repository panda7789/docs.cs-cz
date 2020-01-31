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
ms.openlocfilehash: 4dd4e39c9092d018f13e3bd2822e9492d71141ad
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867292"
---
# <a name="cor_prf_codegen_flags-enumeration"></a><span data-ttu-id="02036-102">COR_PRF_CODEGEN_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="02036-102">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>
<span data-ttu-id="02036-103">Definuje příznaky generování kódu, které lze nastavit pomocí metody [ICorProfilerFunctionControl:: SetCodegenFlags –](icorprofilerfunctioncontrol-setcodegenflags-method.md) .</span><span class="sxs-lookup"><span data-stu-id="02036-103">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02036-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02036-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="02036-105">Členové</span><span class="sxs-lookup"><span data-stu-id="02036-105">Members</span></span>  
  
|<span data-ttu-id="02036-106">Člen</span><span class="sxs-lookup"><span data-stu-id="02036-106">Member</span></span>|<span data-ttu-id="02036-107">Popis</span><span class="sxs-lookup"><span data-stu-id="02036-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="02036-108">Do těla této funkce nebudou vloženy žádné funkce.</span><span class="sxs-lookup"><span data-stu-id="02036-108">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="02036-109">Samotná funkce však může být vložena do svých volajících.</span><span class="sxs-lookup"><span data-stu-id="02036-109">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="02036-110">Všechny optimalizace budou zakázány pro tělo této funkce.</span><span class="sxs-lookup"><span data-stu-id="02036-110">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="02036-111">Samotná funkce však může být stále vložena do svých volajících.</span><span class="sxs-lookup"><span data-stu-id="02036-111">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02036-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="02036-112">Remarks</span></span>  
 <span data-ttu-id="02036-113">`COR_PRF_CODEGEN_FLAGS` výčet používá metoda [ICorProfilerFunctionControl:: SetCodegenFlags –](icorprofilerfunctioncontrol-setcodegenflags-method.md) , která umožňuje profileru řídit generování kódu pro funkci Rekompilované JIT.</span><span class="sxs-lookup"><span data-stu-id="02036-113">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02036-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="02036-114">Requirements</span></span>  
 <span data-ttu-id="02036-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02036-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02036-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="02036-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="02036-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="02036-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02036-118">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02036-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02036-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02036-119">See also</span></span>

- [<span data-ttu-id="02036-120">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="02036-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
