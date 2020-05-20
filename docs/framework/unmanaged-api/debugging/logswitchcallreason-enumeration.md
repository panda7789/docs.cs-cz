---
title: LogSwitchCallReason – výčet
ms.date: 03/30/2017
api_name:
- LogSwitchCallReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LogSwitchCallReason
helpviewer_keywords:
- LogSwitchCallReason enumeration [.NET Framework debugging]
ms.assetid: 5bbb8d1b-bbc4-47b0-b1b1-2d54cc0be291
topic_type:
- apiref
ms.openlocfilehash: 4d29bb3886ffb51e1dfb9654f4d70ef7c568fd43
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420705"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="7cfc1-102">LogSwitchCallReason – výčet</span><span class="sxs-lookup"><span data-stu-id="7cfc1-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="7cfc1-103">Určuje operaci, která byla provedena na přepínači ladění/trasování.</span><span class="sxs-lookup"><span data-stu-id="7cfc1-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cfc1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cfc1-104">Syntax</span></span>  
  
```cpp  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="7cfc1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7cfc1-105">Members</span></span>  
  
|<span data-ttu-id="7cfc1-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7cfc1-106">Member</span></span>|<span data-ttu-id="7cfc1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7cfc1-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="7cfc1-108">Byl vytvořen přepínač ladění/trasování.</span><span class="sxs-lookup"><span data-stu-id="7cfc1-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="7cfc1-109">Přepínač ladění/trasování byl změněn.</span><span class="sxs-lookup"><span data-stu-id="7cfc1-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="7cfc1-110">Přepínač ladění/trasování byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="7cfc1-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7cfc1-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7cfc1-111">Requirements</span></span>  
 <span data-ttu-id="7cfc1-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cfc1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cfc1-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7cfc1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7cfc1-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7cfc1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cfc1-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cfc1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cfc1-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7cfc1-116">See also</span></span>

- [<span data-ttu-id="7cfc1-117">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="7cfc1-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
