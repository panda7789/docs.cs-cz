---
title: "CorDebugUnmappedStop – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugUnmappedStop
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugUnmappedStop
helpviewer_keywords: CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e75c827533a921c4cab31b2e8b0996dffa532fe2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="0dc22-102">CorDebugUnmappedStop – výčet</span><span class="sxs-lookup"><span data-stu-id="0dc22-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="0dc22-103">Určuje typ nenamapovaný kód, který můžete aktivovat zastavení provádění kódu pomocí krokovače.</span><span class="sxs-lookup"><span data-stu-id="0dc22-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dc22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0dc22-104">Syntax</span></span>  
  
```  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a><span data-ttu-id="0dc22-105">Členové</span><span class="sxs-lookup"><span data-stu-id="0dc22-105">Members</span></span>  
  
|<span data-ttu-id="0dc22-106">Člen</span><span class="sxs-lookup"><span data-stu-id="0dc22-106">Member</span></span>|<span data-ttu-id="0dc22-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0dc22-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="0dc22-108">Není zastavit v libovolný typ nenamapovaný kódu.</span><span class="sxs-lookup"><span data-stu-id="0dc22-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="0dc22-109">Zastavte v kódu prologu.</span><span class="sxs-lookup"><span data-stu-id="0dc22-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="0dc22-110">Zastavte v epilogu kódu.</span><span class="sxs-lookup"><span data-stu-id="0dc22-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="0dc22-111">Zastavte v kódu, který neobsahuje žádné informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="0dc22-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="0dc22-112">Zastavte v nenamapovaný kód, který se nevejde do prologu epilogu, ne informace mapování nebo nespravované kategorie.</span><span class="sxs-lookup"><span data-stu-id="0dc22-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="0dc22-113">Zastavte v nespravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="0dc22-113">Stop in unmanaged code.</span></span> <span data-ttu-id="0dc22-114">Tato hodnota je platný pouze s spolupráce ladění.</span><span class="sxs-lookup"><span data-stu-id="0dc22-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="0dc22-115">Zastavte všechny typy nenamapovaný kódu.</span><span class="sxs-lookup"><span data-stu-id="0dc22-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0dc22-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0dc22-116">Remarks</span></span>  
 <span data-ttu-id="0dc22-117">Použití [icordebugstepper::setunmappedstopmask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) metodu a nastavit příznaky, které zadejte kód nenamapovaný, ve kterém krokovač zastaví.</span><span class="sxs-lookup"><span data-stu-id="0dc22-117">Use the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dc22-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0dc22-118">Requirements</span></span>  
 <span data-ttu-id="0dc22-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0dc22-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dc22-120">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0dc22-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0dc22-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0dc22-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0dc22-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dc22-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dc22-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="0dc22-123">See Also</span></span>  
 [<span data-ttu-id="0dc22-124">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="0dc22-124">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
