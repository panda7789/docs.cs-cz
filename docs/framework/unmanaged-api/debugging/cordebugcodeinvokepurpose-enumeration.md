---
title: "Výčet CorDebugCodeInvokePurpose"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugInvokePurpose
api_location: mscordbi.dll
api_type: COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41938a11d7d92fd728772aa45bd8e97f137e5d69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="72573-102">Výčet CorDebugCodeInvokePurpose</span><span class="sxs-lookup"><span data-stu-id="72573-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="72573-103">Popisuje, proč exportované funkce volá spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="72573-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72573-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72573-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,    
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="72573-105">Členové</span><span class="sxs-lookup"><span data-stu-id="72573-105">Members</span></span>  
  
|<span data-ttu-id="72573-106">Člen</span><span class="sxs-lookup"><span data-stu-id="72573-106">Member</span></span>|<span data-ttu-id="72573-107">Popis</span><span class="sxs-lookup"><span data-stu-id="72573-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="72573-108">Žádná nebo je neznámý.</span><span class="sxs-lookup"><span data-stu-id="72573-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="72573-109">Spravovaný kód spustí všechny spravované vstupní bod, jako je například zpětné p-invoke.</span><span class="sxs-lookup"><span data-stu-id="72573-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="72573-110">Jakýkoli účel podrobnější Neznámý modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="72573-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="72573-111">Spravovaný kód spustí statického konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="72573-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="72573-112">Spravovaný kód spustí implementaci pro některé metody rozhraní, která byla volána.</span><span class="sxs-lookup"><span data-stu-id="72573-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72573-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72573-113">Remarks</span></span>  
 <span data-ttu-id="72573-114">Tento výčet je používán [icordebugprocess6::getexportstepinfo –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) metoda s informacemi o procházení spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="72573-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72573-115">Tento výčet je určena pro použití v rozhraní .NET nativní ladění pouze scénáře.</span><span class="sxs-lookup"><span data-stu-id="72573-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72573-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72573-116">Requirements</span></span>  
 <span data-ttu-id="72573-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72573-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72573-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72573-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72573-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72573-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72573-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72573-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72573-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="72573-121">See Also</span></span>  
 [<span data-ttu-id="72573-122">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="72573-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="72573-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="72573-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
