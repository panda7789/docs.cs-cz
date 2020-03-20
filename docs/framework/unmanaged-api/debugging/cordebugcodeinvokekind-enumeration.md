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
ms.openlocfilehash: 54332f5b3383f1c1513242a79cbd81eb8aa5c4f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179250"
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="9a635-102">Výčet CorDebugCodeInvokeKind</span><span class="sxs-lookup"><span data-stu-id="9a635-102">CorDebugCodeInvokeKind Enumeration</span></span>
<span data-ttu-id="9a635-103">Popisuje, jak exportovaná funkce vyvolá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="9a635-103">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a635-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a635-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,
    CODE_INVOKE_KIND_RETURN,
    CODE_INVOKE_KIND_TAILCALL,
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="9a635-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9a635-105">Members</span></span>  
  
|<span data-ttu-id="9a635-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9a635-106">Member</span></span>|<span data-ttu-id="9a635-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9a635-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="9a635-108">Pokud je touto metodou vyvolán jakýkoli spravovaný kód, bude muset být později umístěn explicitními událostmi nebo zarážkymi.</span><span class="sxs-lookup"><span data-stu-id="9a635-108">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="9a635-109">...nebo--</span><span class="sxs-lookup"><span data-stu-id="9a635-109">--or--</span></span><br /><br /> <span data-ttu-id="9a635-110">Můžeme jen chybět některé spravovaného kódu, který tato metoda volá, protože neexistuje žádný snadný způsob, jak na něm zastavit.</span><span class="sxs-lookup"><span data-stu-id="9a635-110">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="9a635-111">...nebo--</span><span class="sxs-lookup"><span data-stu-id="9a635-111">--or--</span></span><br /><br /> <span data-ttu-id="9a635-112">Metoda může nikdy vyvolat spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="9a635-112">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="9a635-113">Tato metoda vyvolá spravovaný kód prostřednictvím instrukce vrácení.</span><span class="sxs-lookup"><span data-stu-id="9a635-113">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="9a635-114">Krokování by mělo být doručeno k dalšímu spravovanému kódu.</span><span class="sxs-lookup"><span data-stu-id="9a635-114">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="9a635-115">Tato metoda vyvolá spravovaný kód prostřednictvím volání ocasu.</span><span class="sxs-lookup"><span data-stu-id="9a635-115">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="9a635-116">Jednokrokování a krokování přes všechny pokyny k volání by měly dorazit ke spravovanému kódu.</span><span class="sxs-lookup"><span data-stu-id="9a635-116">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a635-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9a635-117">Remarks</span></span>  
 <span data-ttu-id="9a635-118">Tento výčet používá metoda [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) k poskytnutí informací o krokování spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="9a635-118">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a635-119">Tento výčet je určen pouze pro použití v nativních scénářích ladění .NET.</span><span class="sxs-lookup"><span data-stu-id="9a635-119">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a635-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9a635-120">Requirements</span></span>  
 <span data-ttu-id="9a635-121">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a635-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a635-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a635-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a635-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a635-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a635-124">**Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a635-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a635-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a635-125">See also</span></span>

- [<span data-ttu-id="9a635-126">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="9a635-126">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="9a635-127">ladění</span><span class="sxs-lookup"><span data-stu-id="9a635-127">Debugging</span></span>](index.md)
