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
ms.openlocfilehash: 2be827e12db765485ee889d6a4a19a982dad5d54
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778372"
---
# <a name="cordebuginternalframetype-enumeration"></a><span data-ttu-id="6a786-102">CorDebugInternalFrameType – výčet</span><span class="sxs-lookup"><span data-stu-id="6a786-102">CorDebugInternalFrameType Enumeration</span></span>
<span data-ttu-id="6a786-103">Určuje typ rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="6a786-103">Identifies the type of stack frame.</span></span> <span data-ttu-id="6a786-104">Tento výčet používá metoda [ICorDebugInternalFrame:: getframetype –](icordebuginternalframe-getframetype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6a786-104">This enumeration is used by the [ICorDebugInternalFrame::GetFrameType](icordebuginternalframe-getframetype-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a786-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a786-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="6a786-106">Členové</span><span class="sxs-lookup"><span data-stu-id="6a786-106">Members</span></span>  
  
|<span data-ttu-id="6a786-107">Člen</span><span class="sxs-lookup"><span data-stu-id="6a786-107">Member</span></span>|<span data-ttu-id="6a786-108">Popis</span><span class="sxs-lookup"><span data-stu-id="6a786-108">Description</span></span>|  
|------------|-----------------|  
|`STUBFRAME_NONE`|<span data-ttu-id="6a786-109">Hodnota null.</span><span class="sxs-lookup"><span data-stu-id="6a786-109">A null value.</span></span> <span data-ttu-id="6a786-110">Metoda `ICorDebugInternalFrame::GetFrameType` nikdy tuto hodnotu nevrací.</span><span class="sxs-lookup"><span data-stu-id="6a786-110">The `ICorDebugInternalFrame::GetFrameType` method never returns this value.</span></span>|  
|`STUBFRAME_M2U`|<span data-ttu-id="6a786-111">Nespravovaný rámeček se zástupnými procedurami spravovaného do nespravovaného kódu</span><span class="sxs-lookup"><span data-stu-id="6a786-111">A managed-to-unmanaged stub frame.</span></span>|  
|`STUBFRAME_U2M`|<span data-ttu-id="6a786-112">Nespravovaný rámec nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="6a786-112">An unmanaged-to-managed stub frame.</span></span>|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|<span data-ttu-id="6a786-113">Přechod mezi doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="6a786-113">A transition between application domains.</span></span>|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|<span data-ttu-id="6a786-114">Zjednodušené volání metody.</span><span class="sxs-lookup"><span data-stu-id="6a786-114">A lightweight method call.</span></span>|  
|`STUBFRAME_FUNC_EVAL`|<span data-ttu-id="6a786-115">Začátek vyhodnocení funkce.</span><span class="sxs-lookup"><span data-stu-id="6a786-115">The start of function evaluation.</span></span>|  
|`STUBFRAME_INTERNALCALL`|<span data-ttu-id="6a786-116">Interní volání modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="6a786-116">An internal call into the common language runtime.</span></span>|  
|`STUBFRAME_CLASS_INIT`|<span data-ttu-id="6a786-117">Začátek inicializace třídy.</span><span class="sxs-lookup"><span data-stu-id="6a786-117">The start of a class initialization.</span></span>|  
|`STUBFRAME_EXCEPTION`|<span data-ttu-id="6a786-118">Výjimka, která je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="6a786-118">An exception that is thrown.</span></span>|  
|`STUBFRAME_SECURITY`|<span data-ttu-id="6a786-119">Rámec používaný pro zabezpečení přístupu kódu.</span><span class="sxs-lookup"><span data-stu-id="6a786-119">A frame used for code access security.</span></span>|  
|`STUBFRAME_JIT_COMPILATION`|<span data-ttu-id="6a786-120">Modul runtime je kompilace metody JIT.</span><span class="sxs-lookup"><span data-stu-id="6a786-120">The runtime is JIT-compiling a method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6a786-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a786-121">Requirements</span></span>  
 <span data-ttu-id="6a786-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a786-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a786-123">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6a786-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a786-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6a786-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a786-125">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a786-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a786-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a786-126">See also</span></span>

- [<span data-ttu-id="6a786-127">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="6a786-127">Debugging Enumerations</span></span>](debugging-enumerations.md)
