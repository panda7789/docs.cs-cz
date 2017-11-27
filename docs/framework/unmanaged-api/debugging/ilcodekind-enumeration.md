---
title: "Výčet ILCodeKind"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ILCodeKind
api_location: mscordbi.dll
api_type: COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61fd5ad93c198000556e8e0be3a278a842ab5716
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="4176e-102">Výčet ILCodeKind</span><span class="sxs-lookup"><span data-stu-id="4176e-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="4176e-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="4176e-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="4176e-104">Obsahuje hodnoty, které určují, jestli je přístup k místní proměnné nebo kódu přidaném v ReJIT instrumentace profileru ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="4176e-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4176e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4176e-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="4176e-106">Členové</span><span class="sxs-lookup"><span data-stu-id="4176e-106">Members</span></span>  
  
|<span data-ttu-id="4176e-107">Název členu</span><span class="sxs-lookup"><span data-stu-id="4176e-107">Member name</span></span>|<span data-ttu-id="4176e-108">Popis</span><span class="sxs-lookup"><span data-stu-id="4176e-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="4176e-109">Ladicí program nemá přístup k informacím z ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="4176e-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="4176e-110">Ladicí program má přístup k informacím z ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="4176e-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4176e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4176e-111">Remarks</span></span>  
 <span data-ttu-id="4176e-112">Člen `ILCodeKind` výčtu se dá předat do [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) a [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) metody k určení, jestli ladicího programu můžete získat přístup k proměnné přidali v profileru Instrumentace ReJIT a [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) IL instrumentovány metoda k určení, jestli má přístup k ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="4176e-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4176e-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4176e-113">Requirements</span></span>  
 <span data-ttu-id="4176e-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4176e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4176e-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4176e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4176e-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4176e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4176e-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4176e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4176e-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="4176e-118">See Also</span></span>  
 [<span data-ttu-id="4176e-119">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="4176e-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="4176e-120">Rozhraní ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="4176e-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="4176e-121">ReJIT: Postupy: Průvodce</span><span class="sxs-lookup"><span data-stu-id="4176e-121">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
