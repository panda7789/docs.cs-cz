---
title: CorDebugUnmappedStop – výčet
ms.date: 03/30/2017
api_name:
- CorDebugUnmappedStop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUnmappedStop
helpviewer_keywords:
- CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6f22c045be9af71644415ae3b6b5e64d3e399dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495432"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="afeff-102">CorDebugUnmappedStop – výčet</span><span class="sxs-lookup"><span data-stu-id="afeff-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="afeff-103">Určuje typ nenamapované kód, který můžete aktivovat zastavení provádění kódu pomocí krokovače.</span><span class="sxs-lookup"><span data-stu-id="afeff-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afeff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afeff-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="afeff-105">Členové</span><span class="sxs-lookup"><span data-stu-id="afeff-105">Members</span></span>  
  
|<span data-ttu-id="afeff-106">Člen</span><span class="sxs-lookup"><span data-stu-id="afeff-106">Member</span></span>|<span data-ttu-id="afeff-107">Popis</span><span class="sxs-lookup"><span data-stu-id="afeff-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="afeff-108">Není zastavit v libovolný typ nenamapované kódu.</span><span class="sxs-lookup"><span data-stu-id="afeff-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="afeff-109">Zastavte v kódu prologu.</span><span class="sxs-lookup"><span data-stu-id="afeff-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="afeff-110">Zastavení Kód epilogu.</span><span class="sxs-lookup"><span data-stu-id="afeff-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="afeff-111">Zastavte v kódu, který neobsahuje žádné informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="afeff-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="afeff-112">Zastavte v nenamapované kódu, který se nevejde do kódu prologu, epilogu, ne informace mapování nebo nespravované kategorie.</span><span class="sxs-lookup"><span data-stu-id="afeff-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="afeff-113">Zastavte v nespravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="afeff-113">Stop in unmanaged code.</span></span> <span data-ttu-id="afeff-114">Tato hodnota je platný pouze pro definiční ladění.</span><span class="sxs-lookup"><span data-stu-id="afeff-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="afeff-115">Zastavte ve všech typech nenamapované kódu.</span><span class="sxs-lookup"><span data-stu-id="afeff-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afeff-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="afeff-116">Remarks</span></span>  
 <span data-ttu-id="afeff-117">Použití [icordebugstepper::setunmappedstopmask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) metoda nastavit příznaky, které určují nenamapované kódu, ve kterém se zastaví krokovače.</span><span class="sxs-lookup"><span data-stu-id="afeff-117">Use the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afeff-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="afeff-118">Requirements</span></span>  
 <span data-ttu-id="afeff-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afeff-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afeff-120">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="afeff-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="afeff-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="afeff-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afeff-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afeff-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afeff-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="afeff-123">See also</span></span>
- [<span data-ttu-id="afeff-124">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="afeff-124">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
