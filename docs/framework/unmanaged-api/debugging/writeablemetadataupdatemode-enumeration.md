---
title: Výčet WriteableMetadataUpdateMode
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62e4328b75a7f6fecc28cd620ec3ac18460316c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993444"
---
# <a name="writeablemetadataupdatemode-enumeration"></a><span data-ttu-id="29ee1-102">Výčet WriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="29ee1-102">WriteableMetadataUpdateMode Enumeration</span></span>
<span data-ttu-id="29ee1-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="29ee1-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="29ee1-104">Obsahuje hodnoty, které určují, jestli jsou viditelné pro ladicí program v paměti aktualizace metadat.</span><span class="sxs-lookup"><span data-stu-id="29ee1-104">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ee1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29ee1-105">Syntax</span></span>  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a><span data-ttu-id="29ee1-106">Členové</span><span class="sxs-lookup"><span data-stu-id="29ee1-106">Members</span></span>  
  
|<span data-ttu-id="29ee1-107">Název členu</span><span class="sxs-lookup"><span data-stu-id="29ee1-107">Member name</span></span>|<span data-ttu-id="29ee1-108">Popis</span><span class="sxs-lookup"><span data-stu-id="29ee1-108">Description</span></span>|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|<span data-ttu-id="29ee1-109">Zachování kompatibility s předchozími verzemi rozhraní .NET Framework při provádění aktualizací v paměti k metadatům viditelné.</span><span class="sxs-lookup"><span data-stu-id="29ee1-109">Maintain compatibility with previous versions of the .NET Framework when making in-memory updates to metadata visible.</span></span> <span data-ttu-id="29ee1-110">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="29ee1-110">See the Remarks section for more information.</span></span>|  
|`AlwaysShowUpdates`|<span data-ttu-id="29ee1-111">Zviditelnit v paměti aktualizace metadat k ladicímu programu.</span><span class="sxs-lookup"><span data-stu-id="29ee1-111">Make in-memory updates to metadata visible to the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29ee1-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29ee1-112">Remarks</span></span>  
 <span data-ttu-id="29ee1-113">Člen `WriteableMetadataUpdateMode` výčet může být předán [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) metoda řídit, jestli v paměti aktualizace metadat v cílovém procesu jsou viditelné pro ladicí program.</span><span class="sxs-lookup"><span data-stu-id="29ee1-113">A member of the `WriteableMetadataUpdateMode` enumeration can be passed to the [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) method to control whether in-memory updates to metadata in the target process are visible to the debugger.</span></span>  
  
 <span data-ttu-id="29ee1-114">`LegacyCompatPolicy` Možnost vynucuje stejné chování jako verze rozhraní .NET Framework před 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="29ee1-114">The `LegacyCompatPolicy` option enforces the same behavior as in versions of the .NET Framework before 4.5.2.</span></span> <span data-ttu-id="29ee1-115">To často znamená, že metadata z webu aktualizace od není viditelný.</span><span class="sxs-lookup"><span data-stu-id="29ee1-115">This often means that metadata from updates is not visible.</span></span> <span data-ttu-id="29ee1-116">Volání na počet ladění metody však implicitně převedeno ladicí program ke zviditelnění aktualizace.</span><span class="sxs-lookup"><span data-stu-id="29ee1-116">However, calls to a number of debugging methods implicitly coerce the debugger to make updates visible.</span></span> <span data-ttu-id="29ee1-117">Například, pokud ladicí program projde [icordebugilframe::getlocalvariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) index proměnná se nenašla v metadatech původní metody, všechna metadata modulu je aktualizovaná na snímek aktuálního stavu odpovídajících proces.</span><span class="sxs-lookup"><span data-stu-id="29ee1-117">For example, if the debugger passes [ICorDebugILFrame::GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) the index of a variable not found in the method's original metadata, all metadata for the module is updated to a snapshot matching the current state of the process.</span></span> <span data-ttu-id="29ee1-118">Jinými slovy, se `LegacyCompatPolicy` možnost, ladicí program může zobrazit, none, některé nebo všechny aktualizace metadat k dispozici, v závislosti na tom, jak používá jiné části nespravované ladění rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="29ee1-118">In other words, with the `LegacyCompatPolicy` option, the debugger might see none, some, or all of the available metadata updates, depending on how it uses other parts of the unmanaged debugging API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29ee1-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29ee1-119">Requirements</span></span>  
 <span data-ttu-id="29ee1-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29ee1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29ee1-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29ee1-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29ee1-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29ee1-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29ee1-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29ee1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ee1-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29ee1-124">See also</span></span>

- [<span data-ttu-id="29ee1-125">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="29ee1-125">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="29ee1-126">SetWriteableMetadataUpdateMode – metoda</span><span class="sxs-lookup"><span data-stu-id="29ee1-126">SetWriteableMetadataUpdateMode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
