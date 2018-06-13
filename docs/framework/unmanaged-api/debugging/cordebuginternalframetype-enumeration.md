---
title: CorDebugInternalFrameType – výčet
ms.date: 03/30/2017
api_name:
- CorDebugInternalFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInternalFrameType
helpviewer_keywords:
- CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b42a7fc54af56149b602b337e4a6c853c270cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406354"
---
# <a name="cordebuginternalframetype-enumeration"></a><span data-ttu-id="23c9e-102">CorDebugInternalFrameType – výčet</span><span class="sxs-lookup"><span data-stu-id="23c9e-102">CorDebugInternalFrameType Enumeration</span></span>
<span data-ttu-id="23c9e-103">Určuje typ rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="23c9e-103">Identifies the type of stack frame.</span></span> <span data-ttu-id="23c9e-104">Tento výčet je používán [icordebuginternalframe::getframetype –](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="23c9e-104">This enumeration is used by the [ICorDebugInternalFrame::GetFrameType](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23c9e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23c9e-105">Syntax</span></span>  
  
```  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a><span data-ttu-id="23c9e-106">Členové</span><span class="sxs-lookup"><span data-stu-id="23c9e-106">Members</span></span>  
  
|<span data-ttu-id="23c9e-107">Člen</span><span class="sxs-lookup"><span data-stu-id="23c9e-107">Member</span></span>|<span data-ttu-id="23c9e-108">Popis</span><span class="sxs-lookup"><span data-stu-id="23c9e-108">Description</span></span>|  
|------------|-----------------|  
|`STUBFRAME_NONE`|<span data-ttu-id="23c9e-109">Hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="23c9e-109">A null value.</span></span> <span data-ttu-id="23c9e-110">`ICorDebugInternalFrame::GetFrameType` Metoda nikdy vrátí tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="23c9e-110">The `ICorDebugInternalFrame::GetFrameType` method never returns this value.</span></span>|  
|`STUBFRAME_M2U`|<span data-ttu-id="23c9e-111">Spravované na nespravované se zakázaným inzerováním rámce.</span><span class="sxs-lookup"><span data-stu-id="23c9e-111">A managed-to-unmanaged stub frame.</span></span>|  
|`STUBFRAME_U2M`|<span data-ttu-id="23c9e-112">Rámce nespravovaného do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="23c9e-112">An unmanaged-to-managed stub frame.</span></span>|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|<span data-ttu-id="23c9e-113">Přechod mezi doménami aplikací.</span><span class="sxs-lookup"><span data-stu-id="23c9e-113">A transition between application domains.</span></span>|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|<span data-ttu-id="23c9e-114">Volání metody lightweight.</span><span class="sxs-lookup"><span data-stu-id="23c9e-114">A lightweight method call.</span></span>|  
|`STUBFRAME_FUNC_EVAL`|<span data-ttu-id="23c9e-115">Spuštění funkce vyhodnocování.</span><span class="sxs-lookup"><span data-stu-id="23c9e-115">The start of function evaluation.</span></span>|  
|`STUBFRAME_INTERNALCALL`|<span data-ttu-id="23c9e-116">Interní volání do modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="23c9e-116">An internal call into the common language runtime.</span></span>|  
|`STUBFRAME_CLASS_INIT`|<span data-ttu-id="23c9e-117">Spuštění inicializaci třídy.</span><span class="sxs-lookup"><span data-stu-id="23c9e-117">The start of a class initialization.</span></span>|  
|`STUBFRAME_EXCEPTION`|<span data-ttu-id="23c9e-118">Výjimka, která je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="23c9e-118">An exception that is thrown.</span></span>|  
|`STUBFRAME_SECURITY`|<span data-ttu-id="23c9e-119">Rámce, který se používá pro zabezpečení přístupu kódu.</span><span class="sxs-lookup"><span data-stu-id="23c9e-119">A frame used for code access security.</span></span>|  
|`STUBFRAME_JIT_COMPILATION`|<span data-ttu-id="23c9e-120">Modul runtime je JIT – kompilace metodu.</span><span class="sxs-lookup"><span data-stu-id="23c9e-120">The runtime is JIT-compiling a method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="23c9e-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="23c9e-121">Requirements</span></span>  
 <span data-ttu-id="23c9e-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23c9e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23c9e-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23c9e-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23c9e-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23c9e-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23c9e-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23c9e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23c9e-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="23c9e-126">See Also</span></span>  
 [<span data-ttu-id="23c9e-127">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="23c9e-127">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
