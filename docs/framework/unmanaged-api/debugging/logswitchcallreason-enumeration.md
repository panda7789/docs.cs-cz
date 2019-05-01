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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7eadb595eb62b4f1a9dcc888225cbb7454119c7c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986541"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="b0c1a-102">LogSwitchCallReason – výčet</span><span class="sxs-lookup"><span data-stu-id="b0c1a-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="b0c1a-103">Určuje operaci, která byla provedena na přepínači ladění a trasování.</span><span class="sxs-lookup"><span data-stu-id="b0c1a-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0c1a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0c1a-104">Syntax</span></span>  
  
```  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="b0c1a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b0c1a-105">Members</span></span>  
  
|<span data-ttu-id="b0c1a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b0c1a-106">Member</span></span>|<span data-ttu-id="b0c1a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b0c1a-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="b0c1a-108">Ladění a trasování přepínače byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="b0c1a-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="b0c1a-109">Ladění a trasování přepínače byla změněna.</span><span class="sxs-lookup"><span data-stu-id="b0c1a-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="b0c1a-110">Ladění a trasování přepínače byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="b0c1a-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b0c1a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0c1a-111">Requirements</span></span>  
 <span data-ttu-id="b0c1a-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0c1a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0c1a-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0c1a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0c1a-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0c1a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0c1a-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0c1a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0c1a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0c1a-116">See also</span></span>

- [<span data-ttu-id="b0c1a-117">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="b0c1a-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
