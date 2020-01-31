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
ms.openlocfilehash: 23e168b0f322a580917c3fcfcb767a7d4d4628f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793884"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="7aa5d-102">CorDebugUnmappedStop – výčet</span><span class="sxs-lookup"><span data-stu-id="7aa5d-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="7aa5d-103">Určuje typ nemapovaného kódu, který může aktivovat zastavení při provádění kódu stepper.</span><span class="sxs-lookup"><span data-stu-id="7aa5d-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aa5d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7aa5d-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="7aa5d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7aa5d-105">Members</span></span>  
  
|<span data-ttu-id="7aa5d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7aa5d-106">Member</span></span>|<span data-ttu-id="7aa5d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7aa5d-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="7aa5d-108">Nezastaví žádný typ nemapovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="7aa5d-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="7aa5d-109">Zastavit v kódu prologu.</span><span class="sxs-lookup"><span data-stu-id="7aa5d-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="7aa5d-110">Zastavit v kódu epilogu</span><span class="sxs-lookup"><span data-stu-id="7aa5d-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="7aa5d-111">Zastavit v kódu, který nemá žádné informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="7aa5d-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="7aa5d-112">Zastavit v nemapovaném kódu, který se nevejde do prologu, epilogu, žádného mapování-informace nebo nespravované kategorie.</span><span class="sxs-lookup"><span data-stu-id="7aa5d-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="7aa5d-113">Zastavit v nespravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="7aa5d-113">Stop in unmanaged code.</span></span> <span data-ttu-id="7aa5d-114">Tato hodnota je platná pouze při ladění vzájemné spolupráce.</span><span class="sxs-lookup"><span data-stu-id="7aa5d-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="7aa5d-115">Zastavte všechny typy nemapovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="7aa5d-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7aa5d-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7aa5d-116">Remarks</span></span>  
 <span data-ttu-id="7aa5d-117">Použijte metodu [ICorDebugStepper:: SetUnmappedStopMask –](icordebugstepper-setunmappedstopmask-method.md) pro nastavení příznaků, které určují Nemapovaný kód, ve kterém se stepper zastaví.</span><span class="sxs-lookup"><span data-stu-id="7aa5d-117">Use the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7aa5d-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7aa5d-118">Requirements</span></span>  
 <span data-ttu-id="7aa5d-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7aa5d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7aa5d-120">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7aa5d-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7aa5d-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7aa5d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7aa5d-122">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7aa5d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aa5d-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7aa5d-123">See also</span></span>

- [<span data-ttu-id="7aa5d-124">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="7aa5d-124">Debugging Enumerations</span></span>](debugging-enumerations.md)
