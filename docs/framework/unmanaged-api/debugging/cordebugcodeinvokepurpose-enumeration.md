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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b5de58caeeac5ae85402e91a1402958e68336bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967591"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="6da6f-102">Výčet CorDebugCodeInvokePurpose</span><span class="sxs-lookup"><span data-stu-id="6da6f-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="6da6f-103">Popisuje, proč exportovaná funkce volá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="6da6f-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6da6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6da6f-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,    
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="6da6f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="6da6f-105">Members</span></span>  
  
|<span data-ttu-id="6da6f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="6da6f-106">Member</span></span>|<span data-ttu-id="6da6f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6da6f-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="6da6f-108">Žádná nebo neznámá.</span><span class="sxs-lookup"><span data-stu-id="6da6f-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="6da6f-109">Spravovaný kód spustí všechny spravované vstupní body, jako je reverzní volání nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="6da6f-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="6da6f-110">Jakýkoli podrobnější účel není modulem runtime znám.</span><span class="sxs-lookup"><span data-stu-id="6da6f-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="6da6f-111">Spravovaný kód spustí statický konstruktor.</span><span class="sxs-lookup"><span data-stu-id="6da6f-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="6da6f-112">Spravovaný kód spustí implementaci pro některou metodu rozhraní, která byla volána.</span><span class="sxs-lookup"><span data-stu-id="6da6f-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6da6f-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6da6f-113">Remarks</span></span>  
 <span data-ttu-id="6da6f-114">Tento výčet používá metoda [ICorDebugProcess6:: GetExportStepInfo –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) k poskytnutí informací o prokrokování prostřednictvím spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="6da6f-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6da6f-115">Tento výčet je určený pro použití pouze v .NET Nativech scénářích ladění.</span><span class="sxs-lookup"><span data-stu-id="6da6f-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6da6f-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6da6f-116">Requirements</span></span>  
 <span data-ttu-id="6da6f-117">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6da6f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6da6f-118">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6da6f-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6da6f-119">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6da6f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6da6f-120">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6da6f-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6da6f-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6da6f-121">See also</span></span>

- [<span data-ttu-id="6da6f-122">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="6da6f-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="6da6f-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="6da6f-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
