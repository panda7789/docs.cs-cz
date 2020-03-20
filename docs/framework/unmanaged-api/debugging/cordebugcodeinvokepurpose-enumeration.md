---
title: Výčet CorDebugCodeInvokePurpose
ms.date: 03/30/2017
api_name:
- CorDebugInvokePurpose
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type:
- apiref
ms.openlocfilehash: f1d4a1e08a63665a532c7aa3572f1e3f9c106ba6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179246"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="984a2-102">Výčet CorDebugCodeInvokePurpose</span><span class="sxs-lookup"><span data-stu-id="984a2-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="984a2-103">Popisuje, proč exportovaná funkce volá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="984a2-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="984a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="984a2-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="984a2-105">Členové</span><span class="sxs-lookup"><span data-stu-id="984a2-105">Members</span></span>  
  
|<span data-ttu-id="984a2-106">Člen</span><span class="sxs-lookup"><span data-stu-id="984a2-106">Member</span></span>|<span data-ttu-id="984a2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="984a2-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="984a2-108">Žádné nebo neznámé.</span><span class="sxs-lookup"><span data-stu-id="984a2-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="984a2-109">Spravovaný kód spustí libovolný spravovaný vstupní bod, například reverzní p-invoke.</span><span class="sxs-lookup"><span data-stu-id="984a2-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="984a2-110">Jakýkoli podrobnější účel není za běhu znám.</span><span class="sxs-lookup"><span data-stu-id="984a2-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="984a2-111">Spravovaný kód spustí statický konstruktor.</span><span class="sxs-lookup"><span data-stu-id="984a2-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="984a2-112">Spravovaný kód spustí implementaci pro některé metody rozhraní, která byla volána.</span><span class="sxs-lookup"><span data-stu-id="984a2-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="984a2-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="984a2-113">Remarks</span></span>  
 <span data-ttu-id="984a2-114">Tento výčet používá metoda [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) k poskytnutí informací o krokování spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="984a2-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="984a2-115">Tento výčet je určen pouze pro použití v nativních scénářích ladění .NET.</span><span class="sxs-lookup"><span data-stu-id="984a2-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="984a2-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="984a2-116">Requirements</span></span>  
 <span data-ttu-id="984a2-117">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="984a2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="984a2-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="984a2-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="984a2-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="984a2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="984a2-120">**Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="984a2-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="984a2-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="984a2-121">See also</span></span>

- [<span data-ttu-id="984a2-122">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="984a2-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="984a2-123">ladění</span><span class="sxs-lookup"><span data-stu-id="984a2-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
