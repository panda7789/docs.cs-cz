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
ms.openlocfilehash: f037a28f0417f5607cd5b5637da4ca62e34e0edb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132268"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="5b1e9-102">Výčet CorDebugCodeInvokePurpose</span><span class="sxs-lookup"><span data-stu-id="5b1e9-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="5b1e9-103">Popisuje, proč exportovaná funkce volá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="5b1e9-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b1e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b1e9-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,    
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="5b1e9-105">Členové</span><span class="sxs-lookup"><span data-stu-id="5b1e9-105">Members</span></span>  
  
|<span data-ttu-id="5b1e9-106">Člen</span><span class="sxs-lookup"><span data-stu-id="5b1e9-106">Member</span></span>|<span data-ttu-id="5b1e9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5b1e9-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="5b1e9-108">Žádná nebo neznámá.</span><span class="sxs-lookup"><span data-stu-id="5b1e9-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="5b1e9-109">Spravovaný kód spustí všechny spravované vstupní body, jako je reverzní volání nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="5b1e9-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="5b1e9-110">Jakýkoli podrobnější účel není modulem runtime znám.</span><span class="sxs-lookup"><span data-stu-id="5b1e9-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="5b1e9-111">Spravovaný kód spustí statický konstruktor.</span><span class="sxs-lookup"><span data-stu-id="5b1e9-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="5b1e9-112">Spravovaný kód spustí implementaci pro některou metodu rozhraní, která byla volána.</span><span class="sxs-lookup"><span data-stu-id="5b1e9-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b1e9-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b1e9-113">Remarks</span></span>  
 <span data-ttu-id="5b1e9-114">Tento výčet používá metoda [ICorDebugProcess6:: GetExportStepInfo –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) k poskytnutí informací o prokrokování prostřednictvím spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="5b1e9-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b1e9-115">Tento výčet je určený pro použití pouze v .NET Nativech scénářích ladění.</span><span class="sxs-lookup"><span data-stu-id="5b1e9-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b1e9-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b1e9-116">Requirements</span></span>  
 <span data-ttu-id="5b1e9-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b1e9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b1e9-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5b1e9-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b1e9-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5b1e9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b1e9-120">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b1e9-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b1e9-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b1e9-121">See also</span></span>

- [<span data-ttu-id="5b1e9-122">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="5b1e9-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="5b1e9-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="5b1e9-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
