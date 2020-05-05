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
ms.openlocfilehash: 772f1f0dee260ad3752b2f89e5fbe0d6bc27b87b
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795648"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="b72ee-102">CorDebugUnmappedStop – výčet</span><span class="sxs-lookup"><span data-stu-id="b72ee-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="b72ee-103">Určuje typ nemapovaného kódu, který může aktivovat zastavení při provádění kódu stepper.</span><span class="sxs-lookup"><span data-stu-id="b72ee-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b72ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b72ee-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="b72ee-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b72ee-105">Members</span></span>  
  
|<span data-ttu-id="b72ee-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b72ee-106">Member</span></span>|<span data-ttu-id="b72ee-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b72ee-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="b72ee-108">Nezastaví žádný typ nemapovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="b72ee-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="b72ee-109">Zastavit v kódu prologu.</span><span class="sxs-lookup"><span data-stu-id="b72ee-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="b72ee-110">Zastavit v kódu epilogu</span><span class="sxs-lookup"><span data-stu-id="b72ee-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="b72ee-111">Zastavit v kódu, který nemá žádné informace o mapování.</span><span class="sxs-lookup"><span data-stu-id="b72ee-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="b72ee-112">Zastavit v nemapovaném kódu, který se nevejde do prologu, epilogu, žádného mapování-informace nebo nespravované kategorie.</span><span class="sxs-lookup"><span data-stu-id="b72ee-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="b72ee-113">Zastavit v nespravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="b72ee-113">Stop in unmanaged code.</span></span> <span data-ttu-id="b72ee-114">Tato hodnota je platná pouze při ladění vzájemné spolupráce.</span><span class="sxs-lookup"><span data-stu-id="b72ee-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="b72ee-115">Zastavte všechny typy nemapovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="b72ee-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b72ee-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b72ee-116">Remarks</span></span>  
 <span data-ttu-id="b72ee-117">Použijte metodu [ICorDebugStepper:: SetUnmappedStopMask –](icordebugstepper-setunmappedstopmask-method.md) pro nastavení příznaků, které určují Nemapovaný kód, ve kterém se stepper zastaví.</span><span class="sxs-lookup"><span data-stu-id="b72ee-117">Use the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b72ee-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b72ee-118">Requirements</span></span>  
 <span data-ttu-id="b72ee-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b72ee-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b72ee-120">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b72ee-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b72ee-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b72ee-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b72ee-122">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b72ee-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b72ee-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="b72ee-123">See also</span></span>

- [<span data-ttu-id="b72ee-124">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="b72ee-124">Debugging Enumerations</span></span>](debugging-enumerations.md)
