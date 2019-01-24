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
ms.openlocfilehash: d4eeecc3b1c248f4f0bf4372801f6bc71a22f260
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662228"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="cc083-102">Výčet CorDebugCodeInvokePurpose</span><span class="sxs-lookup"><span data-stu-id="cc083-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="cc083-103">Popisuje, proč exportované funkce volá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="cc083-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc083-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc083-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,    
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="cc083-105">Členové</span><span class="sxs-lookup"><span data-stu-id="cc083-105">Members</span></span>  
  
|<span data-ttu-id="cc083-106">Člen</span><span class="sxs-lookup"><span data-stu-id="cc083-106">Member</span></span>|<span data-ttu-id="cc083-107">Popis</span><span class="sxs-lookup"><span data-stu-id="cc083-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="cc083-108">Žádné nebo neznámý.</span><span class="sxs-lookup"><span data-stu-id="cc083-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="cc083-109">Spravovaný kód se spustí všechny spravovaný vstupní bod, jako je například reverzní p-invoke.</span><span class="sxs-lookup"><span data-stu-id="cc083-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="cc083-110">Jakýkoli účel podrobnější neznámý modul runtime.</span><span class="sxs-lookup"><span data-stu-id="cc083-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="cc083-111">Spravovaný kód se spustí statický konstruktor.</span><span class="sxs-lookup"><span data-stu-id="cc083-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="cc083-112">Spravovaný kód se spustí provádění pro některé metody rozhraní, která byla volána.</span><span class="sxs-lookup"><span data-stu-id="cc083-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc083-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc083-113">Remarks</span></span>  
 <span data-ttu-id="cc083-114">Tento výčet je používán [icordebugprocess6::getexportstepinfo –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) metodu k dispozici informace o procházení spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="cc083-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc083-115">Tento výčet je určena pro použití v .NET Native ladění pouze scénáře.</span><span class="sxs-lookup"><span data-stu-id="cc083-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc083-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc083-116">Requirements</span></span>  
 <span data-ttu-id="cc083-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc083-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc083-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc083-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc083-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc083-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc083-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc083-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc083-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc083-121">See also</span></span>
- [<span data-ttu-id="cc083-122">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="cc083-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="cc083-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="cc083-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
