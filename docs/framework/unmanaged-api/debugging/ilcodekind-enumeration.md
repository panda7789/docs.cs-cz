---
title: Výčet ILCodeKind
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a02c26b72fc7039a5050ee369043f081c32cd7ec
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869977"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="3d7e8-102">Výčet ILCodeKind</span><span class="sxs-lookup"><span data-stu-id="3d7e8-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="3d7e8-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="3d7e8-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="3d7e8-104">Obsahuje hodnoty, které určují, jestli je přístup k lokálním proměnným nebo kód přidaný v profileru instrumentace ReJIT ladicí program.</span><span class="sxs-lookup"><span data-stu-id="3d7e8-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d7e8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d7e8-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="3d7e8-106">Členové</span><span class="sxs-lookup"><span data-stu-id="3d7e8-106">Members</span></span>  
  
|<span data-ttu-id="3d7e8-107">Název členu</span><span class="sxs-lookup"><span data-stu-id="3d7e8-107">Member name</span></span>|<span data-ttu-id="3d7e8-108">Popis</span><span class="sxs-lookup"><span data-stu-id="3d7e8-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="3d7e8-109">Ladicí program nemá přístup k informacím z ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="3d7e8-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="3d7e8-110">Ladicí program má přístup k informacím z ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="3d7e8-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d7e8-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d7e8-111">Remarks</span></span>  
 <span data-ttu-id="3d7e8-112">Člen `ILCodeKind` výčet může být předán [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) a [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) metody k určení, zda ladicí program má přístup k proměnným, které jsou přidány v profileru Instrumentace ReJIT a [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) metodou ke zjištění, jestli můžete přistupovat k ladicímu programu instrumentována IL.</span><span class="sxs-lookup"><span data-stu-id="3d7e8-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d7e8-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3d7e8-113">Requirements</span></span>  
 <span data-ttu-id="3d7e8-114">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d7e8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d7e8-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d7e8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d7e8-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d7e8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d7e8-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d7e8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d7e8-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d7e8-118">See Also</span></span>  
 [<span data-ttu-id="3d7e8-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="3d7e8-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="3d7e8-120">ICorDebugILFrame4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3d7e8-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="3d7e8-121">ReJIT: Nepředstavuje Průvodce</span><span class="sxs-lookup"><span data-stu-id="3d7e8-121">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
