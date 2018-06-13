---
title: COR_PRF_MISC – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_MISC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MISC
helpviewer_keywords:
- COR_PRF_MISC enumeration [.NET Framework profiling]
ms.assetid: 619bb5de-e309-48b6-a3af-32d935a0ff46
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c8f4cffd718fffa9145e1082092ecec45b80a2ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451055"
---
# <a name="corprfmisc-enumeration"></a><span data-ttu-id="26e22-102">COR_PRF_MISC – výčet</span><span class="sxs-lookup"><span data-stu-id="26e22-102">COR_PRF_MISC Enumeration</span></span>
<span data-ttu-id="26e22-103">Obsahuje konstantní hodnoty, které určují speciální identifikátory.</span><span class="sxs-lookup"><span data-stu-id="26e22-103">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26e22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26e22-104">Syntax</span></span>  
  
```  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="26e22-105">Členové</span><span class="sxs-lookup"><span data-stu-id="26e22-105">Members</span></span>  
  
|<span data-ttu-id="26e22-106">Člen</span><span class="sxs-lookup"><span data-stu-id="26e22-106">Member</span></span>|<span data-ttu-id="26e22-107">Popis</span><span class="sxs-lookup"><span data-stu-id="26e22-107">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="26e22-108">Výchozí identifikátor používané [icorprofilerinfo::getmoduleinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) pro modul, který ještě nebyl přidán do sestavení.</span><span class="sxs-lookup"><span data-stu-id="26e22-108">The default identifier used by [ICorProfilerInfo::GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="26e22-109">Identifikátor třídy výchozí globální konstanty, které nepatří do třídy.</span><span class="sxs-lookup"><span data-stu-id="26e22-109">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="26e22-110">Identifikátor výchozí modul pro globální objekty, které nepatří do modulu.</span><span class="sxs-lookup"><span data-stu-id="26e22-110">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="26e22-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="26e22-111">Requirements</span></span>  
 <span data-ttu-id="26e22-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26e22-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26e22-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="26e22-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="26e22-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26e22-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26e22-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26e22-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26e22-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="26e22-116">See Also</span></span>  
 [<span data-ttu-id="26e22-117">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="26e22-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
