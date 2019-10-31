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
ms.openlocfilehash: 98566176ff33000fc4b4587b5669a037c90268f5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139096"
---
# <a name="writeablemetadataupdatemode-enumeration"></a><span data-ttu-id="d5c1a-102">Výčet WriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="d5c1a-102">WriteableMetadataUpdateMode Enumeration</span></span>
<span data-ttu-id="d5c1a-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="d5c1a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d5c1a-104">Poskytuje hodnoty, které určují, zda mají být aktualizace metadat v paměti viditelné ladicímu programu.</span><span class="sxs-lookup"><span data-stu-id="d5c1a-104">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5c1a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5c1a-105">Syntax</span></span>  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a><span data-ttu-id="d5c1a-106">Členové</span><span class="sxs-lookup"><span data-stu-id="d5c1a-106">Members</span></span>  
  
|<span data-ttu-id="d5c1a-107">Název členu</span><span class="sxs-lookup"><span data-stu-id="d5c1a-107">Member name</span></span>|<span data-ttu-id="d5c1a-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d5c1a-108">Description</span></span>|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|<span data-ttu-id="d5c1a-109">Zachovat kompatibilitu s předchozími verzemi .NET Framework při zpřístupnění aktualizací v paměti na metadatech</span><span class="sxs-lookup"><span data-stu-id="d5c1a-109">Maintain compatibility with previous versions of the .NET Framework when making in-memory updates to metadata visible.</span></span> <span data-ttu-id="d5c1a-110">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="d5c1a-110">See the Remarks section for more information.</span></span>|  
|`AlwaysShowUpdates`|<span data-ttu-id="d5c1a-111">Zpřístupnit v paměti aktualizace metadat viditelných pro ladicí program.</span><span class="sxs-lookup"><span data-stu-id="d5c1a-111">Make in-memory updates to metadata visible to the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5c1a-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5c1a-112">Remarks</span></span>  
 <span data-ttu-id="d5c1a-113">Člen výčtu `WriteableMetadataUpdateMode` lze předat metodě [SetWriteableMetadataUpdateMode –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) a určit tak, zda mají být aktualizace v paměti metadaty v cílovém procesu viditelné ladicímu programu.</span><span class="sxs-lookup"><span data-stu-id="d5c1a-113">A member of the `WriteableMetadataUpdateMode` enumeration can be passed to the [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) method to control whether in-memory updates to metadata in the target process are visible to the debugger.</span></span>  
  
 <span data-ttu-id="d5c1a-114">Možnost `LegacyCompatPolicy` vynutila stejné chování jako ve verzích .NET Framework před 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="d5c1a-114">The `LegacyCompatPolicy` option enforces the same behavior as in versions of the .NET Framework before 4.5.2.</span></span> <span data-ttu-id="d5c1a-115">To často znamená, že metadata z aktualizací nejsou viditelná.</span><span class="sxs-lookup"><span data-stu-id="d5c1a-115">This often means that metadata from updates is not visible.</span></span> <span data-ttu-id="d5c1a-116">Nicméně volání na řadu metod ladění implicitně převede ladicí program, aby byly aktualizace viditelné.</span><span class="sxs-lookup"><span data-stu-id="d5c1a-116">However, calls to a number of debugging methods implicitly coerce the debugger to make updates visible.</span></span> <span data-ttu-id="d5c1a-117">Například pokud ladicí program projde [ICorDebugILFrame:: GetLocalVariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) index proměnné, který nebyl nalezen v původních metadatech metody, všechna metadata pro modul jsou aktualizována na snímek, který odpovídá aktuálnímu stavu procesu.</span><span class="sxs-lookup"><span data-stu-id="d5c1a-117">For example, if the debugger passes [ICorDebugILFrame::GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) the index of a variable not found in the method's original metadata, all metadata for the module is updated to a snapshot matching the current state of the process.</span></span> <span data-ttu-id="d5c1a-118">Jinými slovy, s možností `LegacyCompatPolicy`, ladicí program se může v závislosti na tom, jak používá jiné části nespravovaného rozhraní API pro ladění, zobrazovat žádná, některá nebo všechna dostupná aktualizace metadat.</span><span class="sxs-lookup"><span data-stu-id="d5c1a-118">In other words, with the `LegacyCompatPolicy` option, the debugger might see none, some, or all of the available metadata updates, depending on how it uses other parts of the unmanaged debugging API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5c1a-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5c1a-119">Requirements</span></span>  
 <span data-ttu-id="d5c1a-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5c1a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5c1a-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d5c1a-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5c1a-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d5c1a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5c1a-123">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5c1a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5c1a-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5c1a-124">See also</span></span>

- [<span data-ttu-id="d5c1a-125">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="d5c1a-125">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="d5c1a-126">SetWriteableMetadataUpdateMode – metoda</span><span class="sxs-lookup"><span data-stu-id="d5c1a-126">SetWriteableMetadataUpdateMode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
