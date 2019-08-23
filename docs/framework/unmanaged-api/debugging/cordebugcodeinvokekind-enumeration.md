---
title: Výčet CorDebugCodeInvokeKind
ms.date: 03/30/2017
api_name:
- CorDebugCodeInvokeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fa8de1a561e59e00d5bd9e78172d78b417aeff0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951970"
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="e1182-102">Výčet CorDebugCodeInvokeKind</span><span class="sxs-lookup"><span data-stu-id="e1182-102">CorDebugCodeInvokeKind Enumeration</span></span>
<span data-ttu-id="e1182-103">Popisuje, jak exportovaný funkce vyvolá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="e1182-103">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1182-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1182-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="e1182-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e1182-105">Members</span></span>  
  
|<span data-ttu-id="e1182-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e1182-106">Member</span></span>|<span data-ttu-id="e1182-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e1182-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="e1182-108">Pokud je v této metodě vyvolán nějaký spravovaný kód, bude muset být umístěn pomocí explicitních událostí nebo zarážek později.</span><span class="sxs-lookup"><span data-stu-id="e1182-108">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="e1182-109">--nebo--</span><span class="sxs-lookup"><span data-stu-id="e1182-109">--or--</span></span><br /><br /> <span data-ttu-id="e1182-110">Omlouváme se, ale může se stát, že tato metoda volá jenom některé spravované kódy, protože neexistuje žádný snadný způsob, jak ji zastavit.</span><span class="sxs-lookup"><span data-stu-id="e1182-110">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="e1182-111">--nebo--</span><span class="sxs-lookup"><span data-stu-id="e1182-111">--or--</span></span><br /><br /> <span data-ttu-id="e1182-112">Metoda nikdy nemůže vyvolat spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="e1182-112">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="e1182-113">Tato metoda vyvolá spravovaný kód prostřednictvím návratové instrukce.</span><span class="sxs-lookup"><span data-stu-id="e1182-113">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="e1182-114">Krokování by mělo být doručeno do dalšího spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="e1182-114">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="e1182-115">Tato metoda vyvolá spravovaný kód prostřednictvím volání tail.</span><span class="sxs-lookup"><span data-stu-id="e1182-115">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="e1182-116">Do spravovaného kódu by měly být doručeny jednoduché krokování a krokování prostřednictvím jakýchkoli instrukcí volání.</span><span class="sxs-lookup"><span data-stu-id="e1182-116">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1182-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e1182-117">Remarks</span></span>  
 <span data-ttu-id="e1182-118">Tento výčet používá metoda [ICorDebugProcess6:: GetExportStepInfo –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) k poskytnutí informací o prokrokování prostřednictvím spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="e1182-118">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1182-119">Tento výčet je určený pro použití pouze v .NET Nativech scénářích ladění.</span><span class="sxs-lookup"><span data-stu-id="e1182-119">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1182-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1182-120">Requirements</span></span>  
 <span data-ttu-id="e1182-121">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1182-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1182-122">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e1182-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1182-123">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1182-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1182-124">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1182-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1182-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1182-125">See also</span></span>

- [<span data-ttu-id="e1182-126">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="e1182-126">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="e1182-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="e1182-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
