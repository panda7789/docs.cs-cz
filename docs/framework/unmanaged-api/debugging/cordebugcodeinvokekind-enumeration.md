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
ms.openlocfilehash: cc839e9b2a28dc428ae7cc87c9d080c4b7612a9d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098883"
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="e0495-102">Výčet CorDebugCodeInvokeKind</span><span class="sxs-lookup"><span data-stu-id="e0495-102">CorDebugCodeInvokeKind Enumeration</span></span>
<span data-ttu-id="e0495-103">Popisuje, jak exportovaný funkce vyvolá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="e0495-103">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0495-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0495-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="e0495-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e0495-105">Members</span></span>  
  
|<span data-ttu-id="e0495-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e0495-106">Member</span></span>|<span data-ttu-id="e0495-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e0495-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="e0495-108">Pokud je v této metodě vyvolán nějaký spravovaný kód, bude muset být umístěn pomocí explicitních událostí nebo zarážek později.</span><span class="sxs-lookup"><span data-stu-id="e0495-108">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="e0495-109">--nebo--</span><span class="sxs-lookup"><span data-stu-id="e0495-109">--or--</span></span><br /><br /> <span data-ttu-id="e0495-110">Omlouváme se, ale může se stát, že tato metoda volá jenom některé spravované kódy, protože neexistuje žádný snadný způsob, jak ji zastavit.</span><span class="sxs-lookup"><span data-stu-id="e0495-110">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="e0495-111">--nebo--</span><span class="sxs-lookup"><span data-stu-id="e0495-111">--or--</span></span><br /><br /> <span data-ttu-id="e0495-112">Metoda nikdy nemůže vyvolat spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="e0495-112">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="e0495-113">Tato metoda vyvolá spravovaný kód prostřednictvím návratové instrukce.</span><span class="sxs-lookup"><span data-stu-id="e0495-113">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="e0495-114">Krokování by mělo být doručeno do dalšího spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="e0495-114">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="e0495-115">Tato metoda vyvolá spravovaný kód prostřednictvím volání tail.</span><span class="sxs-lookup"><span data-stu-id="e0495-115">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="e0495-116">Do spravovaného kódu by měly být doručeny jednoduché krokování a krokování prostřednictvím jakýchkoli instrukcí volání.</span><span class="sxs-lookup"><span data-stu-id="e0495-116">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0495-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0495-117">Remarks</span></span>  
 <span data-ttu-id="e0495-118">Tento výčet používá metoda [ICorDebugProcess6:: GetExportStepInfo –](icordebugprocess6-getexportstepinfo-method.md) k poskytnutí informací o prokrokování prostřednictvím spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="e0495-118">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0495-119">Tento výčet je určený pro použití pouze v .NET Nativech scénářích ladění.</span><span class="sxs-lookup"><span data-stu-id="e0495-119">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0495-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0495-120">Requirements</span></span>  
 <span data-ttu-id="e0495-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0495-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0495-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e0495-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0495-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e0495-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0495-124">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0495-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0495-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0495-125">See also</span></span>

- [<span data-ttu-id="e0495-126">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="e0495-126">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="e0495-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="e0495-127">Debugging</span></span>](index.md)
