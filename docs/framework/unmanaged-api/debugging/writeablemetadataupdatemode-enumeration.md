---
title: "Výčet WriteableMetadataUpdateMode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- WriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6758f4d3-6bc7-4c99-8582-e9be00566784
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b32eca0bec61e6c7b6fcf83bb05650c30c2f9f16
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="writeablemetadataupdatemode-enumeration"></a><span data-ttu-id="0d5ba-102">Výčet WriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="0d5ba-102">WriteableMetadataUpdateMode Enumeration</span></span>
<span data-ttu-id="0d5ba-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="0d5ba-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="0d5ba-104">Obsahuje hodnoty, které určují, zda jsou viditelné pro ladicí program aktualizace v paměti pro metadata.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-104">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d5ba-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d5ba-105">Syntax</span></span>  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a><span data-ttu-id="0d5ba-106">Členové</span><span class="sxs-lookup"><span data-stu-id="0d5ba-106">Members</span></span>  
  
|<span data-ttu-id="0d5ba-107">Název členu</span><span class="sxs-lookup"><span data-stu-id="0d5ba-107">Member name</span></span>|<span data-ttu-id="0d5ba-108">Popis</span><span class="sxs-lookup"><span data-stu-id="0d5ba-108">Description</span></span>|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|<span data-ttu-id="0d5ba-109">Zachování kompatibility s předchozími verzemi rozhraní .NET Framework při provádění aktualizací v paměti metadata viditelné.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-109">Maintain compatibility with previous versions of the .NET Framework when making in-memory updates to metadata visible.</span></span> <span data-ttu-id="0d5ba-110">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-110">See the Remarks section for more information.</span></span>|  
|`AlwaysShowUpdates`|<span data-ttu-id="0d5ba-111">Zpřístupněte aktualizace v paměti k metadatům pro ladicí program.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-111">Make in-memory updates to metadata visible to the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d5ba-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d5ba-112">Remarks</span></span>  
 <span data-ttu-id="0d5ba-113">Člen `WriteableMetadataUpdateMode` výčtu se dá předat do [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) metoda řídit, jestli v paměti aktualizace metadat v tento cílový proces jsou viditelné pro ladicí program.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-113">A member of the `WriteableMetadataUpdateMode` enumeration can be passed to the [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) method to control whether in-memory updates to metadata in the target process are visible to the debugger.</span></span>  
  
 <span data-ttu-id="0d5ba-114">`LegacyCompatPolicy` Možnost vynucuje stejné chování jako verze rozhraní .NET Framework před 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-114">The `LegacyCompatPolicy` option enforces the same behavior as in versions of the .NET Framework before 4.5.2.</span></span> <span data-ttu-id="0d5ba-115">Často to znamená, že metadata z webu aktualizace od není viditelná.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-115">This often means that metadata from updates is not visible.</span></span> <span data-ttu-id="0d5ba-116">Volání metody, ladění ale coerce implicitně ladicí program ke zviditelnění aktualizace.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-116">However, calls to a number of debugging methods implicitly coerce the debugger to make updates visible.</span></span> <span data-ttu-id="0d5ba-117">Například v případě úspěšného ladicího programu [icordebugilframe::getlocalvariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) index proměnné nebyla nalezena v metody původní metadata, všechna metadata pro modul se aktualizuje na snímku odpovídající aktuální stav proces.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-117">For example, if the debugger passes [ICorDebugILFrame::GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) the index of a variable not found in the method's original metadata, all metadata for the module is updated to a snapshot matching the current state of the process.</span></span> <span data-ttu-id="0d5ba-118">Jinými slovy, pomocí `LegacyCompatPolicy` možnost ladicího programu setkat none, některé nebo všechny aktualizace k dispozici metadata, v závislosti na tom, jak ji používá dalších částí nespravovaného rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="0d5ba-118">In other words, with the `LegacyCompatPolicy` option, the debugger might see none, some, or all of the available metadata updates, depending on how it uses other parts of the unmanaged debugging API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d5ba-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0d5ba-119">Requirements</span></span>  
 <span data-ttu-id="0d5ba-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d5ba-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d5ba-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d5ba-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d5ba-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d5ba-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d5ba-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d5ba-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d5ba-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d5ba-124">See Also</span></span>  
 [<span data-ttu-id="0d5ba-125">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="0d5ba-125">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="0d5ba-126">SetWriteableMetadataUpdateMode – metoda</span><span class="sxs-lookup"><span data-stu-id="0d5ba-126">SetWriteableMetadataUpdateMode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
